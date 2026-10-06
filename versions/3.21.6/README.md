# 3.21.6

> 一句话：相对 3.20.6，这一包是 **Play base**。美股期权从「即将上线」推进到可交易文案（1000+ 标的、交易所路由、备兑/现金担保、期权链接口），并带上 Meme Rush、Pancake Pre-IPO、资金账户迁移。

| 项 | 3.20.6 BNApp64 | 3.21.6 Play base |
|---|---|---|
| 对照文件 | `BNApp64 (2).apk` | **`币安 3.21.6.apk`** |
| 体积 | 306.82 MB | 268.98 MB |
| SHA256 | `26476a35…857b557c` | `ac8813e3f456fd313189ef49597878be2fd42e66aa7179e954a7dd0c91e36d42` |
| versionCode | — | **100302106** |
| DEX | 28（未压缩 255.98 MB） | **25**（未压缩 229.57 MB）。相对同类 Play base 3.20.5 的 24 个，多了 `classes25.dex` |
| 权限 | 47，有 `REQUEST_INSTALL_PACKAGES` | **46**，没有这条。和 3.20.5 Play base 一样，相对完整包的差是包装 |
| arm64 so | 76 | **0** |
| `resources.arsc` | 83.47 MB | 7.36 MB（3.20.5 同口径 7.41 MB） |
| 小程序运行时 | 5.16.4 | **5.16.4** |
| 内置 MP | 3 | 3，id 不变 |
| Flutter package | 15 | **15**（相对 3.20.6、相对 3.20.5 都无增减） |

包装和 3.20.6 **不是同类包**。缺 so、缺完整中文、Manifest 没有 `REQUEST_INSTALL_PACKAGES`，是 Play base，不是这版把功能卸了。同类包装对照是 3.20.5。手头没有 3.20.7–3.21.5，下面说的「新」是相对已有安装包，中间版可能已经带上其中一部分。

`Options (Coming soon)` 还在包里。同时新出现 `Trade U.S. Stock Options — Now on Binance`。黄布、明文 `美股期权`、`Binance Music`、`secret menu` **仍没进包**。`Dina Degen`、烟花、提现保护、防抢 **仍是旧文案**。

**本版没有：** 隐藏彩蛋、黄布、明文「美股期权」、Binance Music。so 差集不当产品变化。

- [相对 3.20.6](changelog.md) · [对照长文](../../compare/3.20.6-3.21.6.md)
- [文案](copy.md) · [接口](apis.md) · [参数](params.md) · [页面](surface.md) · [彩蛋](easter.md)
