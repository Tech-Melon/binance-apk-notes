# 3.20.1 彩蛋

## 真彩蛋

没有。没有 secret menu / 点 Logo / 摇一摇解锁。  
`you found` 能在旧包里搜到，是子串误报，不是「you found it」。

## 产品预告（这版新进或仍在）

- `Support for %1$s coming soon.` — **这版新句**，占位符，没写死产品名。
- `Options (Coming soon)` — 3.17.1 起就有，Play base 这版英文还在。

## 看起来像彩蛋、其实是旧文案或包装假差

| 东西 | 实际 |
|---|---|
| `Dina Degen` | 3.17.1 起就在 `classes3.dex` |
| `Binance AI Pro is coming soon` / Dual Identity | 3.17.1 |
| 烟花 / to the moon / `我进场就像放烟花` / `期权（即将上线）` | 完整 3.19.8 有。Play base 搜不到中文 **≠ 删了** |
| Play base 0 个 so / 瘦 arsc / 无 `REQUEST_INSTALL_PACKAGES` | `币安 3.20.1.apk` 是拆分包装，和 3.19.8 Play base 同类。还没有 `BNApp64` |
| dex 里中文「孤儿引擎 / 保险槽 / 预热升槽」 | Live Flutter 引擎调试日志，不是用户文案 |
| `Illegal Field. No non square value can be found` | 密码学库，不是 Square 产品 |
| BouncyCastle picnic / Ascon / Dilithium 字样 | PQC 依赖进包，不是彩蛋 |
| `EggView` | 人脸 SDK 取景框（旧结论仍成立） |

## 运营活动（新进包，不是彩蛋）

ETH Options Trading Cup、GRVT Trading Challenge、Altcoins Summer Sprint、Stars & Stripes Futures Competition、ESP / USDC / GRVT / 期权奖金池。当远程配置的活动文案。

## 没进这些包

`Continue to X`、yellow cloth、under the cloth。黄布图只在站外 X，继续盯远程小程序 / CMS / `getUserAppFeatures` v3。  
明文 `buzz-appeal-quiz` 不在包里，只有双重/单重 base64 的 `startPagePath`。

## 扫描误报

`US Eastern`、`clothing_store`、`curtains` 库、`org.meowcat.edxposed`、R8 哈希、`keccak`、BouncyCastle `square` 数学句。  
`coming soon` / `AOR` / `Chase` 单字或短子串命中率高，必须看整句。
