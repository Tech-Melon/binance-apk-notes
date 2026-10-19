# 3.22.3 文案

判定「新」：3.18.4 + 3.19.5 + 完整 3.19.8 + 3.20.1 / 3.20.3 / 3.20.5 Play base + 3.20.6 完整包 + **3.21.6 Play base**，整包 UTF-8 / UTF-16LE 都没有。  
这一包和 3.21.6 都是 Play base。完整包里有、瘦 arsc 里没有的译文 **不能写成这版删了**。  
没有 3.21.7–3.22.2。

## 确认新增

| 原文 | 用途 |
|---|---|
| `Buy US Stocks on Binance` / `Own Real US Stocks` | 买美股正股 |
| `Trade US Stock Options` / `Calls & Puts on 1,000+ US Stocks & ETFs` | 股票和 ETF 的认购 / 认沽 |
| `Buy calls if you expect prices to rise, or puts if you expect prices to fall.` | 期权方向说明 |
| `Defined Risk When Buying Options` / `Know your risk before you buy. The maximum you can lose is the premium you pay.` | 买入期权最多亏权利金 |
| `Orders are routed to US options exchanges via Alpaca Securities.` | 路由点名 Alpaca。3.21.6 有路由句，没有这句 |
| `Exercise a Call and the underlying US shares are delivered to your account, custodied by Alpaca Securities.` | 行权后正股托管在 Alpaca |
| `Options Product Suitability Assessment` | 适当性评估。及格 80%，主账户，30 天内，失败后 7 天冷却 |
| `This option is now within the final %1$s minutes before market close` | 收盘前自动处理。公开配置里 `closeOnlyMinutes` 是 45 |
| `final %1$s minutes before expiration` / `automatically liquidated` | 到期前最后一段只能平仓 |
| `Commodity Channel Index` / `Volume Weighted Average Price` | CCI、VWAP 全称。单词 `VWAP` 是旧的 |
| `Place an eligible P2P order with a verified merchant to earn cashback.` | 找认证商家下 P2P 单拿返现 |
| `Cashback will be credited in USDT to your Spot Account within 24 hours` | 返现进现货，24 小时 |
| `This Voucher provides a one-time cashback on eligible P2P deposits.` | 一次性 P2P 入金券 |
| `The UTR is invalid. Copy the complete UTR from your payment app.` | 印度付款参考号不完整 |
| `Explore Rewards on Yield Arena` / `Your one-stop Earn campaign center` | Earn 活动中心 |
| `Complete Tasks to Share 200 BNB Rewards!` | 200 BNB 任务奖池 |
| `Fixed Rate Loan Collateral` / `Pay Later Collateral` / `Pay Later Outstanding Balance` | 固定利率和先买后付的抵押展示 |
| `Institutional Loan Liquidation` / `Est. Repay Total` / `Pairs to repay` | 机构贷强平、预计还款、按交易对还 |
| `Each pair is processed independently and may partially succeed.` | 多交易对还款可以部分成功 |
| `Copy a lead trader with virtual funds, risk-free.` | 用模拟金跟单 |
| `Futures Competition Round 2` / `Prize Pool of 500 BNB` | 合约竞赛第二轮 |
| `TradFi Perp Competition Round 2` | TradFi 永续竞赛第二轮 |
| `Join the TradFi Trading Competition for a Prize Pool of Up to 250,000 USDC!` | 整句是新的。`250,000 USDC` 这串数字旧包就有 |
| `BTC & ETH Options Trading Cup` | 币本位期权杯 |
| `Based on your IP, you're in Germany... Binance Deutschland GmbH` | 德国 IP 要签当地协议。公司名是旧的，整句是新的 |
| `Action Required: Verify Your Address` / `Account Review Not Passed` | 地址核验和账户审查，旁边是 Persona 域名 |
| `App signature check failed — this build may not be official.` | 安装包签名不像官方包 |
| `Number of Binance Wallet users holding this token.` | 持有这个代币的钱包用户数 |
| `Of all tokens previously launched by this creator, the share that successfully migrated to a DEX.` | 创建者历史代币迁到 DEX 的比例 |
| `Share of supply held by addresses that bought via bundled transactions in the same block.` | 同块捆绑买入的筹码占比 |
| `Buy and sell tax charged by the token contract` | 合约买卖税 |
| `Total trading fees this token has generated on-chain since creation.` | 创建以来的链上手续费 |
| `Wallet name must be 1–20 characters.` | 钱包名长度 |
| `No wallet backup found in this Google Drive account.` | 这个 Google 账号里没有备份 |
| `Biometric verification is not working properly on this device.` | 生物识别坏了，建议改密码 |
| `Couldn't connect to this dApp.` / `maximum number of connected dApps` | dApp 请求不支持，或连接数满了 |
| `The outcome is determined by an on-chain oracle or smart contract, not by Binance.` | 预测结果看链上预言机，不是币安裁定 |
| `Adjusts the time zone shown on the time axis of the charts.` | 改的是时间轴显示，不改 K 线数据 |
| `After switching, the change (%) for Spot, Margin, Options and Futures is recalculated in the new time zone.` | 涨跌幅按时区重算，Alpha 不支持 |

dex 里还有 `已订阅-引导完成`、`未订阅-引导中` 这种中文调试句。那是工程师状态，不是界面文案。Play base 本来就没有完整中文表。

## 旧文案，不要当成新的

| 原文 | 最早见到 |
|---|---|
| `Options (Coming soon)` | 3.17.1 起，这版还在 |
| `Trade U.S. Stock Options — Now on Binance` | 3.21.6 |
| `Covered Call` / `Cash-Secured Put` | 3.21.6 |
| `Meme Rush` / `Pancake Pre IPO` | 3.21.6 |
| `25,000 USDT` 期权竞赛句 | 3.21.6 |
| `20,000 USDT` | 3.20.1 |
| `Short Interest` / `shares sold short and not yet covered` | 3.21.6 |
| `Stock traders:` / `Non-stock traders` / `stock settlement` | 3.21.6 |
| `Binance Deutschland GmbH` | 3.20.5 及更早。新的是包住它的德国 IP 整句 |
| `VWAP` 这个单词 | 3.20.5 及更早。新的是全称和 `EditVWAPFragment` |
| `cashback` 这个单词 | 更早的包。新的是 P2P 返现那几句 |
| `250,000 USDC` 这串数字 | 更早的包。新的是 TradFi 竞赛整句 |
| `Dina Degen` | 3.17.1 起 |
| `you found` | 旧包里的子串，不是 secret menu |

## 没进包

| 在找的 | 结论 |
|---|---|
| 黄布 / `Continue to X` / `yellow cloth` / `under the cloth` | 3.18.4 到 3.22.3 都没有 |
| 明文 `美股期权` | 仍没有 |
| `Binance Music` | 仍没有。R8 签名里的 `MusicFragmentBriefingBinding` 是旧类 |
| `secret menu` | 没有 |
| 带连字符的 `Pre-IPO` | 没有。3.21.6 的 `Pancake Pre IPO` 还在 |
| `我进场就像放烟花` | 3.19.8 / 3.20.6 完整包有。这一包和 3.21.6 都是 Play base，没有。不是这版删的 |
