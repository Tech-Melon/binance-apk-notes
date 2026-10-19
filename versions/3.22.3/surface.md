# 3.22.3 页面和客户端表面

Manifest 的 Activity 对过 3.21.6、3.20.6、3.20.5。类名再搜裸名字。  
R8 签名里出现旧类，不算新页面。这一版 **没有** 新增 Activity。

## Manifest 新增的 Activity

没有。

## 裸类名确认是新的

这些不在 3.21.6、3.20.6、3.20.5、完整 3.19.8 里：

| 类名 | 做什么 |
|---|---|
| `EquityWelcomeIntroStock` | 美股正股欢迎 / 介绍 |
| `EquityWelcomeIntroStockOption` | 美股期权欢迎 / 介绍 |
| `EditCCIFragment` | 图表 CCI 设置。旁边有新句子 `Commodity Channel Index` |
| `EditVWAPFragment` | 图表 VWAP 设置。单词 `VWAP` 是旧的，全称 `Volume Weighted Average Price` 是新的 |
| `AlphaCryptoUnavailableDialog` | Alpha 代币不可用弹窗 |

## Manifest 去掉的 Activity

3.21.6、3.20.6、3.20.5、完整 3.19.8 都有，3.22.3 的 Manifest 和整包字节里都没有：

- `com.binance.ocbs.activity.BuyWithBankTransferDetailActivity`
- `com.binance.paymentsdk.cardmanagement.FiatManageCardForSellActivity`
- `com.finance.voptions.feature.market.VOptionsPreferenceActivity`

`VOptionsOrderConfirmDialog` 还在。去掉的是偏好页，不是期权确认单。

3.20.5 就有、3.21.6 已经没有的法币店铺、现金交易地点、双币 V2、借款页、`AutocompleteActivity`，不是这版新删的。

## 域名和依赖

| 字符串 | 旧 | 新 |
|---|---|---|
| `https://www.binance.com/en/stocks/options/` | 无 | 有 |
| `app.withpersona.us` / `inquiry-fallback.withpersona.us` / `tg.withpersona.us` / `webrtc-consumer.withpersona.us` | 无 | 有。地址核验供应商 |
| `https://app.binance.com/uni-qr/report-landing` | 无 | 有 |
| `qa1fdg.net` | 有 | 有。新的是上面的 `quick-login?email=` 整段 |
| `lib/arm64-v8a` | 0 | 0。完整包 3.20.6 有 76 个 so，那是包装 |
| 小程序运行时 | 5.16.4 | 5.16.4 |
| Flutter package | 15 | 15。skylinef 多了 5 个字体文件 |

新文件里和产品有关的是 `com/bigdata/StrategyAgentEventMsg.proto`。`assets/jarvis_landing_share_capture.js` 给落地页小程序做截图。`assets/PublicSuffixDatabase.list` 换成 OkHttp 公共后缀表。

## 这轮没有单独立项的

- so：两边都没有 `lib/arm64-v8a`。相对 3.20.6 的 76 个 so 是包装
- `res/raw/` 哈希轮换（相对 3.21.6 大约 675 增、664 删）
- 服务端开关的当前值
- R8 签名里的 `CopyTradingCreateChatRoomDialog`、`TradFiStatsInfoDialog`、`ChatSessionListActivity`、`NezhaSheetTransparentActivity`。裸名字旧包就有
