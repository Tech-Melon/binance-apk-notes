# 3.21.6 接口

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`，`User-Agent: Binance/3.21.6 (Android)`

路径来自 dex + 瘦 arsc + 小配置 assets 的差集，再在旧包里做整文件字节搜索。没有 3.20.7–3.21.5。

## 新路径

| 方法 | 路径 | 鉴权 | 含义 | 实打 |
|---|---|---|---|---|
| GET | `/bapi/equity/v1/public/equity/option/get-symbols-index` | public | 美股期权标的索引 | 200 `000000`。样例 `SPY`/`EQ_SPY`、`QQQ`/`EQ_QQQ`，后面还有约 1042 个 |
| GET | `/bapi/equity/v1/public/equity/option/get-symbols-by-param` | public | 按标的拉合约 | 200 `000000`，`data` 是空数组。试过 `assetCode=EQ_NVDA`、`assetCode=EQ_SPY`、`underlyingSymbol=SPY`，都是空的。索引有数据，这条是缺参数 |
| GET | `/bapi/equity/v1/private/equity/order/oto/place` | 要登录 | 期权 OTO 下单 | 401 `100001005 Please log in first.` |
| GET | `/bapi/equity/v1/private/equity/order/otoco/place` | 要登录 | 期权 OTOCO 下单 | 未单独打。和上一条一样是 private place，不编返回体 |
| GET | `/bapi/asset/v1/private/asset-service/funding-migrate/config` | 要登录 | 资金账户迁移配置 | 401 `100001005` |
| GET | `/bapi/asset/v1/private/asset-service/funding-migrate/migrate-to-spot` | 要登录 | 迁到现货 | 未打。写操作，只记路径 |
| GET | `/bapi/c2c/v1/private/c2c/funding-migration/can-migrate` | 要登录 | C2C 侧能否迁移 | 未打 |
| GET | `/bapi/defi/v1/public/wallet-direct/buw/wallet/market/token/pulse/rank/home/card` | public | Meme 脉冲榜卡片 | 200 `000000`。`tokenList` 加 `migratedCount`、`risingCount`（当次 2552 / 68） |
| GET | `/bapi/defi/v1/public/wallet-direct/buw/wallet/ai-widget/hot-zone/config` | public | 钱包 AI 热区问题 | 200 `000000`。样例 `What is Tokenized Securities?`，后面还有约 210 条 |
| GET | `/bapi/defi/v1/public/wallet-direct/buw/wallet/ai-widget/query` | public | AI 组件查询 | 400 `000002 illegal parameter` |
| GET | `/bapi/defi/v1/public/wallet-direct/prediction/mp/widget` | public | 预测小程序组件 | 400 `000002` |
| GET | `/bapi/apex/v1/friendly/apex/discover/trading/ranking-list` | public | 发现页排行 | 200 `000000`。`rankingList` 里有 `subjectType`（`COPY_TRADING` / `SMART_MONEY` / `TRADING_BOT`）、`productLine`、`pnl`、`roi`、`deeplink` |
| GET | `/bapi/fiat/v2/public/fiatpayment/transactions/asset/get-asset-list` | public | 法币资产列表 v2 | 200 `000000`。`assets` 约 1517 条，字段含 `assetCode`、`alphaId`、`precision` |
| GET | `/bapi/margin/v2/public/margin/get-wss-url` | public | 杠杆行情地址 | 200 `000000`，`data` 为 `wss://fstream.binance.com/private/ws` |
| GET | `/bapi/apex/v1/friendly/apex/app/markets/tabs` | public | 旧行情底栏，复打 | 200 `000000`，`defaultTab=fav` |

`/bapi/fe/chimera/news-flash/friendly/v1/flash/detail` 用 GET 会 `000405 method not allowed, use POST`。没有改成 POST。  
`/bapi/fe/chimera/admin/a2ui/get` 在客户端里。未登录 GET 返回 code `13`，网关要的不是这份 JSON。没有继续试。

## 全量新 /bapi/

下面每条都在旧包字节搜索里确认过，3.18.4 到 3.20.6 都没有。private 未登录按 `100001005` 理解。写操作只记路径，没有提交。

