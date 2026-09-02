# 3.20.1 文案

判定「新」：3.18.4 + 3.19.5 + **完整 3.19.8** 整包（dex + 完整 arsc + assets）UTF-8 / UTF-16LE 都没有。  
本轮扫描包是 Play base `币安 3.20.1.apk`（默认英文瘦 arsc）。**不能用来判中文下线。**

## 确认新增（三旧包整包没有）

### 美股下单 / AOR

| 原文 | 用途 |
|---|---|
| `Auto Order Routing` / `Auto Order Routing (AOR)` / `Auto Order Routing Terms` | 自动订单路由 |
| `This order is eligible for Auto Order Routing (AOR), where Binance may route your order to an Intermediary Order Book...` | 可走中间簿找价格改善 |
| `The 1s interval is not supported for AOR symbols` | AOR 标的不支持 1s K 线 |
| `The average filled price shown may include trades executed in the intermediary pair...` | 成交均价含中间对换算，仅供参考 |
| `Buy or Sell at a specific price or better. AOR may route your order to an intermediary order book to seek price improvement.` | 限价 + AOR 说明 |

### 钱包成本价

| 原文 | 用途 |
|---|---|
| `Cost Price Settings` | 成本价设置 |
| `New Average Price` / `New Average Price (Per Share)` | 新均价 |
| `New Cost Price` / `New Cost Price (Per Share)` | 新成本价 |
| `Average Price is the cumulative average buy cost. Selling does not affect it, and it does not reset automatically...` | 均价口径 |
| `Cost Price is the moving weighted average cost. Selling affects it, and it resets after the position is closed.` | 成本价口径 |
| `Average Price = Total purchase cost ÷ Total quantity purchased (based on data since August 1, 2021)` | 均价公式（口径从 2021-08-01 起） |
| `Cost Price= (Previous Cost × Previous Qty + Buy Price × New Qty) ÷ Total Qty` | 成本价公式 |
| `Switch and edit Cost Price or Average Price. The price is token-based and shared across accounts.` | 跨账户共享 |
| `Still switch the displayed cost price to Average Price?` | 切换确认 |

### 聊天 / Square

| 原文 | 用途 |
|---|---|
| `Message Requests` / `No message requests` / `You have pending message requests.` | 消息请求收件箱 |
| `Users can direct message you if they follow you on Square` | Square 关注才能私信 |
| `People On Square` | Square 上的人 |
| `Based on a comprehensive calculation of factors such as the number of Square posts, search volume, and the number of users adding it to their favorite list. For reference only.` | Square 热度口径 |
| `Stand out in the comments` / `token badge` | 评论区持仓徽章 |
| `Unban & Take Quiz` / `Community Guidelines Quiz` | 解封答题 |

### 个股研究 / 公司行动

| 原文 | 用途 |
|---|---|
| `Dividend History` / `Dividends Summary` / `Dividends Per Share (%1$s)` | 股息页 |
| `Cash Dividend: %1$s %2$s Per Share` | 现金股息 |
| `Stock Splits History` / `Reverse Stock Split` | 拆合股 |
| `Company Overview` | 公司概览 |
| `Finance Estimates` / `Financials Report` | 财务预估 |
| `Insider Activity` / `Insider Trading Trends` | 内部人交易 |
| `EPS estimates are based on analyst consensus data provided via Benzinga and are for reference only.` | 分析师一致预期（Benzinga） |

### 网格 / 跟单 / Earn / 钱包

| 原文 | 用途 |
|---|---|
| `Grid Density` / `New Grid Density Tips` | 网格密度 |
| `Formula: Grid Count ÷ ((Upper Price - Lower Price) / Lower Price × 100)` | 密度公式 |
| `Follow Top Traders' Live Signals` | 跟单实时信号 |
| `Filter lead traders currently holding TradFi symbols.` | 带单员 TradFi 过滤 |
| `Futures copy trade by %1$s` | 合约跟单署名 |
| `No deposit needed! Try Simple Earn for free — rewards are yours.` | Simple Earn 免存试用 |
| `Earn <b>%1$s</b> APR Free — No Catch` | 免任务试用 APR |
| `Free Trial Fund, no tasks, no deposit.` | 试用金 |
| `Create Agentic Wallet` | AI Agent 钱包 |
| `Keyless wallet dedicated for your AI Agent` | 无密钥 Agent 钱包 |
| `Binance Hot Wallet` / `Binance: Hot Wallet` | Hot Wallet 展示名 |
| `Trade Hub Now Available` | 交易中枢 |

### 其它确认新增

| 原文 | 用途 |
|---|---|
| `After enabled, a "Chase" button is displayed in the Open Orders list...` | 挂单 Chase |
| `Full Paid Securities Lending` | 全额证券借贷 |
| `Withdraw Arbitrage Profit` | 提取套利利润 |
| `Support for %1$s coming soon.` | 泛预告，没点名 |
| `Receive bStocks in your bStocks!` | 句式奇怪，像 bStock 公司行动入账 |
| `Quiz unavailable.` | quiz 不可用 |
| `Mercad de ações dos Estados Unidos disponibilizado pela Alpaca Securities LLC.` | 葡语 Alpaca 免责；产品不是新的，这句 locale 是新的 |

竞赛 / 活动句（新进包，但是运营）：`ETH Options Trading Cup`、`GRVT Trading Challenge`、`Altcoins Summer Sprint`、`Stars & Stripes Futures Competition`、`Complete Tasks to Share 2,100,000 ESP Rewards!`、`Join the Options Competitions and Share 20,000 USDT in Rewards!` 等。

## 旧文案，不要当成新的

| 原文 | 最早见到 |
|---|---|
| `Options (Coming soon)` | 3.17.1。Play base 这版仍能搜到英文 |
| `Dina Degen` | 3.17.1 `classes3.dex` |
| `Binance AI Pro is coming soon` / `Introducing Dual Identity in Chat` | 3.17.1 |
| `Binance AI Preference` | 旧。这版新的是 `Binance AI Tooltip Frequency` |
| `Stock Dividend` / `Cash Dividend` | 短词旧；完整页标签才是新的 |
| `coming soon` / 单词 `AOR` / 单词 `Chase` | 旧子串，不能当新功能 |
| `znf9fpiMh6ufdU3vDtAvi4` / `daRdj4PkKgdy6HNB2dgwDC` / `gE3L87HgrhVrM5YAeaseWc` | 旧 appId。新的是 query 或另一个 id |
| `commission/get` 这段路径 | 旧子串。新的是 **v2** 完整路径 |
| `you found` | 旧子串，不是彩蛋 |
| 期权链 / 提前行权 / 每日洞察 / 烟花句 | 完整 3.19.8 有。Play base 搜不到中文 **≠ 删了** |

## 没进包

| 在找的 | 结论 |
|---|---|
| `Continue to X` / yellow cloth / under the cloth | 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 base 都没有 |
| 明文 `美股期权` | 仍不用这个 slogan |
| 明文 `buzz-appeal-quiz` | 只有 base64 `startPagePath` |
| `secret menu` | 没有 |
| 用户向中文新句 | Play base 瘦 arsc 里几乎没有；dex 里那 30 来条中文全是 Live 引擎调试日志 |
