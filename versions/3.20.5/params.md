# 3.20.5 参数和字段

键名在完整 3.19.8、3.20.1、3.20.3、3.20.5、3.20.6 上做了整包字节搜索（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
「新」= 3.20.3 及更早没有、从 3.20.5 起有。  
这是安装包里的字符串键，不是反编译出来的每个类字段。

## 确认新增的产品字段

| 键 | 像什么 |
|---|---|
| `aorExchangeRate` | AOR 换算汇率。出现在拼接字段串里 |
| `aorFxConvertedFlag` | 是否已经按外汇换算 |
| `aorNativeSymbol` | AOR 原生标的 |
| `aorOptIn` | 某标的是否加入 AOR。旁边有 `aorOptIn failed or returned false` |
| `FUT-4936` | 内部单号，和 `aorOptIn` 写在一起，用来判断某标的是否走 AOR |

AOR 产品本身是 3.20.1。这版补的是上面这些字段。

## 确认新增的开关

没有。

## 查询参数

没有新的查询参数，也没有新的 `bnc://`。  
这版新的是路径，写在 [apis.md](apis.md)：钱包 backup / restore、预测 `event/detail` 与 `up-down/list`、期权 `wss/switch`、行情 `get-markets-bottom-tab`、agent-wallet 两条。

`walletId`、`walletType`、`slug`、`timeline` 只出现在被差集标成新的长句里。裸键没有单独核对成「这版才有」，不记。

## 调试字段

没有。

## 旧键，不要当成新的

`isAor` 从 3.20.1 就有。