行情和 B9：

- `/bapi/apex/v1/friendly/apex/discover/trading/ranking-list`
- `/bapi/apex/v1/private/apex/b9/asset-analysis/holding-performance`
- `/bapi/apex/v1/private/apex/b9/daily-report/detail-v4`
- `/bapi/apex/v1/private/apex/b9/daily-report/display-v4`
- `/bapi/apex/v1/private/apex/b9/daily-report/history-v4`
- `/bapi/apex/v1/private/apex/b9/watch-market/l2-report-widget`
- `/bapi/apex/v1/private/apex/b9/widget/favouritemore/kline`
- `/bapi/apex/v1/private/apex/homepage/vip-upgrade-popup/report`
- `/bapi/apex/v1/private/apex/user/current/profile/voucher-widget`
- `/bapi/apex/v2/private/apex/b9/homepage/watch-market`
- `/bapi/apex/v2/private/apex/b9/watch-market/groups`
- `/bapi/apex/v2/private/apex/b9/widget/favouritemore`
- `/bapi/apex/v2/private/apex/b9/widget/favouritemore/list`
- `/bapi/fe/mimir/v1/private/get-b9-report-preview`
- `/bapi/fe/mimir/v1/private/list-hp-6in1-resource-banners`
- `/bapi/fe/mimir/v3/private/get-b9-asset-report`
- `/bapi/composite/v1/private/bigdata/finance/spot-pnl/pnl`

美股期权和资金迁移：

- `/bapi/equity/v1/public/equity/option/get-symbols-index`
- `/bapi/equity/v1/public/equity/option/get-symbols-by-param`
- `/bapi/equity/v1/private/equity/order/oto/place`
- `/bapi/equity/v1/private/equity/order/otoco/place`
- `/bapi/asset/v1/private/asset-service/funding-migrate/config`
- `/bapi/asset/v1/private/asset-service/funding-migrate/migrate-to-spot`
- `/bapi/c2c/v1/private/c2c/funding-migration/can-migrate`

钱包、Meme、预测、Earn：

- `/bapi/defi/v1/public/wallet-direct/buw/wallet/ai-widget/hot-zone/config`
- `/bapi/defi/v1/public/wallet-direct/buw/wallet/ai-widget/query`
- `/bapi/defi/v1/public/wallet-direct/buw/wallet/dex/market/token/ext/info`
- `/bapi/defi/v1/public/wallet-direct/buw/wallet/market/token/pulse/rank/home/card`
- `/bapi/defi/v1/public/wallet-direct/buw/wallet/token/token/address/gas-fee`
- `/bapi/defi/v1/public/wallet-direct/prediction/mp/widget`
- `/bapi/defi/v3/public/wallet-direct/buw/wallet/market/token/search/suggestion`
- `/bapi/defi/v1/private/wallet-direct/buw/alpha-event/competition/query`
- `/bapi/defi/v1/private/wallet-direct/mgmt/user/wallet/identity/type`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/card/banner/list`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/card/pool/list`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/card/token/list`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/pool/detail`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/pool/statistics`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/recommended/list/for/w3w`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/token/info`
- `/bapi/defi/v2/private/wallet-direct/tx-history-pending-simple`
- `/bapi/defi/v2/private/wallet-earn/simple/yield/card/loan/list`
- `/bapi/defi/v4/private/wallet-earn/simple/yield/protocol/list`

法币、合约网格、杠杆、支付、增长：

- `/bapi/fiat/v2/public/fiatpayment/transactions/asset/get-asset-list`
- `/bapi/fiat/v2/private/fiatpayment/transactions/asset/get-asset-tags`
- `/bapi/fiat/v2/private/fiatpayment/transactions/bs/unify/get-from-asset-list`
- `/bapi/fiat/v2/private/fiatpayment/transactions/bs/unify/get-from-asset-list?forceBusinessType=FX`
- `/bapi/fiat/v2/private/fiatpayment/transactions/bs/unify/get-to-asset-list?fromAssetId=`
- `/bapi/futures/v1/friendly/future/spot-copy-trade/common/recommend-lead-item`
- `/bapi/futures/v1/private/future/grid/algo-order`
- `/bapi/futures/v1/private/future/grid/cancel-algoOrder`
- `/bapi/futures/v1/private/future/grid/open-algo-order`
- `/bapi/futures/v1/private/delivery/grid/algo-order`
- `/bapi/futures/v1/private/delivery/grid/cancel-algoOrder`
- `/bapi/futures/v1/private/delivery/grid/open-algo-order`
- `/bapi/futures/v1/private/future/user-setting/batch-update-saved-preferences`
- `/bapi/margin/v1/private/isolated-margin/trade/user-symbol-cost`
- `/bapi/margin/v2/private/margin/listen-key`
- `/bapi/margin/v2/public/margin/get-wss-url`
- `/bapi/pay/v1/friendly/binance-pay/layout/quick-entries`
- `/bapi/growth/v1/private/growth/insight/recommend`
- `/bapi/growth/v2/private/usertask/distribution-platform/popup/playbook`
- `/bapi/fe/chimera/news-flash/friendly/v1/flash/detail`
- `/bapi/fe/chimera/admin/a2ui/get`

包外链接里新出现的是 `https://massive.com`、`https://www.dtcc.com/support/dtc-directories`，以及三篇 Web3 钱包 FAQ / 博客。域名差集写在 [surface.md](surface.md)。

