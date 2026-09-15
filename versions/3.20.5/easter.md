# 3.20.5 彩蛋

## 真彩蛋

没有。没有 secret menu / 点 Logo / 摇一摇解锁。  
`you found` 能在旧包里搜到，是子串误报。

## 产品预告（这版仍在）

- `Options (Coming soon)` — 3.17.1 起就有，Play base 这版英文还在。
- `Support for %1$s coming soon.` — 3.20.1 的泛预告，这版仍在。

## 看起来像彩蛋、其实是旧文案或包装假差

| 东西 | 实际 |
|---|---|
| `Dina Degen` | 3.17.1 起就在 `classes3.dex` |
| `Binance AI Pro is coming soon` / Dual Identity | 3.17.1 |
| 烟花 / to the moon / `我进场就像放烟花` / `期权（即将上线）` | 完整 3.19.8 有。Play base 搜不到中文 **≠ 删了** |
| Play base 0 个 so / 瘦 arsc / 无 `REQUEST_INSTALL_PACKAGES` | 和 3.20.1 / 3.20.3 同类拆分包装。还没有 `BNApp64` |
| `AGenUI disabled: SO load failed` / `不含 arm64-v8a` | 3.20.3 已有。Play base 没 native |
| `bnc://x` | 短串，不是黄布、也不是 `Continue to X` |
| `Tokenized Stocks` / `Stock Perps` | 3.20.1 已有 |
| `Add prediction market` | 旧入口句。这版新的是 event / up-down 接口 |
| `All Set!` | 安全升级/恢复流程收尾，不是隐藏菜单 |
| `EggView` | 人脸 SDK 取景框（旧结论仍成立） |

## 没进这些包

`Continue to X`、yellow cloth、under the cloth。黄布图只在站外 X，继续盯远程小程序 / CMS / `getUserAppFeatures` v3。  
明文 `buzz-appeal-quiz` 不在包里。  
`Binance Music` 整句不在包里。  
明文 `美股期权` / Covered Call 仍没有。

## 扫描误报

`US Eastern`、`clothing_store`、`curtains` 库、`org.meowcat.edxposed`、R8 哈希、`keccak`、protobuf 二进制当字符串、Lottie JSON 碎片。  
`coming soon` / `Restore` / `Upgrade` 短句必须看整句和上下文。  
`res/raw/` 六百多个哈希文件不当新功能。  
`REQUEST_INSTALL_PACKAGES` 字符串能在 dex 里搜到 **≠ Manifest 有这个权限**（Play base 没有）。
