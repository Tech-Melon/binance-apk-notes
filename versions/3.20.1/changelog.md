# 3.20.1 相对 3.19.8

对照用 Play base：`币安 3.19.8.apk` → `币安 3.20.1.apk`。  
「这句是新的」额外在 3.18.4 / 3.19.5 / 完整 3.19.8 上整包对过。  
**没有 BNApp64 3.20.1**，不拿缺 so / 缺中文当产品下线。

## 产品

1. **美股 Auto Order Routing（AOR）**  
   新句：`Auto Order Routing` / `Auto Order Routing (AOR)` / `Auto Order Routing Terms`。  
   限价单可被路由到中间订单簿（文案里的 Intermediary Order Book）去找价格改善；1s K 线对 AOR 标的不支持。  
   对应公开接口 `get-quote-v2`（买卖报价资产 + 闪兑资产列表，不是行情价）。
2. **钱包成本价 / 均价改版**  
   新设置：`Cost Price Settings`、`New Average Price` / `New Cost Price`。  
   均价 = 累计买入成本（卖出不影响、不自动重置）；成本价 = 移动加权，卖出影响、平仓重置。  
   Manifest 去掉 `AVGCostEditActivity` / `PnlModifyAveragePriceActivity`，改走对话框 + `/bapi/apex/v4/private/apex/pnl/overview/avgCost`（要登录）。
3. **聊天消息请求**  
   新 Activity：`MessageRequestsListActivity`、`MessageRequestsSettingsActivity`。  
   空态 `No message requests`；`You have pending message requests.`  
   可设「关注你 Square 的人才能私信」。
4. **Flutter Square 模块首次进包**  
   `assets/flutter_assets/packages/module_square/`。3.19.8 完整包也没有这个 package。  
   另有 `ContentCommonFlutterActivity`（内容 Live 的 Flutter 引擎预热，dex 里一堆引擎槽位调试句）。
5. **个股公司行动 / 研究卡加厚**  
   `Dividend History` / `Dividends Summary` / `Cash Dividend: %1$s %2$s Per Share`。  
   `Stock Splits History` / `Reverse Stock Split`。  
   `Company Overview` / `Finance Estimates` / `Financials Report` / `Insider Activity` / `Insider Trading Trends`。  
   短词 `Stock Dividend` / `Cash Dividend` **旧包就有**，这版新的是完整标签和页面句。
6. **网格密度**  
   `Grid Density` + 公式：`Grid Count ÷ ((Upper Price - Lower Price) / Lower Price × 100)`。  
   按每 1% 价格区间的网格数给「太稀 / 适中 / 太密」提示。
7. **跟单**  
   `Follow Top Traders' Live Signals`、`Filter lead traders currently holding TradFi symbols.`  
   现货跟单标的表 `spot-copy-trade/common/support-symbol-details`（公开，约 374 个，带 `bstock` 字段）。
8. **Earn 免存试用**  
   `No deposit needed! Try Simple Earn for free — rewards are yours.`  
   `Earn <b>%1$s</b> APR Free — No Catch`、`Free Trial Fund, no tasks, no deposit.`
9. **Agentic / Hot Wallet**  
   `Create Agentic Wallet`、`Keyless wallet dedicated for your AI Agent`、`Binance Hot Wallet`。  
   包内有文案和入口句，**没有**对应公开接口可打。
10. **Trade Hub**  
    `Trade Hub Now Available`。偏好页 `DeliveryPreferenceActivity` / `FuturePreferenceActivity` 从 Manifest 消失，像是收进交易中枢，不是功能蒸发。
11. **远程小程序 quiz**  
    已有 appId `znf9fpiMh6ufdU3vDtAvi4`，这版新 query：`startPagePath=cGFnZXMvYnV6ei1hcHBlYWwtcXVpei9pbmRleA` → 解码 `pages/buzz-appeal-quiz/index`。明文 `buzz-appeal-quiz` **不在包里**。  
    另有新 appId `VEjMk4pBxLYdtkWUWGghxD`（无 startPagePath）。`daRdj4PkKgdy6HNB2dgwDC` / `gE3L87HgrhVrM5YAeaseWc` 是旧 id。

## 加强 / 改版

- Square 热度说明：帖子数 + 搜索量 + 收藏人数。`People On Square`。评论区 `token badge`（持仓公开徽章）。
- 合约开仓列表可开 **Chase** 按钮：一键把挂单价改成买一/卖一。单词 `Chase` 旧包就有，这句说明是新的。
- 美股转入深链 `bnc://app.binance.com/stock/stockTransfer?direction=IN`。
- 内置 MP `7w9dcecw3ejUBkzRwYdZ95` 多了 `res/pages/paypay/layout.json`。
- 运营竞赛（当活动，不当常驻产品）：`ETH Options Trading Cup`、`GRVT Trading Challenge`、`Altcoins Summer Sprint`、`Stars & Stripes Futures Competition`、ESP 210 万、USDC 15 万、GRVT 68 万、期权竞赛 2 万 USDT。
- `Full Paid Securities Lending`、`Withdraw Arbitrage Profit`、`Support for %1$s coming soon.`（泛预告，没点名产品）。
- 聊天社区准则 quiz：`Unban & Take Quiz` / `Community Guidelines Quiz`。
- Bibi 眨眼 tooltip：`assets/bibi_tooltips_blinking_left.json` / `_right.json`。
- Onfido capture bridge 升到 `1.2`。

## 基础设施

- 小程序运行时 5.16.2 → **5.16.3**。三个内置 MP id 不变。
- Flutter 14 → **15**，新增 `module_square`。`module_content` 多了领奖台 / 热度 / 规则 / 股票图标。
- DEX 23 → 24。Play base 没有 so，**不要拿来比 native**。
- `resources.arsc` 7.19 MB → 7.27 MB（仍是瘦表，几乎没有用户向中文）。
- BouncyCastle 带上 picnic 低 MC 参数（`lowmcL1/L3/L5.bin.properties`），PQC 依赖进包。
- `res/raw/` 哈希名大量轮换，当资源重建，不当新功能。