## 客户端换掉的旧路径

这些路径在 3.21.6 的字符串里没有，在 3.20.5 里有。归因时抽查过的，3.20.6 里也没有。

- B9 v3 / v1：`daily-report/detail-v3`、`history-v3`、`daily-report/display`、`homepage/watch-market`、`watch-market/tabs/secondary`、`widget/favouritemore`、`favouritemore/list`、`movers-highlight`、`movers-list`、`android-version`
- 资产报告：`/bapi/fe/mimir/v2/private/get-b9-asset-report`，现货盈亏旧路径 `/bapi/composite/v1/private/report/exchange-analytics/spot-pnl/pnl`
- 划转钱包：`setUserTransferWallet`、`userTransferWallet`
- Earn 协议：`service-agreement`、`service-agreement/sign`，以及 v2 的 `multiple/list`、`multiple/sign`
- P2P 借贷历史：borrower / lender 的 `adjustment-history`、`liquidation-history`、`loan-history`、`repayment-history`
- 法币 v1：`get-asset-list`、`get-asset-tags`、`get-from-asset-list`、`isFxOnly=true`、`fromAsset=`
- 跟单推荐：`home-page/recommend-lead-list`、`home-page-recommended-lead-list`
- 杠杆抵押和逐仓借贷历史：`collateral/liquidation/query-force-liquidation-retail`、`query-adjustment-collateral-retail`、`collateral/repay/query`、`collateral/order/query`，以及 `flexibleLoan/isolated` 新旧两套 `adjustmentHistory` / `liquidationHistory` / `loanHistory` / `repaymentHistory` / `subscriptionHistory`

## 深链

这轮字节搜索确认是新的：

| 链接 | 含义 |
|---|---|
| `bnc://app.binance.com/markets/marketsDetail?at=equity&assetCode=EQ_NVDA&selectTab=options` | 英伟达行情页直接开期权 tab |
| `bnc://app.binance.com/markets/markets?at=prediction&mpModalType=replace` | 行情切到预测 |
| `bnc://app.binance.com/ai/landing?source=market_asset_analysis&category=` | 资产分析进 AI |
| `bnc://app.binance.com/p2p/addContact?scenario=1&source=Homepage` | 首页加联系人 |
| `bnc://strategy` / `bnc://strategy/detail?id=334` | 策略详情，id 写死 334 |
| `bnc://profile` | 个人页短链 |

小程序路径（`startPagePath` 解开）：`pages/order/index`（`orderType=lender`）、`pages/alpha-airdrop/index`（query 是占位 `foo=bar`）、`pages/alpha-point/index`、`pages/home/index`、`pages/mp/add-feedback/index`、`pages/messages/v2/group/$groupId/index`。appId 整段 URL 是新的，不代表每个 appId 都是这版才有的小程序。
