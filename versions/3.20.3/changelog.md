# 3.20.3 相对 3.20.1

对照用 Play base：`币安 3.20.1.apk` → `币安 3.20.3.apk`。  
「这句是新的」额外在 3.18.4 / 3.19.5 / 完整 3.19.8 上整包对过。  
**没有 BNApp64 3.20.3**，不拿缺 so / 缺中文当产品下线。

## 产品

1. **美股定投 Recurring Buy**  
   新句：`Stock recurring buy is now available. Tap to set one up.`  
   `Automate your investments with scheduled recurring buys.`  
   周期：Daily / Weekly / Biweekly / Monthly / One-Time；最多 10 只；每期约美东 10:30。  
   One-Time 限美股开盘。资金顺序：Funding → Spot → Simple Earn Flexible。  
   新 ViewModel：`UsRecurringPlaceOrderViewModel` / `UsRecurringTradeViewModel`。  
   公开接口 `get-symbols-index` 回 100 个 `EQ_*`（样例 MU / NVDA / AAPL / META / TSLA）。计划 CRUD 要登录。
2. **行情 For You / B9 + AGenUI**  
   内部代号 B9，feature gate 写成 `For You(B9)`。  
   动态卡片走 AGenUI（`assets/agenui/`，schema 写着 `amap.com/agenui`）。  
   组件：Today's Hotspot、Market Brief、Key Notes、Movers Flash、每日复盘 / 波动归因 / 涨幅领先 / 盯 ETF、ETF / 加密 / 美股 widget、screener、top trader、资金流。  
   深链 `bnc://app.binance.com/ai/landing?source=…`（crypto tracker / ETF tracker / stock board / market pulse / top trader）。  
   **Play base 没有 so**：包内有 `AGenUI disabled: SO load failed`、`不含 arm64-v8a`。这包上 native 引擎可能要等 Play split。
3. **Jarvis 透明浮层 + 语音**  
   新 Activity：`JarvisBizWidgetTransparentActivity`。  
   TTS 列表从 `tts/demovoice` + `tts/list_voice` 换成 `jarvis/v2/user/voice-names`。  
   新句：`Connecting to voice service…`、`Select the speech recognition model`、`ASR Model`、`Play voice` / `Pause voice`。  
   `A2UI` 三个字 3.20.1 就有，这版新的是透明 Activity 和 voice-names。
4. **行情简报播放（`music` 模块）**  
   新 Activity：`MusicLandingActivity`；深链 `bnc://app.binance.com/music/landingPage`。  
   dex 里有 `MusicBriefingViewModel` / `MusicHistoryViewModel`。  
   行情头 Bibi 播放/暂停 Lottie（classic / light）。  
   **没有** `Binance Music` / `Music Briefing` 整句，不当独立音乐 App。
5. **小程序钱包 Provider 选择**  
   新 Activity：`WalletProviderSheetActivity`。  
   `appId is not allowed to use wallet provider`、`no available wallet`、`failed to open wallet`。  
   给 MP 调起钱包用，不是新的中心化钱包产品。

## 加强 / 改版

- 公开 `markets/tabs`：未登录默认 `fav`，其余 `market` / `tradfi` / `alpha` / `content` / `data`。For You 不在这份公开表里，走 feature flag。
- B9 screener 公开 widget 带回远程 MP `kg39guhd4MzvBvsgyEcmjU`（Easy Screener / Quant / 实盘 master，样例 John Paulson Holdings）。**appId 不在 APK 硬编码里**，是接口下发。
- 内置三个 MP 的 jwt 刷新了，页面 id 没变。
- Jarvis 点赞/点踩多了 dark Lottie。
- `IndexPriceChangeMsg.proto` 进包（BDP 指数价变动）。

## 基础设施

- 小程序运行时 5.16.3 → **5.16.4**。三个内置 MP id 不变。
- Flutter 仍 15，无新 package。
- DEX 仍 24，全量 CRC 变。未压缩 DEX 226.6 MB → 233.7 MB。
- Play base 没有 so，**不要拿来比 native**。AGenUI 明确依赖 arm64 so。
- `resources.arsc` 7.27 MB → 7.39 MB（仍是瘦表）。
- `res/raw/` 哈希名大量轮换（+2524 / -2268），当资源重建。
- 权限相对 3.20.1 Play base **无增减**。
