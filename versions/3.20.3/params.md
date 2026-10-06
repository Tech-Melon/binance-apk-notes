# 3.20.3 参数和字段

键名在完整 3.19.8、3.20.1、3.20.3、3.20.5、3.20.6 上做了整包字节搜索（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
「新」= 3.20.1 及更早没有、从 3.20.3 起有。  
这是安装包里的字符串键，不是反编译出来的每个类字段。

## 确认新增的产品字段

没有单独的新字段名。这版新的是下面的查询赋值和功能门。

## 确认新增的开关

| 键 | 像什么 |
|---|---|
| `For You(B9)` | 行情 For You 的功能门。内部代号 B9 |

包里只有这串字。开没开要看远程配置。

## 查询参数

都在 `bnc://app.binance.com/ai/landing`。裸的 `source=`、`category=` 是常见日志碎片，只记这些完整赋值：

| 参数 | 用在哪 |
|---|---|
| `source=market_crypto_tracker` | 加密 tracker。公开接口空 `source` 会回 `unknown source` |
| `source=market_crypto_tracker&category=spot&subcategory=trending&entry=` | 同上，落到现货 trending。`entry` 是空的 |
| `source=market_ETF_tracker&category=trending` | ETF tracker |
| `source=market_market_pulse&entry=` | Market pulse |
| `source=stock_board_entry` | 美股看板入口 |
| `source=stock_board_entry&category=trending&entry=` | 看板 trending |
| `source=top_trader_trades` | Top trader |
| `source=inline_crypto_tracker_landing_ranklist&category=landingPage` | 榜单内嵌，落地页 |
| `source=inline_stock_board_landing_ranklist&category=landingPage` | 美股榜单内嵌，落地页 |
| `source=inline_stock_board_landing_ranklist&category=entryCard` | 同上，入口卡 |

`bnc://app.binance.com/music/landingPage` 从这版起有，没有查询参数。

## 调试字段

没有。

## 旧键，不要当成新的

`sourceEntry=1` 在 3.19.8 就有。`dG9SZWN1cnJpbmdIaXN0b3J5PXRydWU`（解码 `toRecurringHistory=true`）也是旧的，不是这版定投参数。`A2UI` 三个字在 3.20.1 就有。
