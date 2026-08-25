# 3.19.8 相对 3.19.5

## 产品

1. **美股期权交易进客户端**  
   新包 `com.finance.tradfi.us.options.*`，路由 `UsOptionsRouterService`。  
   覆盖：期权链（Call/Put/All）、报价列设置 `UsOptionsColumnSettingActivity`、下单/预览、仓位、提前行权、到期自动平仓、Covered Call / Cash-Secured Put。  
   深链：`bnc://app.binance.com/usOptions/trade?os=`、`.../usOptions/options-position-details?assetCode=`、`/usOptions/eventDetail`。  
   3.19.5 及更早就有 `Options (Coming soon)` / 「已签署可交易 TradFi 期权」类句子，**交易页和期权链接口是这版才进包**。
2. **期权行情权限**  
   默认 15 分钟延时；满足「持仓或本月做过期权」等条件可 `Turn on Real-time Quotes`。对应 `UsOptionsQuoteDelayDialog` / `option/rt/enable`。
3. **期权规费拆条**  
   ORF、OCC、FINRA TAF、FINRA CAT、SEC Transaction Fee，文案写明按合约张数或成交金额计、费率会变、**BNB 折扣暂不适用**。
4. **个股研究卡**  
   新句：`Daily insights`、`Macro Analysis`、`Technical Analysis`、`Market Sentiment and Risks`、`Key Drivers` / `Sector Drivers`、`Core Conclusion`。挂在行情侧，不是独立 Activity。
5. **远程小程序 quiz 深链**  
   已有 appId `q7xVG7ra5ocEDmTGEQo9uX`（3.18.4 就有），这版新 query：`pages/index/index` + `url=/stocks/quiz`（包内是双重 base64，明文 `/stocks/quiz` 不出现）。

## 加强 / 改版

- 美股订单详情从 `com.finance.tradfi.feature.history...TradFiOrderDetailActivity` 挪到 `com.finance.tradfi.us.stock.feature.history...`。同页换包，不是新功能。
- 订单/成交历史走 equity **v2**：`/order/history`、`/order/open-orders`、`/trade/history`。要登录。
- 旧 stock 行情中心注释写明废弃，改 `getStockCoinDataCenter2()`。
- 网格策略公开参数 `grid/coef`（`maxGridCount=500` 等）。对应新句 `Price difference is too small. Max number of grids...`。
- Discover 推荐列表 `trading/recommend-list`（smart money / top traders / trading bot 布局）。
- 钱包侧新句：`Investment Performance Summary`、昨日 PnL 公式、总资产相对前一日变动。
- 权限去掉 `REQUEST_INSTALL_PACKAGES`（不能再在应用内拉安装包）。字符串还在 DEX 里，Manifest 已无此权限。

## 基础设施

- 小程序运行时 5.16.1 → **5.16.2**。内置三个 MP id 不变，jwt 各 +12 字节。
- Flutter 仍 14 个 package，没新模块。
- 这份 APK **0 个 so**；3.19.5 有 73 个 arm64 so。对比 so 哈希没有意义，缺的是拆分包。
- `resources.arsc` 84.9 MB → 7.5 MB。中文资源不在这份 base 里。
- `stamp-cert-sha256`、`feature-delivery.properties` 出现，旁证来自 Play App Bundle。
- DEX 27 → 23。旧 `classes27.dex` 是 WebRTC，不写「这版删了 WebRTC」——native 和多余 DEX 可能在别的 split。
