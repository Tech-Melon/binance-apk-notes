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

同一批差集里还有、这轮没有逐条打的 private 路径：B9 日报 `detail-v4` / `history-v4` / `display-v4`，自选 `apex/v2/.../watch-market`，mimir `get-b9-asset-report` v3，钱包收益卡 `yield/card/*`，Alpha `competition/query`，合约网格 `grid/algo-order`。未登录按 `100001005` 理解，不编返回体。

`/bapi/fe/chimera/news-flash/friendly/v1/flash/detail` 用 GET 会 `000405 method not allowed, use POST`。没有改成 POST。

## 客户端换掉的旧路径

这些字符串在 3.20.5 和 3.20.6 里都有，3.21.6 没有：

- B9：`daily-report/detail-v3`、`history-v3`、v1 `homepage/watch-market`、mimir `get-b9-asset-report` v2
- 法币：`/bapi/fiat/v1/.../get-asset-list` 以及 v1 的 asset-tags / from-asset-list
- 跟单推荐：`home-page/recommend-lead-list`、`home-page-recommended-lead-list`，换成 `recommend-lead-item`（GET 无参是 `000002`）

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
