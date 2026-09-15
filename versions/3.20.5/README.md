# 3.20.5

> 一句话：相对 3.20.3，**Web3 钱包统一安全升级 + Quick Backup 批量恢复**、**预测市场上/下事件原生接口**、**美股期权实时报价单设备占用**，以及 **Agent 钱包 DeFi 持仓 / 代币列表 + Perps 账户再启用**。本轮仍只有 Play base，缺 so / 缺中文 **不是下线**。

| 项 | 3.20.3 Play base | 3.20.5 Play base |
|---|---|---|
| 对照文件 | `币安 3.20.3.apk` | **`币安 3.20.5.apk`** |
| 体积 | 262.03 MB | 262.83 MB（**+0.80 MB**） |
| SHA256 | `1ae4822a0048d3461c21b0f3809182aa9ebf23bfc99b8a6ced13f3f3cc186d77` | `d0a3c218b0e1fc27319906fc8adfcb2dcc4c0e6d3453a3f2291c5476bcf6068c` |
| DEX | 24 | **24**（CRC 全量变；未压缩 DEX 233.65 MB → 234.35 MB） |
| 权限 | 无增减 | 两边都没有 `REQUEST_INSTALL_PACKAGES`（Play base 包装） |
| arm64 so | 0 | **0** |
| `resources.arsc` | 7.39 MB | 7.41 MB |
| 小程序运行时 | 5.16.4 | **5.16.4** |
| 内置 MP | 3 | 3，id 不变 |
| Flutter package | 15 | **15**（无增减，`module_square` 仍在） |

**没有 `BNApp64` 完整包。** 产品文案的「新/旧」是拿 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 Play base / 3.20.3 Play base 整包字节搜过的。

`Dina Degen`、烟花/月球、AI Pro、Dual Identity、`Options (Coming soon)`、AOR / 成本价 / 消息请求 / Agentic Wallet / Hot Wallet / Trade Hub / 美股定投 / AGenUI / Jarvis / music **仍是旧文案**。黄布 / `Continue to X` / 明文 `美股期权` / Covered Call **仍没进包**。

**本版没有：** 隐藏彩蛋、meme / 动物新产品、黄布、`secret menu`、独立「Binance Music」歌单产品句、新 Flutter package。

- [相对 3.20.3](changelog.md) · [对照长文](../../compare/3.20.3-3.20.5.md)
- [文案](copy.md) · [接口](apis.md) · [彩蛋](easter.md)
