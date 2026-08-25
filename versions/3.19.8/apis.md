# 3.19.8 接口

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`

## 新路径（相对 3.19.5 字符串差集）

| 方法 | 路径 | 鉴权 | 含义 | 实打 |
|---|---|---|---|---|
| GET | `/bapi/equity/v1/friendly/equity/option/get?symbol=AAPL` | public | 标的价 + 到期日列表 | 200 |
| GET | `/bapi/equity/v1/friendly/equity/option/chain?symbol=AAPL&expirationDate=YYYY-MM-DD` | public | 一张到期日的期权链 | 200 |
| GET | `/bapi/equity/v1/public/equity/option/get-exchange-info?symbol=AAPL` | public | 交易所信息；AAPL 返回 `data: null` | 200 空体 |
| GET | `/bapi/equity/v1/public/equity/symbol/get-symbols-index` | public | 全市场 `{ac,s}` 索引，约 7900 条 | 200 |
| GET | `/bapi/equity/v1/public/equity/symbol/search?q=AAPL` | public | 股票搜索。参数是 **`q`**，`keyword`/`symbol` 会 `000002` | 200 |
| GET | `/bapi/equity/v1/private/equity/option/order/place` | 要登录 | 下单 | 401 |
| GET | `/bapi/equity/v1/private/equity/option/position/get` | 要登录 | 持仓 | 401 |
| GET | `/bapi/equity/v1/private/equity/option/exercise/submit` 等同族 | 要登录 | 行权提交/历史/详情 | 未打体，路径在包内 |
| GET | `/bapi/equity/v1/private/equity/option/quote` + `quote/heartbeat` + `rt/enable` | 要登录 | 报价 / 心跳 / 开实时 | 未打体 |
| GET | `/bapi/equity/v1/private/equity/option/wss/token` | 要登录 | 期权行情 WS token | 未打 |
| GET | `/bapi/equity/v2/private/equity/order/history` | 要登录 | 订单历史 v2 | 401 |
| GET | `/bapi/equity/v2/private/equity/order/open-orders` | 要登录 | 当前委托 v2 | 401 |
| GET | `/bapi/equity/v2/private/equity/trade/history` | 要登录 | 成交历史 v2 | 401 |
| GET | `/bapi/apex/v1/private/apex/asset/stock-option/subtypes` | 要登录 | 钱包股票期权子类型 | 401 |
| GET | `/bapi/apex/v1/private/apex/asset/stock-option/history` | 要登录 | 钱包股票期权流水 | 401 |
| GET | `/bapi/apex/v1/friendly/apex/discover/trading/recommend-list` | public | Discover 交易推荐布局 | 200 |
| GET | `/bapi/futures/v1/public/strategy/common/grid/coef` | public | 网格数量/系数 | 200 |
| GET | `/bapi/fe/mimir/v1/private/get-b9-page-whitelist` | 要登录 | 未知 B9 页面白名单 | 401 |
| GET | `/bapi/fe/mimir/v1/private/get-b9-tips` | 要登录 | 未知 B9 提示 | 401 |

`option/chain` 只传 `symbol` 会 `000002`，必须带 `expirationDate`。`assetCode=EQ_AAPL` 也能打通。

## 实打摘要

### option/get

`symbol=AAPL` 或 `assetCode=EQ_AAPL`。样例：`price=309.54`，`cv=342814`，`pv=133316`，`expirations[]` 每项 `expirationDate` + `rootSymbol`（当日 22 个到期日，近的是 2026-08-26）。

### option/chain

关键参数 **`symbol` + `expirationDate`**。样例合约：

- `os=AAPL260826C00205000`
- `n=AAPL Aug 26 2026 205 Call`
- `t=call`，`sp=205`，`m=100`，`sz=100`
- `bp`/`ap`/`bs`/`as` 买卖价量，`mp` 中间价，`iv` 隐含波动率
- `de`/`ga`/`th`/`ve` = delta / gamma / theta / vega
- `oi` 未平仓（样例为 null），`be` 盈亏平衡

### symbol/search

`q=AAPL` → `type=ALL`，`items: [{ac: EQ_AAPL, s: AAPL}, EQ_AAPB / AAPD / AAPU / AAPW, ...]`。

### get-symbols-index

`data` 是短字段列表，样例头三：`EQ_NVDA/NVDA`、`EQ_MU/MU`、`EQ_SNDK/SNDK`，后面大约还有 7920 条。`limit` 不裁。

### grid/coef

`windowCount=170`，`orderBufferCount=20`，`maxGridCount=500`，`minGridCount=2`，`trailingCoef=2.0`，`alphaScale=0.35`，`coefBase=1.05`，`maxTrailingGridCount=170`。

### trading/recommend-list

`layout: [smartMoneySignal, topTraders, tradingBot]`。smart money 深链 appId `ePnX8nC4YXdmFkGBpmNxCi`，解码 `pages/home/index?queryTab=smart-signal`。

### B9 / 私有期权

未登录：`100001005`。B9 两条文案是 `Please check if you are logged in.`（mimir 风格）；期权私有是 `Please log in first.`。不编返回体。B9 是什么产品，包内没有用户可读名。
