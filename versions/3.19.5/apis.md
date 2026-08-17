# 3.19.5 接口

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`

## 新路径（相对 3.18.4 字符串差集）

| 方法 | 路径 | 鉴权 | 含义 | 实打 |
|---|---|---|---|---|
| GET | `/bapi/equity/v1/public/equity/corporate-actions?symbol=AAPL` | public | 公司行动（分红/拆股） | 200 |
| GET | `/bapi/equity/v1/public/equity/market/get-info?symbol=AAPL` | public | 个股价、量、估值、公司简介 | 200 |
| GET | `/bapi/equity/v1/public/equity/news/get-news?symbol=AAPL&limit=5` | public | Alpaca 新闻，可用 `lastAlpacaNewsId` 翻页 | 200 |
| GET | `/bapi/composite/v1/private/bigdata/finance/stock-statistics` | 要登录 | 钱包美股盈亏统计 | 401 |
| GET | `/bapi/margin/v1/private/margin/stock-dividend-history` | 要登录 | 杠杆侧股票股息流水 | 401 |
| GET | `/bapi/margin/v1/private/margin/quiz/status?quizType=BSTOCK_COLLATERAL` | 要登录 | bStocks 抵押适当性测验 | 未打通体 |
| GET | `/bapi/futures/v1/private/future/copy-trade/copy-portfolio/enter-self-managing` | 要登录 | 跟单转自管 | 未打 |
| GET | `/bapi/margin/v1/private/isolated-margin/conditional-close` | 要登录 | 逐仓条件平仓 | 未打 |
| GET | `/bapi/apex/v3/public/apex/marketing/getUserAppFeatures` | public | 功能开关 v3（替换 v2） | 400 缺参 |
| GET | `/bapi/defi/v1/public/wallet-direct/prediction/market/list/crypto/up-down/settled` | public | 预测盘涨跌结算列表 | 未打 |

同族已通、不一定是「路径字符串首次出现」：

- `/bapi/equity/v1/public/equity/financials/overview?symbol=AAPL` → 利润表/资产负债表/现金流

删除侧（字符串不再唯一出现，不代表服务端下线）：

- `/bapi/apex/v2/friendly/apex/marketing/getUserAppFeatures`
- `/bapi/apex/v2/friendly/apex/marketing/banners`
- Earn 首页 search
- `alpha-trade/order/get-order-history`（可能只是换路径）

## 实打摘要

### corporate-actions

不带 `symbol` 会 200 但 `actions: []`。AAPL 两条 `cash_dividend`，`rate=0.27`，`assetCode=EQ_AAPL`，有 `exDate` / `payableDate` / `processDate`。TSLA 当时 `actions: []`。

### market/get-info

必须 `symbol`。AAPL：`currentPrice`、`high52Week`、`marketCap`、`peRatio`、`dividendYield`、`eps`、`companyName`、长 `description`。TSLA：`EQ_TSLA`，`dividendYield=0`。

### news/get-news

关键参数是 **`symbol` + `limit`**，`page`/`rows` 会 `000002`。字段：`alpacaNewsId`、`headline`、`summary`、`author`、`source`（样例 The Motley Fool）、`url`、`createdAt`、`hasMore`。`lastAlpacaNewsId` 是游标。
