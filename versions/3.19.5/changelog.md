# 3.19.5 相对 3.18.4

## 产品

1. **美股真券开卖**  
   slogan `US Stocks, Now on Binance!` / `美股现已上线币安！`。托管写 Alpaca + SIPC，支持加密货币买 7000+、自动股息、FPSL 出借、DTC 转仓。  
   `StockCoinDetail` 从 Fragment 升为独立 Activity。远程小程序 `zkvttk2chaoaJvkPumxLxY`，`biz=us_stock`。
2. **真股 ↔ bStocks**  
   「把股票代币化」介绍弹窗、适当性评估后可作杠杆抵押（`quizType=BSTOCK_COLLATERAL`）。
3. **预测市场进广场**  
   发帖出现 `Add prediction market`；开关 `enablePredictionMarket` / `FEATURE_TYPE_PREDICTION_MARKET`。底层 3.18.4 已有，这版产品化。
4. **合约跟单自管**  
   `enter-self-managing`。文案：Lead Trader 同步停止，仓位转自己管。
5. **逐仓条件平仓**  
   `com.binance.margin.conditionalclose.*`，3.18.4 零命中。
6. **钱包资产展示设置**  
   `AssetDisplaySettingsActivity`（隐藏小额、快捷操作行）。资产列表 Dynamic 化。
7. **C2C 群聊可发现性**  
   `DiscoverabilitySettingsActivity`，路由 `/chat/discoverabilitySetting`。

## 加强 / 改版

- 广场直播：live setting 图、`EnableLivePrewarm`、`enableFlvMode`、`classes27.dex` 为 WebRTC
- PayPay：登录流 3.18.4 已有，这版补日/印尼法务 URL
- Earn 搜索页 `EarnHomeSearchActivity` 整包消失
- 营销开关 `getUserAppFeatures` v2 → v3
- Buzz：新深链 `pages/buzz-unavailable/index?type=ugc`（区域下线，不是新开）

## 基础设施

- 小程序运行时 5.15.0 → 5.16.1
- `libapmanr.so` = ANR SIGQUIT 探针
- 哈希名 so 轮换：`libd390/libd50b81` → `liba68ac1/libeea0`
