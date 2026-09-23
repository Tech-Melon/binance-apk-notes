# 3.20.6

> 一句话：相对 3.20.5，**没有新 Activity、没有新接口、没有新 deeplink**。这是 3.19.8 之后第一份 `BNApp64` 完整包，完整 `resources.arsc` 把 3.20.1–3.20.5 已经上线的功能翻译补了回来。能确认只在这一包里的用户英文，是 4 句播放器限制。

| 项 | 3.20.5 Play base | 3.20.6 BNApp64 |
|---|---|---|
| 对照文件 | `币安 3.20.5.apk` | **`BNApp64 (2).apk`** |
| 体积 | 262.83 MB | 306.82 MB |
| SHA256 | `d0a3c218b0e1fc27319906fc8adfcb2dcc4c0e6d3453a3f2291c5476bcf6068c` | `26476a35bce4c5f48607610cd62654227c3c7f4cbe7e213f694f29aa857b557c` |
| DEX | 24 | **28**（未压缩 234.35 MB → 268.41 MB。相对 Play base 多出来的 dex 主要是完整包，不是单版重写） |
| 权限 | 46，没有 `REQUEST_INSTALL_PACKAGES` | **47**，有 `REQUEST_INSTALL_PACKAGES`。和完整 3.19.8 一样，相对完整包无增减 |
| arm64 so | 0 | **76** |
| `resources.arsc` | 7.41 MB | 83.47 MB（完整 3.19.8 同口径 81.47 MB） |
| 小程序运行时 | 5.16.4 | **5.16.4** |
| 内置 MP | 3 | 3，id 不变 |
| Flutter package | 15 | **15**（相对 3.20.5 无增减） |

包装和 3.20.5 **不是同类包**。缺 so / 缺中文 / Manifest 没有 `REQUEST_INSTALL_PACKAGES` 在 3.20.5 上是 Play base，不是 3.20.6 把功能加回来。

so 只能和完整 3.19.8（74 个）比，中间隔了三版：去掉 `libaa71.so`、`libc6a665.so`，多了 `liba13f47.so`、`libddd4.so`、`libamap_AGenUI.so`、`libweb_weave.so`。67 个同名 so 的 CRC 变了。`WebWeaveNativeViewController` 从 **3.20.1** 的 dex 里就有；AGenUI 的 Java 从 **3.20.3** 就有。native 文件第一次出现在我们手头的完整包里，**不能写成 3.20.6 的新功能**。

`Dina Degen`、烟花/月球、AI Pro、Dual Identity、`Options (Coming soon)`、AOR / 定投 / AGenUI / Jarvis / music / Agentic Wallet / Hot Wallet / Trade Hub **仍是旧文案**。黄布 / `Continue to X` / 明文 `美股期权` / Covered Call / `Binance Music` **仍没进包**。

**本版没有：** 新页面、新 `/bapi/`、新 `bnc://`、隐藏彩蛋、meme 新产品、黄布。

- [相对 3.20.5](changelog.md) · [对照长文](../../compare/3.20.5-3.20.6.md)
- [文案](copy.md) · [接口](apis.md) · [彩蛋](easter.md)
