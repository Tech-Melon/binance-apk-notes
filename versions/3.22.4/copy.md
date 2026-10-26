# 3.22.4 文案

判定「新」：3.18.4 + 3.19.5 + 完整 3.19.8 + 3.20.1 / 3.20.3 / 3.20.5 Play base + 3.20.6 完整包 + 3.21.6 Play base + **3.22.3 Play base**，整包 UTF-8 / UTF-16LE 都没有。  
这一包和 3.22.3 都是 Play base。完整包里有、瘦 arsc 里没有的译文 **不能写成这版删了**。  
`versionCode` 连号，中间没有未入库的 versionName。

## 确认新增

| 原文 | 用途 |
|---|---|
| `Futures Account Migration` | 巴西合约迁移标题 |
| `As per new Brazilian regulations effective 30 October 2026, your futures trading must move to a separate ADGM international account.` | 法规日和迁移动机。后半句是没有账户就在同意时创建 |
| `Agree and Migrate` / `Confirm Migration` / `Stay in Brazil` | 同意迁移、确认、留在巴西 |
| `Acknowledge & Switch account` | 确认并切换账户 |
| `During migration, your positions will be frozen. You won't be able to trade, close or reduce positions, or transfer funds.` | 迁移过程中仓位冻结 |
| `Once migration starts, it can't be undone. After migration, futures on your current Binance Brasil account will be disabled. Spot and other products are not affected.` | 不能撤销。现货不动 |
| `Your open positions ... will be transferred automatically to your new ADGM international account` | 持仓和保证金自动转走，含子账户 |
| `Any unfilled open orders (such as limit and stop-limit orders) will be cancelled.` | 未成交单取消，要在新账户重下 |
| `Your unrealized PnL is preserved, and your entry price stays the same.` | 盈亏和开仓价保留 |
| `You can transfer funds freely between your Binance Brasil account and your international account at any time.` | 两个账户可以互转 |
| `Futures trading permission will be removed from all API keys on your current Binance Brasil account and its sub-accounts.` | 旧账户 API 的合约权限会被拿掉 |
| `Market volatility may trigger liquidation immediately after migration.` | 迁移刚结束可能被强平，文案写币安不负责 |
| `Futures trading is now available on ADGM international accounts only.` | 此后合约只在 ADGM 账户。残留在巴西账户上的仓位要自己处理 |
| `Worried about a position or an order? Handle it first, then come back to migrate.` | 先处理仓位和订单再迁移 |
| `{0} BTC is currently unavailable for withdrawal due to pending U.S. stock trading processing fees or collateral requirements.` | 美股处理费或抵押品未结清，冻住 BTC 提现 |
| `Funds are frozen due to U.S. stock trading requirement` | 同上，短句 |
| `由于美股交易处理费或抵押品要求尚未结清，{0} BTC 暂时无法提现。` | 上句的中文 |
| `You have violated the Binance Chatroom Community Guidelines.` 加三条原因 | 乞讨募资、垃圾信息、推广第三方频道或付费服务。这次只警告 |
| `Confirm this is you logging in on the web.` / `Log in to Binance Web` | 网页扫码登录确认 |
| `Confirm this is you logging in on the desktop.` / `Log in to Binance Desktop` | 桌面端同一套 |
| `请确认是您本人在网页端登录。` / `登录币安网页端` | 上两句的中文。桌面端是「桌面端」 |
| `Resend ({{second}}s)` | 重发倒计时的英文整句。键名 `mfa-resend-countdown` 是旧的 |
| `You are initiating a withdrawal. If you did not initiate this action...` | 提现防钓鱼。确认是本人就 10 分钟后再试 |
| `As of %1$s, your total asset value was %2$s %3$s, with a 24-hour change of %4$s` | 资产市值快照。没有新页面 |
| `Unable to Place Order` | 只在这一包的短句。没有新 Activity，不单独当功能名 |
| `Sell clicked` | 点击日志。`Buy clicked` 是旧的 |

反诈提现的长句在 `mp-bids-mfa-ui` 文案表里，和上面的聊天室、美股冻结、扫码登录是同一批新增键。代表句是欺诈地址、仿冒网站、同 gas 来源、签完风险披露才能继续提。键名见 [params.md](params.md)，不把每一句都再抄一遍。

## 旧文案勿当成新

| 原文 | 实际 |
|---|---|
| `Buy US Stocks on Binance` / `Options Product Suitability Assessment` | 3.22.3 就有 |
| `Options (Coming soon)` / `Trade U.S. Stock Options` | 还在。3.21.6 起 |
| `Covered Call` / `Meme Rush` / `Pancake Pre IPO` / `25,000 USDT` | 还在 |
| `Binance Deutschland GmbH & Co. KG` / `CM-Equity AG` / `No, I am not a German resident` | 五个对照包里都有。JSON 碎块看起来像新句，裸句子是旧的 |
| `mfa-scene-action-pay` / `withdraw` / `crypto-box` / `transfer-web3` / `mfa-verify-scene-tip` | 3.21.6 和 3.22.3 就有。这版只是写进 `mp-bids-mfa-ui` |
| `StockRankAnomalyFilter` | 裸类名旧包就有。新的只是 R8 签名整段 |
| `switchLogin` | 裸词旧包就有。新的是 `authcenter/mirror/switchLogin` 这条路径 |
| `Discover More` / `Buy clicked` / `you found` | 旧 |
| `我进场就像放烟花` | 这一包没有。3.22.3 Play base 也没有。完整包有 |

`SCAM_BLACK_ADDRESS_WITHDRAW_FORBIDDEN_v3` 的键是旧的，英文从 “withdrawals have been temporarily restricted” 改成 “making withdrawals has been temporarily restricted”。

## 未进包

`Continue to X`、yellow cloth、under the cloth。黄布继续盯远程小程序 / CMS / `getUserAppFeatures` v3。  
明文 `美股期权`、`Binance Music`、`secret menu`、带连字符的 `Pre-IPO` 仍没有。

## 这一包拿走的

`https://app.binance.com/uni-qr/report-landing` 只在 3.22.3 有。3.22.4、3.21.6、3.20.6 都没有。
