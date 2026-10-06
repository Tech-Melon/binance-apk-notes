# 3.21.6 参数和字段

键名在 3.21.6、3.20.6、3.20.5、完整 3.19.8 上做了整包字节搜索（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
「新」= 只在 3.21.6。没有 3.20.7–3.21.5。  
这是安装包里的字符串键，不是反编译出来的每个类字段，也不是服务端开关的当前值。

## 确认新增的产品字段

| 键 | 像什么 |
|---|---|
| `tradFiPreferOptionsTab` | TradFi 切标的时落到期权 tab |
| `optionPositionAmount` | 期权持仓数量 |
| `copyTradingButton` | 跟单按钮开关或文案位 |
| `merchantSinceTime` | 商户入驻时间，给高级筛选用 |

`collateralAsset` 在 3.19.8 起就有。差集里那串 `, collateralAsset=` 是拼接文本变了，键本身不是新的。

## 确认新增的开关

| 键 | 像什么 |
|---|---|
| `androidSquareImDeferEnabled` | Square 即时通讯延迟加载 |
| `androidSquareUserDeferEnabled` | Square 用户数据延迟加载 |
| `Android_square_enable_prefetch_detail` | Square 详情预取 |
| `liveImTokenCacheEnabled` | 直播 IM token 缓存 |
| `liveBatch` | 直播批量字段，上下文是日志键 |

包里只有键名。开没开要看远程配置，这里看不出来。

## 查询参数

| 参数 | 用在哪 | 对照 |
|---|---|---|
| `forceBusinessType=FX` | 法币 v2 `get-from-asset-list` | v1 用的是 `isFxOnly=true`。`isFxOnly` 这个词还在包里 |
| `fromAssetId=` | 法币 v2 `get-to-asset-list` | v1 是 `fromAsset=` |
| `selectTab=options` | 行情深链 | 只在 3.21.6 |
| `assetCode=EQ_NVDA` | 同上 | 和 `at=equity` 一起打开期权 tab |
| `at=prediction` | `bnc://.../markets/markets` | 行情切到预测 |
| `mpModalType=replace` | 同一条行情深链 | 小程序弹层替换当前页 |
| `source=market_asset_analysis` | `bnc://.../ai/landing` | `category=` 在这条链接里是空的 |
| `scenario=1` / `source=Homepage` | `bnc://.../p2p/addContact` | 首页加联系人 |
| `id=334` | `bnc://strategy/detail` | 策略 id 写死在客户端 |
| `ongoingType=request&orderType=lender` | 小程序 `pages/order/index` | `startPageQuery` 解开 |
| `foo=bar` | `pages/alpha-airdrop/index` | 占位 query，不是活动参数 |
| `groupId=d4e9eh371n0v8eo3r4a0` | `pages/messages/v2/group/$groupId/index` | 示例群 id |

## 调试字段，不要当成用户参数

这些键只在 3.21.6，前缀是 `mock`，用来填跟单余额：

`mockCopyOverallBalance`、`mockFutCopyBalance`、`mockSpotCopyBalance`，以及同一串里的 `mockCopyBalanceAsset`、`mockFutCopyUnrealizedPnl`、`mockSpotCopyUnrealizedPnl`、`mockFutOngoingCopyPortfolioCount`、`mockSpotOngoingCopyPortfolioCount`。

## 旧键，签名变了才看起来像新的

`collateralAsset`、`isFxOnly`、`EarnMainV6` 相关类名、`WalletEntranceFragment`、`ContactsViewModel`、`UsOptionChainQuoteWsPO`。  
R8 把旧类重新拼进签名串，字符串差集会把整段签名当成新句子。键和类名要再搜一遍裸名字。
