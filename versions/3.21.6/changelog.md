# 3.21.6 相对 3.20.6

对照：`BNApp64 (2).apk`（universal）→ `币安 3.21.6.apk`（Play base）。  
「这句是新的」在 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 / 3.20.3 / 3.20.5 / **3.20.6** 上整包对过（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
**两边包装不同。** 缺 so、缺中文、没有 `REQUEST_INSTALL_PACKAGES` 不是产品下线。文件名差集同时对过 3.20.5 Play base 和完整 3.19.8。  
手头没有 3.20.7–3.21.5。

## 产品

1. **美股期权写成已经能交易**  
   旧预告 `Options (Coming soon)` 还在。新英文是另一套：  
   `Trade U.S. Stock Options — Now on Binance`  
   `NVDA, AAPL, TSLA and 1,000+ U.S. stock options.`  
   `Orders are routed to US options exchanges, giving you access to listed US options contracts and market liquidity.`  
   `Activate US Stock Options` / `Options Account Activated`  
   `Quotes are delayed by 15 min. Activate your Options account for real-time quotes.`  
   备兑和现金担保第一次以完整句子进包：`Covered Call`、`Cash-Secured Put`，以及 Collateral / Risk Notice。到期实值会被指派、要卖出或买入正股，写在风险说明里。  
   新页面 `TradFiMarketDetailLandActivity`。深链 `bnc://app.binance.com/markets/marketsDetail?at=equity&assetCode=EQ_NVDA&selectTab=options`。  
   公开接口 `option/get-symbols-index` 返回约 1044 个标的，样例 `SPY` / `EQ_SPY`、`QQQ` / `EQ_QQQ`。下单路径 `order/oto/place`、`order/otoco/place` 要登录。
2. **期权竞赛奖池改成 25,000 USDT**  
   `Join the Option Competitions and Share 25,000 USDT in Rewards!` 只在这一包。  
   3.20.1 起的 `20,000 USDT` 那句还在，两句并存。
3. **Meme Rush / Meme Rank**  
   两个名字只在这一包。旁边是失败日志 `meme rush load failed`，不是独立彩蛋。脉冲榜接口 `pulse/rank/home/card` 公开可打，字段有 `tokenList`、`migratedCount`、`risingCount`。
4. **Pancake Pre-IPO**  
   `Pancake Pre IPO`、`Pre IPO` 只在这一包。带连字符的 `Pre-IPO` 仍然没有。
5. **资金账户迁到现货**  
   新页面 `FundingMigrateActivity`。  
   `/bapi/asset/v1/private/asset-service/funding-migrate/config`  
   `/bapi/asset/v1/private/asset-service/funding-migrate/migrate-to-spot`  
   `/bapi/c2c/v1/private/c2c/funding-migration/can-migrate`  
   前两条未登录是 `100001005`。
6. **聊天和内容多了 6 个页面**  
   `ContactsActivity`、`BinanceChatGroupSheetActivity`、`BinanceChatPrivateSheetActivity`、`RemarkEditActivity`、`ContentCopyTradingDialogActivity`、`ContentShareTradingAssetContentDialogActivity`。  
   深链 `bnc://app.binance.com/p2p/addContact?scenario=1&source=Homepage`。
7. **发现页排行和 B9 简报换版本**  
   公开 `discover/trading/ranking-list` 返回 `COPY_TRADING` / `SMART_MONEY` / `TRADING_BOT`。  
   日报从 `detail-v3` / `history-v3` 换成 `detail-v4` / `history-v4` / `display-v4`。自选从 v1 换成 `apex/v2/.../watch-market`。资产报告从 mimir v2 换成 v3。这些是客户端路径替换，旧路径字符串从包里消失。

## 看起来像下线，其实要分开看

下面的 Activity 在 3.20.5 和 3.20.6 的 Manifest 里都有，3.21.6 没有。类名没了，不等于整个产品下线：

- 法币店铺 / 现金交易：`FiatStoreListActivity`、`FiatStoreSearchActivity`、`FiatMerchantStoreListActivity`、`FiatOrderThirdScanActivity`、`FiatThirdOrderDetailActivity`、`CashTradeSearchLocationActivity`
- 理财旧页：`LoanHistoryActivity`、`LoanBorrowActivity`、`DualInvestmentMainV2Activity`、`DualInvestmentProjectsActivity`
- `AutocompleteActivity`：Google Places 依赖换文件（`places.properties` 换成 `play-services-places-placereport.properties`），不是币安功能

相对完整 3.20.6 少掉的 eKYC / 人脸模型、76 个 so、`classes26.dex`–`classes28.dex`，3.20.5 Play base 里同样没有。那是包装。

## 基础设施

- 小程序运行时仍 **5.16.4**。三个内置 MP id 不变。
- Flutter package 仍 15。三个图标从 `module_content` / `module_live` 换到 `lib_base` 的 `ic_close_1c` / `ic_plus_1c` / `ic_search_1c`，是资源改名。
- 权限相对 3.20.5 **无增减**。相对 3.20.6 少 `REQUEST_INSTALL_PACKAGES`，是包装。
- `res/raw/` 相对 3.20.5 大约 1348 增、1179 删，哈希文件名轮换。
- DEX 全量 CRC 会变，是 R8 重打包，不当成业务重写。
- 法币资产列表客户端从 `/bapi/fiat/v1/.../get-asset-list` 换成 v2。v2 公开可打，`assets` 里约 1517 条。
