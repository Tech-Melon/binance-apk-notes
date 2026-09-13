# 3.20.3 文案

判定「新」：3.18.4 + 3.19.5 + 完整 3.19.8 + **3.20.1 Play base** 整包（dex + 完整 arsc + assets）UTF-8 / UTF-16LE 都没有。  
本轮扫描包是 Play base `币安 3.20.3.apk`（默认英文瘦 arsc）。**不能用来判中文下线。**

## 确认新增（四旧包整包没有）

### 美股定投

| 原文 | 用途 |
|---|---|
| `Stock recurring buy is now available. Tap to set one up.` | 定投上线提示 |
| `Automate your investments with scheduled recurring buys.` | 说明 |
| `No Recurring Plan` / `Recurring Plan Set Successfully` / `Recurring History` | 空态 / 成功 / 历史 |
| `Daily Buy` / `Weekly Buy` / `Biweekly Buy` / `Monthly Buy` / `One-Time Buy` | 周期 |
| `One-time buy is available only during US Market open hours.` | 一次性限开盘 |
| `Add up to 10 stocks` | 最多 10 只 |
| `Amount per Cycle` / `Every Trading Day` | 每期金额 / 交易日 |
| `Create Plan` / `Edit Plan` / `End Plan` / `Pause Plan` / `Resume Plan` / `Rename Plan` | 计划操作 |
| `Are you sure you want to end/pause/resume this recurring plan?` | 确认 |
| `Instantly execute your plan once with market orders` | 立刻按市价跑一期 |
| `Each cycle is funded from your selected wallets. The Funding wallet is used first; if it falls short, the remainder is drawn from your selected sources, transferring from the Spot wallet before redeeming from Simple Earn Flexible.` | 扣款顺序 |
| `Your plan runs at around 10:30 AM Eastern Time on this date. Actual execution may be a few minutes later...` | 执行时点 |
| `The estimated fee for each cycle. It's deducted from your investment amount per cycle...` | 每期费用口径 |
| `Holdings Breakdown` / `Hide 0 Allocation Assets` / `Purchased Shares` | 持仓拆分 |

### 行情 For You / B9

| 原文 | 用途 |
|---|---|
| `Today's Hotspot` | 今日热点 |
| `Market Brief` / `Key Notes` / `Movers Flash` | 简报 / 要点 / 异动 |
| `每日复盘` / `波动归因` / `涨幅领先` / `盯 ETF` / `昨日收益(USD)` / `年年上涨` | B9 卡片标题（这包里是中文整句） |
| `#MarketForYouRefresh#` | For You 刷新标记 |
| `AGenUI` | 动态卡片引擎名。`A2UI` 三字旧 |

英文演示稿（像占位，不当运营文案）：`AI Tokens Rally as NVIDIA Reports Record Earnings` 及对应中文「AI板块代币集体上涨…」。

### Jarvis / 语音 / music / 钱包 MP

| 原文 | 用途 |
|---|---|
| `Connecting to voice service…` | 连语音 |
| `Select the speech recognition model` / `ASR Model` | 选识别模型 |
| `Play voice` / `Pause voice` | 播/停 |
| `Voice service is temporarily unavailable.` / `Voice transmission interrupted.` | 语音失败 |
| `Music Playback` | music 模块播放（Media3 库句很多，这条跟落地页一起看） |
| `appId is not allowed to use wallet provider` / `no available wallet` | MP 钱包 provider |

## 旧文案，不要当成新的

| 原文 | 最早见到 |
|---|---|
| `Options (Coming soon)` | 3.17.1。Play base 这版仍能搜到英文 |
| `Dina Degen` | 3.17.1 `classes3.dex` |
| `Binance AI Pro is coming soon` / `Introducing Dual Identity in Chat` | 3.17.1 |
| `Auto Order Routing` / `Cost Price Settings` / `Message Requests` / `Create Agentic Wallet` / `Binance Hot Wallet` / `Trade Hub Now Available` / `module_square` | 3.20.1 |
| `Tokenized Stocks` / `Stock Perps` | 3.20.1 已有整句，不是这版新开 |
| `A2UI` | 3.20.1。这版新的是透明 Activity + voice-names |
| `Daily Report` / `For You` / `主力流入` | 旧子串或旧句。B9 整套路径才是新的 |
| `coming soon` / 单词 `Chase` | 旧子串 |
| `znf9fpiMh6ufdU3vDtAvi4` + `pages/buzz-appeal-quiz/index` | 3.20.1。这版只是字符串多了空的 `startPageQuery=` |
| `q7xVG7ra5ocEDmTGEQo9uX` + `pages/index/index` | 3.20.1 已有这组 query |
| `/bapi/composite/v4/friendly/pgc/feed/news/list` | 3.20.1 字节里已有 |
| `you found` | 旧子串，不是彩蛋 |
| 期权链 / 提前行权 / 每日洞察 / 烟花句 | 完整 3.19.8 有。Play base 搜不到中文 **≠ 删了** |

## 没进包

| 在找的 | 结论 |
|---|---|
| `Continue to X` / yellow cloth / under the cloth | 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 / 3.20.3 都没有。`bnc://x` 是短串，不是这句 |
| 明文 `美股期权` / `Covered Call` / `Cash-Secured Put` | 仍没有 |
| `secret menu` | 没有 |
| `Binance Music` / `Music Briefing` 整句 | 没有。只有模块名和 `Music Playback` |
| `Pre-IPO` / `Perp Stocks`（这种拼法） | 没有。`Stock Perps` 是旧句 |
| 明文 `buzz-appeal-quiz` | 仍只有 base64 `startPagePath` |
