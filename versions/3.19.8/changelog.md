# 3.19.8 相对 3.19.5

对照用完整包 `BNApp64_V3.19.8.apk`。Play base `币安 3.19.8.apk` 只作包装旁证。

## 产品

1. **美股期权交易进客户端**  
   新包 `com.finance.tradfi.us.options.*`，路由 `UsOptionsRouterService`。  
   覆盖：期权链（Call/Put/All）、报价列设置 `UsOptionsColumnSettingActivity`、下单/预览、仓位、提前行权、到期自动平仓、CC / CSP。  
   深链：`bnc://app.binance.com/usOptions/trade?os=`、`.../usOptions/options-position-details?assetCode=`、`/usOptions/eventDetail`。  
   3.19.5 及更早就有 `Options (Coming soon)` / `您已签署协议，现在可以交易 TradFi 期权了`，**交易页和期权链接口是这版才进包**。包内不用 slogan `美股期权`。
2. **期权行情权限**  
   默认延迟 15 分钟；持仓或本月做过一笔期权可「开启实时报价」。对应 `UsOptionsQuoteDelayDialog` / `option/rt/enable`。
3. **期权规费拆条**  
   ORF、OCC、FINRA TAF、FINRA CAT、SEC 交易手续费。按合约张数或成交金额计、费率会变、**BNB 折扣暂不适用**。
4. **个股研究卡**  
   `Daily insights` / `每日洞察`、`宏观分析`、`技术分析`、`市场情绪与风险`、`关键动因`、`核心结论`。挂在行情侧，不是独立 Activity。
5. **远程小程序 quiz 深链**  
   已有 appId `q7xVG7ra5ocEDmTGEQo9uX`（3.18.4 就有），这版新 query：`pages/index/index` + `url=/stocks/quiz`（包内是双重 base64，明文 `/stocks/quiz` 不出现）。

## 加强 / 改版

- 美股订单详情从 `com.finance.tradfi.feature.history...TradFiOrderDetailActivity` 挪到 `com.finance.tradfi.us.stock.feature.history...`。同页换包，不是新功能。
- 订单/成交历史走 equity **v2**：`/order/history`、`/order/open-orders`、`/trade/history`。要登录。
- 旧 stock 行情中心注释写明废弃，改 `getStockCoinDataCenter2()`。
- 网格策略公开参数 `grid/coef`（`maxGridCount=500` 等）。对应「价差过小。运行该机器人的最大网格数量为%1$s。」
- Discover 推荐列表 `trading/recommend-list`（smart money / top traders / trading bot 布局）。
- 钱包侧新句：投资表现摘要、昨日盈亏公式（「昨日盈亏」四字旧包就有，公式是新的）。

## 基础设施

- 小程序运行时 5.15 线：5.16.1 → **5.16.2**。内置三个 MP id 不变，jwt 各 +12 字节。
- Flutter 仍 14 个 package，没新模块。
- so：73 → 74。哈希名轮换 `liba68ac1` / `libeea0` → `libaa71` / `libc6a665`。具名新增 **`librheatrace.so`**（Rhea 性能追踪）。其余 66 个 CRC 变了，当重建，不当重写。
- `resources.arsc` 84.9 MB → 85.4 MB。
- DEX 仍 27。Play base 那份只有 23 个、0 个 so，不要拿来比 native。
