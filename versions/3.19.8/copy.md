# 3.19.8 文案

判定「新」：3.18.4 + 3.19.5 整包（dex + **完整** arsc + assets）UTF-8 / UTF-16LE 都没有。  
完整对照包：`BNApp64_V3.19.8.apk`（中/繁/日都在）。Play base 只有默认英文，不能用来判中文下线。

## 确认新增（两旧包整包没有）

### 美股期权

| 原文 | 中文包 | 用途 |
|---|---|---|
| `Failed to load option chain` / `No option chain data available` | — | 期权链空态 |
| `Turn on Real-time Quotes` | `开启实时报价` | 15 分钟延时 → 实时 |
| `Your options quotes are delayed by 15 minutes...` | `您的期权报价将延迟 15 分钟。开启实时报价，即可在本月剩余时间查看实时数据。…` | 延时说明 |
| `Real-time quotes stay on automatically when you:` | `在下列情况中，实时报价将自动保持开启：` | 保活条件 |
| `Hold an options position` | `持有期权仓位` | 条件 1 |
| `Place an options trade this month.` | `本月进行一笔期权交易。` | 条件 2 |
| `Early Exercise` | `提前行权` / 繁 `提前行使` | 提前行权 |
| `View Exercise Event` | `查看行权事件` | 行权事件 |
| `Options Assignment` | `期权分配` / 繁 `期權指派` | 指派 |
| `I understand this exercise request cannot be cancelled in app and will result in cash or stock settlement.` | `我已知悉，此行权申请在 App 内无法取消，并最终以现金或股票形式结算。` | 行权不可撤销 |
| `If you still hold this option at expiration, the system will attempt to automatically sell your position.` | `如果您在到期时仍持有该期权，系统将尝试自动卖出您的仓位。` | 到期自动平 |
| `This option has entered the final 30 minutes before market close and only supports closing positions.` | `该期权已进入到期日收盘前最后 30 分钟，仅支持平仓。`（另有美东 15:30 长说明） | 到期日最后 30 分钟 |
| `ORF (Options Regulatory Fee)` | `期权监管费（ORF）` | 规费 |
| `OCC (Options Clearing Corporation Fee)` | `OCC（期权清算公司费用）` | 规费 |
| `FINRA Trading Activity Fee (TAF)` / `FINRA Consolidated Audit Trail Fee (CAT)` / `SEC Transaction Fee` | `FINRA 交易活动费（TAF）` / `FINRA 综合审计追踪费用（CAT）` / `SEC 交易手续费` | 规费拆条 |
| `The estimated total fees are for reference only... BNB fee discounts are currently not supported.` | — | 预估费 + 无 BNB 折扣 |
| Position-level Delta/Gamma/Theta/Vega 四段 | `仓位级 Delta/Gamma/Theta/Vega` 四段（1 张 ≈ 100 股） | 希腊值 |
| `CC and CSP oder confirmation` | `CC 和 CSP 订单确认`（英包 `oder` 拼错） | Covered Call / Cash-Secured Put。全文 `Covered Call` / `备兑` **不在包里** |
| `Convert & Buy Now` | `兑换并立即买入` | 期权页闪兑再买 |
| `%1$d DTE` / `%1$d Days To Expiration` | `距离到期还有 %1$d 天` | 距到期 |
| `Open Interest (OI)` 作为完整标签 | `未平仓量（OI）` | 期权链列（`Open Interest` 三字旧包就有） |

### 个股研究 / 资产

| 原文 | 中文包 | 用途 |
|---|---|---|
| `Daily insights` | `每日洞察` | 个股研究卡 |
| `Macro Analysis` / `Technical Analysis` / `Core Conclusion` | `宏观分析` / `技术分析` / `核心结论` | 同上 |
| `Market Sentiment and Risks` / `Key Drivers` / `Sector Drivers` | `市场情绪与风险` / `关键动因` | 同上 |
| `Investment Performance Summary` | `投资表现摘要` | 资产表现 |
| `Yesterday's PnL = Yesterday's final asset...` | `昨日盈亏 = 昨日账户期末资产 - 昨日 00:00:00 UTC 的期初资产 - 净转账和充值` | 公式新；「昨日盈亏」四字旧 |
| `Chart data will adjust according to corporate actions` | `图表数据将根据公司行动进行调整` | 复权 |

### 其它确认新增

| 原文 | 中文包 | 用途 |
|---|---|---|
| `Price difference is too small. Max number of grids to run this bot is %1$s.` | `价差过小。 运行该机器人的最大网格数量为%1$s。` | 网格上限 |

## 旧文案，不要当成新的

| 原文 | 最早见到 |
|---|---|
| `Options (Coming soon)` / `期权（即将上线）` | 3.17.1。完整包 **中英都还在**，和已上线期权链并存 |
| `您已签署协议，现在可以交易 TradFi 期权了` | 3.19.5。完整包仍有 |
| `期权链` / `期权行权` / `期权到期` | 3.18.4 就有，单词级旧标签 |
| `Stock Options` / `Implied Volatility` / `Open Interest` / `Strike` / `Expiry` / `Exercise` | 3.19.5 或更早 |
| `US Stocks, Now on Binance!` / `美股现已上线币安！` | 3.19.5 |
| `Add prediction market` | 3.19.5 |
| `Dina Degen` | 3.17.1 `classes3.dex` |
| 烟花 / to the moon / `我进场就像放烟花` | 3.17.1 `resources.arsc`，完整 3.19.8 仍有 |
| `Binance AI Pro is coming soon` / `Introducing Dual Identity in Chat` | 3.17.1 |
| `昨日盈亏` / `监管费用` | 旧标签，这版只是补了长说明 |
| `q7xVG7ra5ocEDmTGEQo9uX` | 3.18.4 起就有。新的是 query，不是 appId |
| `usOptions` 前缀 | 旧。新的是 `/trade`、`/options-position-details`、`/eventDetail` |
| `POV 订单（即将上线）` | 3.19.5，完整包仍有 |

## 没进包

| 在找的 | 结论 |
|---|---|
| `Continue to X` / yellow cloth / under the cloth | 3.18.4 / 3.19.5 / 完整 3.19.8 都没有 |
| 明文 `美股期权` / `US Options` | 完整 arsc 也不用这个 slogan |
| 明文 `Covered Call` / `Cash-Secured Put` / `备兑` / `现金担保` | 只用 `CC 和 CSP 订单确认` |
| 明文 `/stocks/quiz` | 只有双重 base64 |
