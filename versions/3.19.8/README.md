# 3.19.8

> 一句话：相对 3.19.5，**美股期权交易 UI 落地**（期权链 / 下单 / 行权 / OCC·ORF 规费 / 15 分钟延时行情），顺带个股研究卡和网格参数接口。

| 项 | 3.19.5 | 3.19.8 |
|---|---|---|
| 对照文件 | `BNApp64_V3.19.5.apk` | `币安 3.19.8.apk` |
| 体积 | 293.59 MB | 251.98 MB（**-41.61 MB**） |
| SHA256 | `2ab3e71075b83752189ddb41ecab7eabe19ac1bbbaf30d7f0e55b06d943af5a7` | `7a6cbca9cbe245f631f4226a79116b6f9cf4f5d0562724577b877ba43047e5b6` |
| DEX | 27 | 23（全量 CRC 变，按组件看不是重写） |
| 权限 | — | **去掉** `REQUEST_INSTALL_PACKAGES` |
| 小程序运行时 | 5.16.1 | **5.16.2** |
| 内置 MP / Flutter package | 3 / 14 | 3 / 14，没新包 |

**先读包装差异：** 这份 3.19.8 很像 Play App Bundle 的 **base APK**，不是 3.19.5 那种 `BNApp64` universal。包内 **没有 `lib/`**，`resources.arsc` 84.9 MB → 7.5 MB（默认英文，中文句会整批「消失」）。下面「没了」如果只出现在 so / 中文资源 / eKYC 模型上，**不当成产品下线**。

体积下降主要是资源表瘦身 + 这份包不带 native。DEX 仍约 226 MB 未压缩。

**本版没有：** 隐藏彩蛋、meme / 动物新产品、黄布、`Continue to X`。  
`Dina Degen`、烟花/月球分享、AI Pro、Dual Identity **仍是旧文案**。`Options (Coming soon)` **还在**，和已上线的期权链并存，灰度两态。

- [相对 3.19.5](changelog.md) · [对照长文](../../compare/3.19.5-3.19.8.md)
- [文案](copy.md) · [接口](apis.md) · [彩蛋](easter.md)
