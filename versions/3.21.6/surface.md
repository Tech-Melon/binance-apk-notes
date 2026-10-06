# 3.21.6 页面和客户端表面

Manifest 的 Activity 同时对过 3.20.6 和 3.20.5。类名再在 3.20.6 / 3.20.5 / 完整 3.19.8 里搜裸名字。  
R8 签名里出现旧类，不算新页面。

## Manifest 新增的 Activity

| 类 | 做什么 |
|---|---|
| `com.binance.c2c.chat_new.contact.contacts.ContactsActivity` | 聊天联系人。`ContactsViewModel` 这个名字旧包就有 |
| `com.binance.c2c.chat_new.groupchat.BinanceChatGroupSheetActivity` | 群聊半屏 |
| `com.binance.c2c.chat_new.ui.BinanceChatPrivateSheetActivity` | 私聊半屏。包内 LCP 配置把它绑到 `order-detail` 和 `query-chat-by-page` |
| `com.binance.c2c.chat_new.privatechat.setting.remark.RemarkEditActivity` | 改备注 |
| `com.binance.content.internal.activity.ContentCopyTradingDialogActivity` | 内容里的跟单弹窗 |
| `com.binance.content.internal.activity.ContentShareTradingAssetContentDialogActivity` | 分享交易资产 |
| `com.finance.marketdetail.feature.business.tradfi.TradFiMarketDetailLandActivity` | TradFi 行情横屏 |
| `com.insurance.wallet.activities.main.funds.migrate.FundingMigrateActivity` | 资金账户迁到现货 |

## 裸类名确认是新的

这些不在 3.20.6、3.20.5、3.19.8 里：

| 类名 | 做什么 |
|---|---|
| `TradFiAnalysisViewModel` | 股票分析。旁边有新模型 `TradFiAnalysisSummaryPO`、`AnalystConsensusPO` |
| `TradFiAnalystRatingsViewModel` | 分析师评级 |
| `AlphaAIPrivateDataService` | Alpha 竞赛私有数据。文件名 `AlphaAIPrivateDataService.kt` 也在 |
| `EarnAIPrivateDataService` | Earn 的 AI 私有数据 |
| `EarnHomeAIPrivateDataService` | Earn 首页协议页 |
| `Web3HomeFragment` | Web3 首页 |
| `Web3HomeQuickAccessGateService` | Web3 首页快捷入口开关 |
| `HideChatsViewModel` | 隐藏会话 |
| `MediaPreviewViewModel` | 聊天媒体预览 |
| `RemarkEditViewModel` | 备注页 |
| `DiscoverRankingViewModel` | 发现页排行，对上 `ranking-list` |
| `FundingMigrateDoneDialog` / `FundingMigrateSuccessDialog` | 迁移完成弹窗 |
| `EarnMainV6VipFragment` | Earn 首页 V6 的 VIP 页。V6 的主 Fragment、ViewModel、高收益、保本页在 3.19.8 就有 |
| `MemeRush` | 和文案 `Meme Rush` 对应的符号。`MemeRank` 连写并不存在，界面是 `Meme Rank` |

`TradFiFinancialsViewModel` 在 3.20.5 和 3.21.6 有，3.20.6 完整包里没搜到。不当成这一版新类。`TradFiFinancialsV2PagerComponent`、`ITradFiTradeService`、`UsOptionChainQuoteWsPO` 更早的包就有。

## Manifest 去掉的 Activity

3.20.5 和 3.20.6 都有，3.21.6 没有。类名没了，不等于产品下线：

- 法币：`FiatStoreListActivity`、`FiatStoreSearchActivity`、`FiatMerchantStoreListActivity`、`FiatOrderThirdScanActivity`、`FiatThirdOrderDetailActivity`、`CashTradeSearchLocationActivity`
- 理财旧页：`LoanBorrowActivity`、`LoanHistoryActivity`、`DualInvestmentMainV2Activity`、`DualInvestmentProjectsActivity`
- `com.google.android.libraries.places.widget.AutocompleteActivity`

同一批 LCP 配置也从字符串里消失：现金广告列表、借款页、双币主页 V2、双币产品列表、双币的全部币对 / 收藏 / 推荐。双币主页 V2 绑的是 `banner/summary` 和 `option-configs/list`。

## 域名和依赖

| 字符串 | 3.19.8 | 3.20.5 | 3.20.6 | 3.21.6 |
|---|---|---|---|---|
| `https://massive.com` | 无 | 无 | 无 | 有。没有更长路径 |
| `binancezh.info` | 有 | 有 | 有 | 无 |
| `maps.googleapis.com` | 有 | 有 | 有 | 无 |
| `dtcc.com/client-center/dtc-directories` | 有 | 有 | 有 | 无 |
| `dtcc.com/support/dtc-directories` | 无 | 无 | 无 | 有 |

`maps.googleapis.com` 和 Places 的 `AutocompleteActivity` 一起消失，`places.properties` 换成 `play-services-places-placereport.properties`。这是依赖换库。  
`binancezh.info` 是三份旧包都有、这份 Play base 没有，不是「完整包才有的中文资源」。

## 这轮没有单独立项的

- so 符号：这份是 Play base，没有 `lib/`
- `res/raw/` 哈希文件：相对 3.20.5 大约 1348 增、1179 删，是资源轮换
- 服务端开关的当前值：包里只有上面的键
- 历史版本：3.20.1–3.20.6 已按同一口径补过。3.19.8 及更早仍是五页
