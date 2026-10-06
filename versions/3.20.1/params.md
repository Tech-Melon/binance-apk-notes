# 3.20.1 参数和字段

键名在完整 3.19.8、3.20.1、3.20.3、3.20.5、3.20.6 上做了整包字节搜索（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
「新」= 3.19.8 没有、从 3.20.1 起有。  
这是安装包里的字符串键，不是反编译出来的每个类字段，也不是服务端开关的当前值。

## 确认新增的产品字段

| 键 | 像什么 |
|---|---|
| `isAor` | AOR 标的标记。`Auto Order Routing` 这套文案也是这版新的 |

`aorExchangeRate`、`aorFxConvertedFlag`、`aorNativeSymbol`、`aorOptIn` 要到 3.20.5 才出现。

## 确认新增的开关

没有。差集里的 `reason=`、`engine=`、`roomId=` 是日志键，不记。

## 查询参数

| 参数 | 用在哪 | 对照 |
|---|---|---|
| `direction=IN` | `bnc://app.binance.com/stock/stockTransfer` | 从 3.20.1 起有。美股转入 |
| `startPagePath=cGFnZXMvYnV6ei1hcHBlYWwtcXVpei9pbmRleA` | 旧 appId `znf9fpiMh6ufdU3vDtAvi4` | 解码是 `pages/buzz-appeal-quiz/index`。明文 `buzz-appeal-quiz` 不在包里 |

`get-quote-v2` 和 `avgCost` 是路径，写在 [apis.md](apis.md)，不是查询键。

## 调试字段

没有。

## 旧键，不要当成新的

`sourceEntry=1` 在完整 3.19.8 就有。差集里带这个参数的那条深链，appId 是旧的。
