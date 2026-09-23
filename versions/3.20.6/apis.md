# 3.20.6 接口

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`，`User-Agent: Binance/3.20.6 (Android)`

## 新路径

没有。  
3.20.6 的 dex + 完整 arsc + 小配置 assets，相对 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 / 3.20.3 / 3.20.5 的字符串差集里，**没有**新的 `/bapi/`、`https://`、`bnc://`。

3.20.5 那批路径还在旧结论里，这版没有新的可打：

- 预测 `event/up-down/list`、`event/detail`
- 钱包 backup / restore、批量风控
- Agent 钱包 DeFi 持仓、MPC 代币列表
- 期权 `wss/switch`
- 行情底栏 `get-markets-bottom-tab`

## 实打记录

这版没有新路径。下面只复打仍公开的旧接口，确认网关还在。

| 方法 | 路径 | 实打 |
|---|---|---|
| GET | `/bapi/apex/v1/friendly/apex/app/markets/tabs` | 200 `000000`，`defaultTab=fav` |
| GET | `/bapi/equity/v1/public/equity/recurring-buy/symbol/get-symbols-index` | 200。样例 `EQ_MU` / `EQ_SNDK` / `EQ_NVDA`，后面还有约 297 个 |
| GET | `/bapi/fe/mimir/v2/public/get-ai-landing-page?source=market_crypto_tracker` | 200 `000000` |
| GET | `/bapi/defi/v1/public/wallet-direct/prediction/native/market/event/up-down/list` | 400 `000002 illegal parameter` |
| GET | `/bapi/defi/v1/public/wallet-direct/prediction/native/market/event/detail` | 400 `000002 illegal parameter` |

私有接口这轮没有新路径，不重复编返回体。未登录仍应按 3.20.5 的记录理解：`100001005`。

## 深链

这轮 **没有新增** `bnc://`。
