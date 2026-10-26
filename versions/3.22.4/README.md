# 3.22.4

> 一句话：和 3.22.3 一样是 **Play base**。巴西站合约要迁到 ADGM 国际账户，文案写的生效日是 2026-10-30。美股处理费或抵押品没结清时，会冻住一部分 BTC 提现。聊天室多了乞讨、垃圾信息和推广的警告。没有新 Activity。

| 项 | 3.22.3 Play base | 3.22.4 Play base |
|---|---|---|
| 对照文件 | `币安 3.22.3.apk` | **`币安 3.22.4.apk`** |
| 体积 | 271.26 MB | 271.60 MB |
| SHA256 | `dd284526…cf670a98` | `41258c2064e476c1674be35cfb5caa2252aee4095b02f585d4d12500947fb5ce` |
| versionCode | 100302203 | **100302204** |
| DEX | 25（未压缩 231.01 MB） | **25**（未压缩 231.32 MB） |
| 权限 | 46 | **46**，相对上一版无增减 |
| arm64 so | 0 | **0** |
| `resources.arsc` | 7.43 MB | 7.44 MB |
| 小程序运行时 | 5.16.4 | **5.16.4** |
| 内置 MP | 3 | 3，id 不变。`mp-bids-mfa-ui` 文案表多了 37 个键 |
| Flutter package | 15 | **15** |

两边都是 Play base。`versionCode` 连号 +1。相对 3.20.6 universal 仍然缺 so、缺完整中文、Manifest 没有 `REQUEST_INSTALL_PACKAGES`，那是包装，不是这版卸功能。

`Buy US Stocks on Binance`、期权适当性评估、`Options (Coming soon)`、Covered Call、Meme Rush、`Pancake Pre IPO`、`Trade U.S. Stock Options`、25,000 USDT **还在**。黄布、明文 `美股期权`、`Binance Music`、`secret menu`、带连字符的 `Pre-IPO` **仍没进包**。`https://app.binance.com/uni-qr/report-landing` 这版从包里消失，它只在 3.22.3 出现过。

**本版没有：** 新的 Manifest Activity、隐藏彩蛋、黄布、明文「美股期权」。so 差集相对完整包仍是包装。

- [相对 3.22.3](changelog.md) · [对照长文](../../compare/3.22.3-3.22.4.md)
- [文案](copy.md) · [接口](apis.md) · [参数](params.md) · [页面](surface.md) · [彩蛋](easter.md)
