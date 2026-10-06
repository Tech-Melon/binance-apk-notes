# 3.20.3 页面和客户端表面

Manifest 的 Activity 对照的是 Play base `币安 3.20.1.apk`。类名再在完整 3.19.8、3.20.1，以及之后的 3.20.5 / 3.20.6 里搜裸名字。  
R8 签名里出现旧类，不算新页面。

## Manifest 新增的 Activity

| 类 | 做什么 |
|---|---|
| `com.binance.chat.ui.bizwidget.JarvisBizWidgetTransparentActivity` | Jarvis 透明浮层。音色列表换成 `jarvis/v2/user/voice-names` |
| `com.binance.music.internal.ui.landing.MusicLandingActivity` | 行情简报播放落地。深链 `bnc://app.binance.com/music/landingPage` |
| `com.buw.mpp.pluginv2.handler.sheet.WalletProviderSheetActivity` | 小程序选钱包 Provider。不是新的中心化钱包 |

没有去掉的 Activity。

## 裸类名确认是新的

这些不在 3.19.8、3.20.1 里，从 3.20.3 起有：

| 类名 | 做什么 |
|---|---|
| `UsRecurringPlaceOrderViewModel` | 美股定投下单 |
| `UsRecurringTradeViewModel` | 美股定投交易 |
| `MusicBriefingViewModel` | 简报播放 |
| `MusicHistoryViewModel` | 简报历史 |

`Binance Music` 整句仍然没有。不当独立音乐 App。

## Manifest 去掉的 Activity

没有。

## 域名和依赖

动态卡片 schema 写着 `amap.com/agenui`，资源在 `assets/agenui/`。这是 AGenUI，不是新的对外域名产品。

## 这轮没有单独立项的

- so：这份是 Play base，没有 `lib/`。包内有 `AGenUI disabled: SO load failed`、`不含 arm64-v8a`。native 引擎不在这只 base 里，不当产品下线
- `res/raw/` 哈希轮换
- 服务端开关的当前值：包里看得到 `For You(B9)` 这串字，看不到它开没开
