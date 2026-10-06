# 3.20.1 页面和客户端表面

Manifest 的 Activity 对照的是 Play base `币安 3.19.8.apk`。类名再在完整 3.19.8，以及 3.20.3 / 3.20.5 / 3.20.6 里搜裸名字。  
R8 签名里出现旧类，不算新页面。

## Manifest 新增的 Activity

| 类 | 做什么 |
|---|---|
| `com.binance.c2c.chat_new.contact.home.messagerequests.MessageRequestsListActivity` | 消息请求列表 |
| `com.binance.c2c.chat_new.groupchat.profile.privacy.messagerequests.MessageRequestsSettingsActivity` | 谁可以发私信。空态是 `No message requests` |
| `com.binance.content.internal.live.ContentCommonFlutterActivity` | 内容 Live 的 Flutter 引擎预热 |

## 裸类名确认是新的

这些不在完整 3.19.8 里，从 3.20.1 起有：

| 类名 | 做什么 |
|---|---|
| `SettledMarketListDataBlock` | 预测市场已结算列表 |
| `MarketTopicDataBlock` | 预测市场话题块 |

`UpDownTradeFragment`、`SettledTimelineSheet` 在 3.19.8 就有，不是这版新类。

Flutter 包 `module_square` 从这版进 `assets/flutter_assets/packages/`。完整 3.19.8 没有这个 package。

## Manifest 去掉的 Activity

完整 3.19.8 有，从 3.20.1 起类名也搜不到：

- `AVGCostEditActivity`、`PnlModifyAveragePriceActivity`：成本价改走对话框和 `avgCost`
- `DeliveryPreferenceActivity`：交割偏好页
- `RecommendGroupChatsActivity`
- `FiatOrderDetailSellHelpActivity`

`FuturePreferenceActivity` 不在这一版 Manifest 里，类名在 dex 里还在。不当成类被删掉。androidx 测试 Activity 的差集不记。

## 域名和依赖

补记没有重跑域名差集。Onfido bridge 1.2、picnic 低 MC 参数仍以 [changelog.md](changelog.md) 为准。

## 这轮没有单独立项的

- so：这份是 Play base，没有 `lib/`
- `res/raw/` 哈希轮换
- 服务端开关的当前值
