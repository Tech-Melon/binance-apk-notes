# 3.19.8 文案

这份包的 `resources.arsc` 只有约 7.5 MB 默认英文。中文句子对不上 **不等于产品删了中文**，只说明 locale 不在这个 APK 里。  
判定「新」：3.18.4 + 3.19.5 整包（dex + 完整 arsc + assets）UTF-8 / UTF-16LE 都没有。

## 确认新增（两旧包整包没有）

### 美股期权

| 原文 | 用途 |
|---|---|
| `Failed to load option chain` / `No option chain data available` | 期权链空态 |
| `Turn on Real-time Quotes` / `Your options quotes are delayed by 15 minutes...` | 15 分钟延时 vs 实时 |
| `Real-time quotes stay on automatically when you:` / `Hold an options position` / `Place an options trade this month.` | 实时行情保活条件 |
| `Early Exercise` / `View Exercise Event` / `Options Assignment` | 提前行权 / 指派 |
| `I understand this exercise request cannot be cancelled in app and will result in cash or stock settlement.` | 行权不可撤销 |
| `If you still hold this option at expiration, the system will attempt to automatically sell your position.` | 到期自动平 |
| `This option has entered the final 30 minutes before market close and only supports closing positions.` | 到期日最后 30 分钟只平仓 |
| `ORF (Options Regulatory Fee)` / `OCC (Options Clearing Corporation Fee)` | 规费名 |
| `FINRA Trading Activity Fee (TAF)` / `FINRA Consolidated Audit Trail Fee (CAT)` / `SEC Transaction Fee` | 美股期权规费拆条 |
| `The estimated total fees are for reference only... BNB fee discounts are currently not supported.` | 预估费 + 无 BNB 折扣 |
| `Position-level Delta/Gamma/Theta/Vega` 四段（1 张 ≈ 100 股） | 仓位希腊值说明 |
| `CC and CSP oder confirmation` | Covered Call / Cash-Secured Put（包内 `oder` 拼错） |
| `Convert & Buy Now` | 期权页闪兑再买 |
| `%1$d DTE` / `%1$d Days To Expiration` | 距到期天数 |
| `Open Interest (OI)` 作为完整标签（`Open Interest` 三字旧包就有） | 期权链列 |

### 个股研究 / 资产

| 原文 | 用途 |
|---|---|
| `Daily insights` / `Macro Analysis` / `Technical Analysis` / `Core Conclusion` | 个股研究卡 |
| `Market Sentiment and Risks` / `Key Drivers` / `Sector Drivers` | 同上 |
| `Investment Performance Summary` | 资产表现 |
| `Yesterday's PnL = Yesterday's final asset... UTC - Net transfer and deposit` | 昨日盈亏口径 |
| `Chart data will adjust according to corporate actions` | 复权 |

### 其它确认新增

| 原文 | 用途 |
|---|---|
| `Price difference is too small. Max number of grids to run this bot is %1$s.` | 网格数量上限 |

## 旧文案，不要当成新的

| 原文 | 最早见到 |
|---|---|
| `Options (Coming soon)` | 3.17.1。这版 **还在**，和已上线期权链并存 |
| `期权（即将上线）` / `您已签署协议，现在可以交易 TradFi 期权了` | 3.19.5 笔记已记。这份 3.19.8 **缺中文资源**，不能写成下线 |
| `Stock Options` / `Implied Volatility` / `Open Interest` / `Strike` / `Expiry` / `Exercise` | 3.19.5 或更早，单词级旧标签 |
| `US Stocks, Now on Binance!` | 3.19.5 |
| `Add prediction market` | 3.19.5 |
| `Dina Degen` | 3.17.1 `classes3.dex` |
| 烟花 / to the moon / `我进场就像放烟花` | 3.17.1 `resources.arsc` |
| `Binance AI Pro is coming soon` / `Introducing Dual Identity in Chat` | 3.17.1 |
| `q7xVG7ra5ocEDmTGEQo9uX` | 3.18.4 起就有。新的是 query，不是 appId |
| `usOptions` 这个前缀 | 旧包已有。新的是 `/trade`、`/options-position-details`、`/eventDetail` |

## 没进包

| 在找的 | 结论 |
|---|---|
| `Continue to X` / yellow cloth / under the cloth | 3.18.4 / 3.19.5 / 3.19.8 都没有 |
| 明文 `美股期权` / `US Options` | 这份英文 arsc 也不用这个 slogan，产品名走 `Stock Options` + `usOptions` 路由 |
| 明文 `/stocks/quiz` | 只有双重 base64 |
