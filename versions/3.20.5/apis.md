# 3.20.5 接口

本轮只有 Play base。下面实打用 `www.binance.com`。

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`，`User-Agent: Binance/3.20.5 (Android)`

## 新路径（相对 3.20.3 字符串差集，且 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 / 3.20.3 没有）

| 方法 | 路径 | 鉴权 | 含义 | 实打 |
|---|---|---|---|---|
| GET | `/bapi/defi/v1/public/wallet-direct/prediction/native/market/event/up-down/list` | public | 预测市场上/下事件列表 | 400 `000002` |
| GET | `/bapi/defi/v1/public/wallet-direct/prediction/native/market/event/detail` | public | 预测市场事件详情 | 400 `000002` |
| GET | `/bapi/defi/v1/private/wallet-direct/agent-wallet/defi/open/position` | 要登录 | Agent 钱包 DeFi 持仓 | 401 |
| GET | `/bapi/defi/v1/private/wallet-direct/agent-wallet/mpc-wallet/token/list` | 要登录 | Agent / MPC 代币列表 | 401 |
| GET | `/bapi/defi/v1/private/wallet-direct/buw/self-custody/restore/batch/risk` | 要登录 | 批量恢复风控 | 401 |
| GET | `/bapi/defi/v1/private/wallet-direct/wallet/security/backup` | 要登录 | 钱包安全备份 | 401 |
| GET | `/bapi/defi/v1/private/wallet-direct/wallet/security/restore` | 要登录 | 钱包安全恢复 | 401 |
| GET | `/bapi/equity/v1/private/equity/option/wss/switch` | 要登录 | 美股期权实时报价占用切换 | 401 |
| GET | `/bapi/fe/mimir/v1/private/app-dynamic/get-markets-bottom-tab` | 要登录 | 行情底栏动态配置 | 401 |

未登录私有接口一律 `100001005`（defi/equity 文案 `Please log in first.`，mimir 文案 `Please check if you are logged in.`），不编返回体。

**这版从字符串里消失（Play base）：**

- `/bapi/apex/v1/private/apex/b9/market-for-me/tab/coins`
- `/bapi/defi/v1/private/wallet-direct/prediction/native/market/list`  
  服务端还在：未登录打仍是 401 `100001005`，只是这版 dex 不再硬编码。

**不当新路径：** 3.20.3 已有的 B9 / 定投 / `get-ai-landing-page` / `voice-names`。公开 `markets/tabs`、定投标的索引、AI landing 这轮复打仍 200。

## 实打摘要

### prediction event

`up-down/list` 与 `event/detail` 空参、以及 `page/rows/limit/categoryId/symbol/pair/slug/eventSlug/topicId/itemSlug/id/eventId` 若干组合，都是 HTTP 400、`code=000002 illegal parameter`。未继续猜字段。

### 私有

`100001005`。不编体。

### 旧公开接口仍通

`markets/tabs` 仍 `defaultTab=fav`。定投 `get-symbols-index`、`get-ai-landing-page?source=market_crypto_tracker` 仍 200。

## 深链（包内硬编码）

这轮 **没有新增** `bnc://` 字符串。3.20.3 的 `ai/landing`、`music/landingPage` 仍在。

| 原文 | 说明 |
|---|---|
| `bnc://x` | 短串，**不是** `Continue to X` |
