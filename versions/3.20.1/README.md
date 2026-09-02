# 3.20.1

> 一句话：相对 3.19.8，**美股自动订单路由 AOR**、**钱包成本价/均价改版**、**聊天消息请求**，以及 **Flutter `module_square` 首次进包**。本轮只有 Play base，缺 so / 缺中文 **不是下线**。

| 项 | 3.19.8 Play base | 3.20.1 Play base |
|---|---|---|
| 对照文件 | `币安 3.19.8.apk` | **`币安 3.20.1.apk`** |
| 体积 | 251.98 MB | 254.40 MB（**+2.42 MB**） |
| SHA256 | — | `467a4c96673e6322db2190d4db812859629ad28d50aa675de3a14c9eede4b7cc` |
| DEX | 23 | **24**（新增 `classes24.dex`；CRC 全量变，按组件看不是重写） |
| 权限 | 相对 3.19.8 base **无增减** | 两边都没有 `REQUEST_INSTALL_PACKAGES`（Play base 包装，**不以完整包为准**） |
| arm64 so | 0 | **0**（Play base 本来就没有 `lib/`） |
| `resources.arsc` | 7.19 MB | 7.27 MB |
| 小程序运行时 | 5.16.2 | **5.16.3** |
| 内置 MP | 3 | 3，id 不变；多了 `paypay/layout.json` |
| Flutter package | 14 | **15**（新增 **`module_square`**） |

**没有 `BNApp64` 完整包。** 产品文案的「新/旧」是拿 3.18.4 / 3.19.5 / 3.19.8 **universal** 整包字节搜过的；so 哈希、中文资源表、`REQUEST_INSTALL_PACKAGES` 等完整包才有的东西，这轮不下结论。若之后拿到 `BNApp64_V3.20.1`，再补一层 native / 中文。

`Dina Degen`、烟花/月球、AI Pro、Dual Identity、`Options (Coming soon)` **仍是旧文案**。黄布 / `Continue to X` / 明文 `美股期权` **仍没进包**。

**本版没有：** 隐藏彩蛋、meme / 动物新产品、黄布、`secret menu`。  
运营向竞赛文案很多（ETH Options Cup / GRVT / ESP / Stars & Stripes），当活动配置，不当常驻功能。

- [相对 3.19.8](changelog.md) · [对照长文](../../compare/3.19.8-3.20.1.md)
- [文案](copy.md) · [接口](apis.md) · [彩蛋](easter.md)
