# 3.22.3 参数和字段

键名在 3.22.3、3.21.6、3.20.6、3.20.5、完整 3.19.8 上做了整包字节搜索（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
「新」= 这些包里只有 3.22.3 有。没有 3.21.7–3.22.2。  
这是安装包里的字符串键，不是反编译出来的每个类字段，也不是服务端开关的当前值。

## 确认新增的产品字段

| 键 | 像什么 |
|---|---|
| `KEY_OPTIONS_GEN` | 期权通用配置键，和 `option/get-config` 放一起看 |
| `INSTITUTIONAL_LOAN_LIQUIDATION_TRANSFER` | 机构贷强平划转 |
| `tool_call_name` | AI 策略事件里的工具名。在新 proto `StrategyAgentEventMsg` |
| `tool_call_id` | 同一次工具调用的 id |
| `reply_id` | 策略事件的回复 id |
| `max_iters` | 策略事件最大迭代次数 |
| `AI_DATA_STRATEGY_AGENT_EVENT` | 新的 WS / 事件频道名 |

`StrategyAgentEventMsg.proto` 里还有 `session_id`、`model_name`、`block_id`、`input_tokens`、`output_tokens`、`media_type`、`sequence`。  
`model_name`、`block_id` 旧包就有。`output_tokens` 在 3.20.6 完整包里有。这些不当成新键。新的是这份 proto 和上面几条裸名。

公开接口返回的 `closeOnlyMinutes`、`liquidationPeriod` 是服务端字段，这一轮没有在包里把它们当成新的客户端键。

## 确认新增的开关

没有新的 `*Enabled` 裸键值得单独立项。  
`country-match-enabled` 是 C2C 路径的一段，不是新的客户端开关名。缺参 GET 是 `000002`。

## 查询参数

| 参数 | 用在哪 | 对照 |
|---|---|---|
| `dialogType=createFavGroup` | `bnc://app.binance.com/dialog/common` | 只在 3.22.3 |
| `dialogType=addFavToGroup` | 同上 | 和 `asset=`、`assetType=` 一起 |
| `bundle_type=group` | `bnc://.../markets/editFav` | 只在 3.22.3 |
| `hide_holdings=1` | 同上 | 编辑自选时隐藏持仓 |
| `source=watch_list_tracking` | `bnc://.../ai/landing` | `category=favouritemore`。`favouritemore` 这条路径 3.21.6 就有 |
| `groupId=` | `bnc://.../p2p/chat` | 键名旧。新的是这条 P2P 聊天深链 |

## 调试字段

`accounts.qa1fdg.net` 上的 `quick-login?email=` 是 QA 登录地址。主机 `qa1fdg.net` 旧包就有，整段 URL 是新的。不当成用户参数。

## 旧键，不要当成新的

`get-config` 这四个字很常见。新的是整段 `/bapi/equity/v1/public/equity/option/get-config`。  
`VWAP`、`cashback`、`gridType=arbitrage`、`gridType=futuresSnowball`、`Stock traders:`、`ChatSessionListActivity`、`CopyTradingQuickCopyComponent`、`WalletBatchRestoreProgressActivity` 都是旧的。  
R8 把旧类重新拼进签名串，差集会把整段签名当成新句子。类名要再搜裸名字。
