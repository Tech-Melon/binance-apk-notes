# 3.19.8

> 一句话：相对 3.19.5，**美股期权交易 UI 落地**（期权链 / 下单 / 行权 / OCC·ORF 规费 / 15 分钟延时行情），顺带个股研究卡和网格参数接口。

| 项 | 3.19.5 | 3.19.8 |
|---|---|---|
| 对照文件 | `BNApp64_V3.19.5.apk` | **`BNApp64_V3.19.8.apk`**（完整 universal） |
| 体积 | 293.59 MB | 294.80 MB（**+1.21 MB**） |
| SHA256 | `2ab3e71075b83752189ddb41ecab7eabe19ac1bbbaf30d7f0e55b06d943af5a7` | `5979e0d0c26ab7ff78d720633080a50f89fd4d3060c13ffe52b444bc0e061b7e` |
| DEX | 27 | 27（全量 CRC 变，按组件看不是重写） |
| 权限 | — | **无增减**（`REQUEST_INSTALL_PACKAGES` 仍在） |
| arm64 so | 73 | **74** |
| 小程序运行时 | 5.16.1 | **5.16.2** |
| 内置 MP / Flutter package | 3 / 14 | 3 / 14，没新包 |

同目录另有一份 `币安 3.19.8.apk`（251.98 MB，无 `lib/`，arsc 7.5 MB），是 Play base 拆分，**不作产品对照**。上一轮用它扫过接口和英文案；缺 so / 缺中文是包装，不是下线。base 的 Manifest 里没有 `REQUEST_INSTALL_PACKAGES`，完整包有——以 universal 为准。

`resources.arsc` 84.9 MB → 85.4 MB，中文/繁中/日文都在。

**本版没有：** 隐藏彩蛋、meme / 动物新产品、黄布、`Continue to X`、明文 slogan `美股期权`。  
`Dina Degen`、烟花/月球分享、AI Pro、Dual Identity **仍是旧文案**。`Options (Coming soon)` / `期权（即将上线）` **还在**，和已上线的期权链并存，灰度两态。

- [相对 3.19.5](changelog.md) · [对照长文](../../compare/3.19.5-3.19.8.md)
- [文案](copy.md) · [接口](apis.md) · [彩蛋](easter.md)
