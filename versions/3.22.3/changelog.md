# 3.22.3 相对 3.21.6

对照：`币安 3.21.6.apk`（Play base）→ `币安 3.22.3.apk`（Play base）。  
「这句是新的」在 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 / 3.20.3 / 3.20.5 / 3.20.6 / **3.21.6** 上整包对过（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
**两边包装相同。** 文件差集可以当产品候选。相对 3.20.6 universal 缺 so / 缺中文仍是包装。  
手头没有 3.21.7–3.22.2。

## 产品

1. **美股写成能买正股，期权加上适当性评估和收盘限制**  
   3.21.6 的开卖句 `Trade U.S. Stock Options — Now on Binance` 还在。这一包另起一套：  
   `Buy US Stocks on Binance` / `Own Real US Stocks` / `Trade US Stock Options`  
   `Calls & Puts on 1,000+ US Stocks & ETFs`  
   `Buy calls if you expect prices to rise, or puts if you expect prices to fall.`  
   `Orders are routed to US options exchanges via Alpaca Securities.`  
   `Exercise a Call and the underlying US shares are delivered to your account, custodied by Alpaca Securities.`  
   开通前要过 `Options Product Suitability Assessment`，及格线 80%。子账户不行，要在主账户做。30 天内要完成，没过要等 7 天冷却。  
   新类 `EquityWelcomeIntroStock`、`EquityWelcomeIntroStockOption`。  
   公开 `option/get-config` 返回 `closeOnlyMinutes=45`、`liquidationPeriod=30`。文案对应收盘前最后几分钟不能再加仓，风险仓会被自动平掉。  
   页面 `https://www.binance.com/en/stocks/options/`。键 `KEY_OPTIONS_GEN`。
2. **图表多了 CCI 和 VWAP 的编辑页**  
   `EditCCIFragment`、`Commodity Channel Index`、`Volume Weighted Average Price` 只在这一包。  
   单词 `VWAP` 旧包就有，新的是全称和这个 Fragment。
3. **P2P 返现，以及一大批 C2C 路径**  
   `Place an eligible P2P order with a verified merchant to earn cashback.`  
   返现打进现货账户，24 小时内到账。单词 `cashback` 是旧的，这几句不是。  
   另外有 UTR 校验失败、付款方式不可用。  
   205 条 `/bapi/c2c/` 精确路径在旧包里都没有。公开能打通的有帮助视频、分享口令配置、法币充值通道、AI 助手配置。详见 [apis.md](apis.md)。  
   深链 `bnc://app.binance.com/p2p/chat?groupId=`。
4. **Earn 活动中心、贷款还款、跟单模拟金**  
   `Explore Rewards on Yield Arena`  
   `Your one-stop Earn campaign center`  
   `Complete Tasks to Share 200 BNB Rewards!`  
   贷款侧：`Fixed Rate Loan Collateral`、`Pay Later Collateral`、`Institutional Loan Liquidation`、`Est. Repay Total`、`Pairs to repay`。多交易对还款可以部分成功。键 `INSTITUTIONAL_LOAN_LIQUIDATION_TRANSFER`。  
   跟单：`Copy a lead trader with virtual funds, risk-free.` 类名 `CopyTradingQuickCopyComponent` 是旧的。
5. **竞赛句换了一批**  
   `Futures Competition Round 2` / `Join the Futures Competition for a Prize Pool of 500 BNB!`  
   `TradFi Perp Competition Round 2`  
   `Join the TradFi Trading Competition for a Prize Pool of Up to 250,000 USDC!`（数字 `250,000 USDC` 旧包就有，整句是新的）  
   `BTC & ETH Options Trading Cup`  
   3.21.6 的 25,000 USDT 期权竞赛句还在。
6. **钱包说明和 Persona 地址核验**  
   持仓地址数、创建者迁移到 DEX 的比例、同块捆绑买入占比、代币买卖税、链上累计手续费，这些解释句是新的。  
   钱包名 1–20 字、Google Drive 找不到备份、生物识别失败就改走密码、dApp 请求不支持、连接数到上限。  
   域名 `withpersona.us`（`app` / `inquiry-fallback` / `tg` / `webrtc-consumer`）第一次出现，旁边是 `Action Required: Verify Your Address`、`Account Review Not Passed`。  
   新类 `AlphaCryptoUnavailableDialog`。
7. **自选分组和 AI Pro 事件通道**  
   深链可以建自选组、把交易对加进组、编辑分组、隐藏持仓。  
   新文件 `StrategyAgentEventMsg.proto`，频道名 `AI_DATA_STRATEGY_AGENT_EVENT`。`aipro/version` 和 `strategy/app/more` 要登录。  
   `assets/jarvis_landing_share_capture.js` 是落地页小程序截图，不是新的用户功能名。

## 从包里去掉的页面和路径

Manifest 相对 3.21.6 少 3 个 Activity，类名在这一包的 dex / arsc / assets 里也搜不到：

- `BuyWithBankTransferDetailActivity` 银行转账买币详情
- `FiatManageCardForSellActivity` 卖出时的银行卡管理
- `VOptionsPreferenceActivity` 香草期权偏好页。`VOptionsOrderConfirmDialog` 还在，不是整个期权下单没了

精确路径字符串消失，不等于产品下线：

- `/bapi/apex/v1/public/apex/market/holiday-atmosphere` 在 3.20.6 和 3.21.6 都有，这一包没有
- `/bapi/mp/gc/tenant/v2/private/leaderboards/`、`/bapi/mp/v3/tenant/apps/qrcode/get-content` 同样从这一包消失
- 3.21.6 才出现、3.20.6 完整包里没有的几条 Earn / AI widget 路径，精确字符串也不在 3.22.3：`yield/pool/detail`、`pool/statistics`、`token/info`、`protocol/list`、`ai-widget/query`、`ai-widget/hot-zone/config`、`alpha-event/competition/query`
- 几条带 `gridType=arbitrage` / `futuresDCA` / `futuresGrid` / `futuresSnowball` 的策略历史深链整段没了。`gridType=` 这个参数还在

3.20.5 起就没有、3.21.6 也没有的法币店铺和双币旧页，不是这版新删的。

## 基础设施

- 小程序运行时仍 **5.16.4**。三个内置 MP id 不变。
- Flutter package 仍 15。skylinef 多了 black / bold / light / medium / semibold 五套字体文件。
- 权限相对 3.21.6 **无增减**。相对 3.20.6 少 `REQUEST_INSTALL_PACKAGES`，是包装。
- `res/raw/` 相对 3.21.6 大约 675 增、664 删，哈希文件名轮换。
- DEX 全量 CRC 会变，是 R8 重打包，不当成业务重写。
- OkHttp 的 `publicsuffixes.gz` 换成 `assets/PublicSuffixDatabase.list`，是依赖换文件。
- 德国合规句 `Based on your IP, you're in Germany... Binance Deutschland GmbH` 整句是新的。公司名本身旧包就有。
- `App signature check failed — this build may not be official` 是新的安装包签名提示。

参数和深链见 [params.md](params.md)。类名和域名见 [surface.md](surface.md)。接口全量路径见 [apis.md](apis.md)。
