# 3.20.1 接口

本轮只有 Play base。下面实打用 `www.binance.com`。

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`，`User-Agent: Binance/3.20.1 (Android)`

## 新路径（相对 3.19.8 字符串差集，且完整 3.19.8 没有）

| 方法 | 路径 | 鉴权 | 含义 | 实打 |
|---|---|---|---|---|
| GET | `/bapi/equity/v1/friendly/equity/symbol/get-quote-v2?symbol=AAPL` | public | 美股买卖报价资产 + 可闪兑资产。`assetCode=EQ_AAPL` 同样通 | 200 |
| GET | `/bapi/equity/v2/public/equity/commission/get?assetCode=EQ_AAPL` | public | 美股佣金/点差。有效参数是 **`assetCode`**；`symbol` 或不传会落到全局表 | 200 |
| GET | `/bapi/futures/v1/public/future/spot-copy-trade/common/support-symbol-details` | public | 现货跟单可跟标的，约 374 条，带 `bstock` | 200 |
| GET | `/bapi/futures/v1/friendly/future/copy-trade/home-page/recommend-lead-item` | public | 推荐带单员。空参 / `page=1` 都 `000002` | 400 |
| GET | `/bapi/apex/v2/private/apex/homepage/onboarding/detail` | 要登录 | 首页 onboarding 详情 | 401 |
| GET | `/bapi/apex/v2/private/apex/homepage/onboarding/display` | 要登录 | 首页 onboarding 展示 | 401 |
| GET | `/bapi/apex/v4/private/apex/pnl/overview/avgCost` | 要登录 | 总览均价/成本价 | 401 |
| GET | `/bapi/composite/v1/private/bigdata/total-cost-price/update` | 要登录 | 改成本价 | 401 |
| GET | `/bapi/defi/v1/private/wallet-direct/buw/wallet/home_page/token/list` | 要登录 | 直连钱包首页 token | 401 |
| GET | `/bapi/defi/v1/private/wallet-direct/event/async/query` | 要登录 | 直连钱包异步事件 | 401 |
| GET | `/bapi/earn/v1/private/finance-earn/snapshot/profit/list-with-period-amount` | 要登录 | Earn 周期收益快照 | 401 |
| GET | `/bapi/futures/v1/private/future/smart-money/subscribe` | 要登录 | Smart Money 订阅 | 401 |
| GET | `/bapi/futures/v1/private/future/strategy/arbitrage/query-max-withdraw-amount` | 要登录 | 套利利润可提上限 | 401 |
| GET | `/bapi/futures/v1/private/future/strategy/arbitrage/withdraw` | 要登录 | 提取套利利润 | 401 |
| GET | `/bapi/margin/v1/private/margin/compliance-check` | 要登录 | 杠杆合规检查 | 401 |

未登录私有接口一律 `100001005 Please log in first.`，不编返回体。  
包内还有截断串 `/bapi/risk`，不当完整路径。

## 实打摘要

### get-quote-v2

`symbol=AAPL` 或 `assetCode=EQ_AAPL`。样例：

- `buyQuoteAssets: ["USDC"]`
- `sellQuoteAssets: ["USDC"]`
- `convertAssets: ["USDT", "USDC", "USD1", ...]`

这是报价资产白名单，**不是** last price。和 AOR / 闪兑再下单对得上。

### commission/get（v2）

`assetCode=EQ_AAPL` 样例：

- `quoteAsset=USDC`
- `equitySpread=0.0005`
- `minOrderFee=0.17`
- `commission=0`
- `feeThreshold=340`
- `limitDiscountRate` / `marketDiscountRate` = `0`

不传或传 `symbol=AAPL`：返回 `GLOBAL_CONFIG` + 一条 `EQ_NKE`（服务端默认表，**不是**按 AAPL 过滤）。要用 `assetCode`。

### support-symbol-details

无参即全表。样例头三：`BTCUSDT` / `ETHUSDT` / `SOLUSDT`，`bstock=false`，后面大约还有 371 条。`symbol=BTCUSDT` **不裁表**。

### recommend-lead-item

空参和 `page=1` 都 `000002 illegal parameter`。缺必填字段，未继续猜。

### 私有

`100001005`。不编体。

## 深链（包内硬编码）

| 原文 | 解码 / 说明 | 相对 3.19.8 |
|---|---|---|
| `bnc://app.binance.com/mp/app?appId=VEjMk4pBxLYdtkWUWGghxD` | 新 appId，无 path | **新** |
| `...appId=znf9fpiMh6ufdU3vDtAvi4&startPagePath=cGFnZXMvYnV6ei1hcHBlYWwtcXVpei9pbmRleA` | `pages/buzz-appeal-quiz/index` | appId 旧，这组 query **新** |
| `...appId=daRdj4PkKgdy6HNB2dgwDC&sourceEntry=1` | 旧 appId | 旧 |
| `bnc://app.binance.com/mp/web?appId=gE3L87HgrhVrM5YAeaseWc&startPagePath=` | 旧 appId | 旧 |
| `bnc://app.binance.com/stock/stockTransfer?direction=IN` | 美股转入 | 这串 **新** |

FAQ 硬编码 `https://www.binance.com/zh-CN/support/faq/detail/80b0b59efdc249519c92cd62ae88d669`（文案里 AOR Learn More 指向 FAQ）。直拉被 AWS WAF 202，没拿到标题。
