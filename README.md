# 币安 App 版本笔记

非官方对照笔记。记录每个 Android 版本相对上一版 **多了什么产品、文案、接口**。  
不含安装包、不含密钥、和币安无关联。

## 版本

| 版本 | 对照 APK | 相对上一版 | 笔记 |
|---|---|---|---|
| 3.17.1 | `BNApp64.apk` | 基线 | [versions/3.17.1](versions/3.17.1/README.md) |
| 3.18.4 | `binance-3-18-4.apk` | 人脸核验 + 股票划转 + 小程序 5.15 | [versions/3.18.4](versions/3.18.4/README.md) · [对照](compare/3.17.1-3.18.4.md) |
| 3.19.5 | `BNApp64_V3.19.5.apk` | 美股开卖文案 + 预测市场进广场 + 跟单自管 | [versions/3.19.5](versions/3.19.5/README.md) · [对照](compare/3.18.4-3.19.5.md) |
| 3.19.8 | `BNApp64_V3.19.8.apk` | 美股期权交易 UI + 期权链接口 | [versions/3.19.8](versions/3.19.8/README.md) · [对照](compare/3.19.5-3.19.8.md) |

## 每版里有什么

```text
versions/<版本>/
  README.md       一页看懂
  changelog.md    相对上一版
  copy.md         文案（新 / 旧 / 没进包）
  apis.md         接口（含实打）
  easter.md       彩蛋和误判
```

下一版复制 [`versions/_template`](versions/_template/README.md)。

## 不是什么

- 不是官方更新日志
- 不托管 APK
- 字符串差集不等于功能一定上线（有 feature flag / 区域）
- 「仅新窗口」不等于新句子，资源表重建会制造假新增
