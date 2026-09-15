# 3.20.5 相对 3.20.3

对照用 Play base：`币安 3.20.3.apk` → `币安 3.20.5.apk`。  
「这句是新的」额外在 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 Play base 上整包对过。  
**没有 BNApp64 3.20.5**，不拿缺 so / 缺中文当产品下线。

## 产品

1. **Web3 钱包统一安全升级 + Quick Backup 批量恢复**  
   新 Activity：`WalletBatchRestoreProgressActivity`。  
   组件：`UnifiedSecureMultiWalletUpgradeUIComponent`、`UnifiedSecureMultiUpgradeGuideDialog`、`BatchRestoreOrchestrator`。  
   新句：`Security Upgrade`、`Upgrading security...`、`Quick Security Check Needed`。  
   批量：`All your wallets have Quick Backup and can be restored in batch.`  
   `Wallets with Quick Backup support batch restore. Others need to be restored individually.`  
   `Restore %d Wallets` / `Individual Restore` / `Restore Complete`。  
   多钱包升级要逐个指纹：`You will need to use your Fingerprint to authorize one by one.`  
   设备安全设置变了会二次确认：`Your assets are safe on-chain. A change to your device's security settings...`  
   统一密码不可找回：`I understand that if I forget this password, Binance cannot recover it...`  
   资源：`assets/mpc_unified_secure_upgrade_processing.json`（含 dark / success）。  
   接口：`/wallet/security/backup`、`/wallet/security/restore`、`/buw/self-custody/restore/batch/risk`（都要登录）。  
   root 设备会拦批量恢复。
2. **预测市场上/下事件原生接口**  
   旧私有 `.../prediction/native/market/list` 从这版字符串里消失。  
   换成公开：`.../event/detail`、`.../event/up-down/list`。  
   dex 里有 `SettledMarketListDataBlock`、`MarketTopicDataBlock`、`UpDownTradeFragment`、`SettledTimelineSheet`。  
   调试句写「过去」结算列表、timeline、slug 回落。  
   `Add prediction market` **旧**；这版新的是 event / up-down 路径。  
   公开空参和若干猜测字段都 `000002`，未继续猜。
3. **美股期权实时报价单设备占用**  
   新句：`Real-time quotes are available on one device at a time.`  
   `Your options quotes are delayed by 15 minutes, real-time is currently on another device.`  
   `Switch to Current Device`。  
   接口：`/bapi/equity/v1/private/equity/option/wss/switch`（要登录）。  
   `Turn on Real-time Quotes` / `Options (Coming soon)` **仍是旧文案**。明文 `美股期权` / Covered Call **仍没有**。
4. **行情页个性化**  
   `Create my own page`、`Page personalized. Scroll down to customize widgets.`、`Rearranging your page...`。  
   问卷：`Which kind of product would you most like to see?`、`#MarketForMeSurvey#`。  
   接口：`/bapi/fe/mimir/v1/private/app-dynamic/get-markets-bottom-tab`（要登录）。  
   旧路径 `/bapi/apex/v1/private/apex/b9/market-for-me/tab/coins` 从这版字符串消失。
5. **Agent 钱包 DeFi 持仓 + MPC 代币列表**  
   `Create Agentic Wallet` 是 3.20.1 旧句。  
   这版新路径：`agent-wallet/defi/open/position`、`agent-wallet/mpc-wallet/token/list`（要登录）。  
   批量恢复会处理 agent wallet（多钱包会降级；只选一个 agent 会拦）。
6. **Perps 账户再启用**  
   `Enable Account Required`  
   `Your Perps trading authorization has expired. Please enable your account again to continue trading.`

## 加强 / 改版

- AOR 补了一句限价说明：`Buy or sell at your specified price or better on the order book of preferred pair only.`  
  dex 有 `aorOptIn` / `FUT-4936` 是否对某标的生效。AOR 产品本身是 3.20.1。
- TradFi K 线叠加未成交单：只有调试句（`get TradFi open order list flow for chart display`），没有新用户 slogan。
- 内置三个 MP 的 jwt 刷新了，页面 id 没变。

## 基础设施

- 小程序运行时仍 **5.16.4**。三个内置 MP id 不变。
- Flutter 仍 15，无新 package。
- DEX 仍 24，全量 CRC 变。未压缩 DEX 233.65 MB → 234.35 MB。
- Play base 没有 so，**不要拿来比 native**。
- `resources.arsc` 7.39 MB → 7.41 MB（仍是瘦表）。
- `res/raw/` 哈希名大量轮换（+732 / -669 ZIP 路径，有名字的新增只有 6 个），当资源重建。
- 权限相对 3.20.3 Play base **无增减**。
