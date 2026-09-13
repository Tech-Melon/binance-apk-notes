# 3.20.3 接口

本轮只有 Play base。下面实打用 `www.binance.com`。

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`，`User-Agent: Binance/3.20.3 (Android)`

## 新路径（相对 3.20.1 字符串差集，且 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 没有）

| 方法 | 路径 | 鉴权 | 含义 | 实打 |
|---|---|---|---|---|
| GET | `/bapi/apex/v1/friendly/apex/app/markets/tabs` | public | 行情 Tab。默认 `fav`；还有 market / tradfi / alpha / content / data | 200 |
| GET | `/bapi/apex/v1/public/apex/b9/market/categories` | public | B9 分类：All / Holdings / Spot / Futures，含 Today's Flow、Net Inflow、Top Trader LS | 200 |
| GET | `/bapi/apex/v1/public/apex/b9/widget/favouritemore/one` | public | 单条自选卡片 schema；空参字段全 null | 200 |
| GET | `/bapi/apex/v1/public/apex/marketing/allSymbolTotalInfoSorted` | public | 行情分区（Fan Token / Monitoring / New Listing 等） | 200 |
| GET | `/bapi/apex/v3/friendly/apex/b9/screener/widget-middle` | public | Screener 中卡。远程 MP `kg39guhd4MzvBvsgyEcmjU`，样例 John Paulson Holdings | 200 |
| GET | `/bapi/apex/v3/friendly/apex/b9/screener/widget-small` | public | Easy Screener / Quant Strategies / Customize / My Favorites | 200 |
| GET | `/bapi/equity/v1/public/equity/recurring-buy/symbol/get-symbols-index` | public | 定投标的索引，100 条 `{ac,s}` | 200 |
| GET | `/bapi/fe/mimir/v2/public/get-ai-landing-page?source=market_crypto_tracker` | public | AI / For You 落地页。空 `source` → `300000 unknown source` | 200 |
| GET | `/bapi/apex/v1/public/apex/b9/market/klines` | public | K 线。空参和 `symbol=BTCUSDT&interval=1h` 都 `000002` | 400 |
| GET | `/bapi/apex/v1/private/apex/app/markets/tabs` | 要登录 | 登录态 Tab（For You 可能在这） | 401 |
| GET | `/bapi/apex/v1/private/apex/b9/apex/homepage/crypto/widget` | 要登录 | B9 加密 widget | 401 |
| GET | `/bapi/apex/v1/private/apex/b9/apex/homepage/etf/widget` | 要登录 | B9 ETF widget | 401 |
| GET | `/bapi/apex/v1/private/apex/b9/apex/homepage/stock/widget` | 要登录 | B9 美股 widget | 401 |
| GET | `/bapi/apex/v1/private/apex/b9/daily-report/display` | 要登录 | 每日复盘 | 401 |
| GET | `/bapi/apex/v1/private/apex/b9/today-hotspot/widget` | 要登录 | 今日热点 | 401 |
| GET | `/bapi/apex/v1/private/apex/b9/top-trader/widget` | 要登录 | 顶级交易员 | 401 |
| GET | `/bapi/apex/v1/private/apex/b9/voice/placeholder-topics` | 要登录 | 语音占位主题 | 401 |
| GET | `/bapi/apex/v1/private/apex/b9/asset-analysis/movers-list` | 要登录 | 异动列表 | 401 |
| GET | `/bapi/apex/v2/private/apex/b9/deep-analysis/widget` | 要登录 | 深度分析 | 401 |
| GET | `/bapi/apex/v2/private/apex/b9/today-trend/widget` | 要登录 | 今日趋势 | 401 |
| GET | `/bapi/equity/v1/private/equity/recurring/plan-list` | 要登录 | 定投计划列表 | 401 |
| GET | `/bapi/equity/v1/private/equity/fee/estimate` | 要登录 | 美股费用估算 | 401 |
| GET | `/bapi/fe/jarvis/v2/user/voice-names` | 要登录 | Jarvis 音色列表 | 401 |
| GET | `/bapi/fe/mimir/v1/private/list-home-6in1-smart-banner` | 要登录 | 首页 6 合 1 banner | 401 |
| GET | `/bapi/fe/mimir/v1/private/tooltip-config` | 要登录 | tooltip 配置 | 401 |
| GET | `/bapi/fe/mimir/v2/private/get-ai-landing-page` | 要登录 | 登录态 AI 落地页 | 401 |
| GET | `/bapi/fe/mimir/v2/private/get-b9-asset-report` | 要登录 | B9 资产报告 | 401 |
| GET | `/bapi/fe/mimir/v1/private/get-b9-report` | 要登录 | B9 报告（包内注释是 POST） | 401 |
| GET | `/bapi/fe/chimera/report/get` | 要登录 | chimera 报告 | 401 |
| GET | `/bapi/fe/chimera/report/find` | 要登录 | chimera 查找 | 401 |

未登录私有接口一律 `100001005`（apex/equity 文案 `Please log in first.`，mimir/jarvis/chimera 文案 `Please check if you are logged in.`），不编返回体。

**不当新路径：** `/bapi/composite/v4/friendly/pgc/feed/news/list` — 3.20.1 字节里已有，公开也通，但这轮不记新增。

**这版从字符串里消失（Play base）：** `/bapi/fe/jarvis/v2/tts/demovoice`、`/bapi/fe/jarvis/v2/tts/list_voice`，换成 `voice-names`。

## 实打摘要

### markets/tabs

`defaultTab=fav`。六个 key：`fav` / `market` / `tradfi` / `alpha` / `content` / `data`。公开包没有 `forYou`。

### recurring-buy symbols

无参即全表，**100** 条。头五：`EQ_MU/MU`、`EQ_NVDA/NVDA`、`EQ_AAPL/AAPL`、`EQ_META/META`、`EQ_TSLA/TSLA`。字段只有 `ac` + `s`。

### get-ai-landing-page

必须带 `source`。`market_crypto_tracker` 样例字段：`widgets`、`protocolVersion=1.0.0`、`scenarioId`、`mpDetails`、`pageConfig`、`layout`。

### screener widgets

中卡 `mppLink` 解出：

- appId `kg39guhd4MzvBvsgyEcmjU`
- path `/pages/screener/master/index`
- query `realMasterTab=true`

小卡按钮：Easy Screener → `/pages/screener/conditions/index`；Quant Strategies → `/pages/screener/quant/index`。

### b9/market/klines

缺参。未继续猜字段。

### 私有

`100001005`。不编体。

## 深链（包内硬编码）

| 原文 | 解码 / 说明 | 相对 3.20.1 |
|---|---|---|
| `bnc://app.binance.com/ai/landing?source=market_crypto_tracker` 等 | For You / AI 落地，source 区分加密、ETF、美股、pulse、top trader | **新** |
| `bnc://app.binance.com/music/landingPage` | 简报/播放落地 | **新** |
| `bnc://app.binance.com/mp/app?appId=znf9fpiMh6ufdU3vDtAvi4&startPagePath=…buzz-appeal-quiz…&startPageQuery=` | 旧 quiz，多了空 query | 路径旧 |
| `bnc://app.binance.com/mp/web?appId=q7xVG7ra5ocEDmTGEQo9uX&startPagePath=cGFnZXMvaW5kZXgvaW5kZXg` | `pages/index/index` | 旧 |
| `bnc://app.binance.com/markets/marketsDetail` | 行情详情 | 旧 |
| `bnc://x` | 短串，**不是** `Continue to X` | 忽略 |

FAQ 硬编码 `https://www.binance.com/support/faq/detail/ecb50ef2012f40b2a2c4f72eaa5b569f`。直拉被 AWS WAF 202，没拿到标题。
