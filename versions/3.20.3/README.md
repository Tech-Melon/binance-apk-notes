# 3.20.3

> 一句话：相对 3.20.1，**美股定投 Recurring Buy**、**行情 For You / B9 + AGenUI 动态卡片**、**Jarvis 透明浮层 + 语音**，以及 **行情简报播放（`music` 模块）**。本轮仍只有 Play base，缺 so / 缺中文 **不是下线**；AGenUI 还带 `SO load failed` / `不含 arm64-v8a` 调试句，native 引擎要靠 split。

| 项 | 3.20.1 Play base | 3.20.3 Play base |
|---|---|---|
| 对照文件 | `币安 3.20.1.apk` | **`币安 3.20.3.apk`** |
| 体积 | 254.40 MB | 262.03 MB（**+7.63 MB**） |
| SHA256 | `467a4c96…ede4b7cc` | `1ae4822a0048d3461c21b0f3809182aa9ebf23bfc99b8a6ced13f3f3cc186d77` |
| DEX | 24 | **24**（CRC 全量变，按组件看不是重写；未压缩 DEX +7.0 MB） |
| 权限 | 无增减 | 两边都没有 `REQUEST_INSTALL_PACKAGES`（Play base 包装） |
| arm64 so | 0 | **0** |
| `resources.arsc` | 7.27 MB | 7.39 MB |
| 小程序运行时 | 5.16.3 | **5.16.4** |
| 内置 MP | 3 | 3，id 不变 |
| Flutter package | 15 | **15**（无增减，`module_square` 仍在） |

**没有 `BNApp64` 完整包。** 产品文案的「新/旧」是拿 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 Play base 整包字节搜过的。

`Dina Degen`、烟花/月球、AI Pro、Dual Identity、`Options (Coming soon)`、AOR / 成本价 / 消息请求 / Agentic Wallet / Hot Wallet / Trade Hub **仍是旧文案**。黄布 / `Continue to X` / 明文 `美股期权` / Covered Call **仍没进包**。

**本版没有：** 隐藏彩蛋、meme / 动物新产品、黄布、`secret menu`、独立「Binance Music」歌单产品句。

- [相对 3.20.1](changelog.md) · [对照长文](../../compare/3.20.1-3.20.3.md)
- [文案](copy.md) · [接口](apis.md) · [彩蛋](easter.md)
