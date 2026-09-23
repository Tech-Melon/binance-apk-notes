# 3.20.6 彩蛋

## 真彩蛋

没有。没有 secret menu / 点 Logo / 摇一摇解锁。

## 产品预告

没有新的 coming soon 英文句。  
`Options (Coming soon)`、`Support for %1$s coming soon.` 仍是旧文案。  
「即将支持 %1$s。」是完整 arsc 里的旧预告译文。

## 看起来像彩蛋、其实是旧文案或包装

| 东西 | 实际 |
|---|---|
| 大量中文「安全升级 / 定投 / 期权竞赛 / 网格密度」 | 3.20.1–3.20.5 英文功能的译文。上一版是瘦 arsc，所以这版完整包第一次带上 |
| `Can't skip any more tracks` 等 4 句 | 只在 3.20.6。像播放器限制，不是隐藏菜单，也不是 `Binance Music` |
| 76 个 so、`REQUEST_INSTALL_PACKAGES`、83 MB arsc | 完整包相对 Play base 的包装。权限和完整 3.19.8 一致 |
| `libamap_AGenUI.so` / `libweb_weave.so` | 相对 3.19.8 多出来的 native 文件。Java 类更早：Weave 控制器 3.20.1，AGenUI 3.20.3 |
| `Dina Degen` / AI Pro / Dual Identity / 烟花 | 旧文案 |
| `bnc://x` | 短串，不是黄布 |
| `https://play.google.com/store` 从字符串差集消失 | Play base 上有、这版抽取没有。不当下线 |

## 没进包

`Continue to X`、yellow cloth、under the cloth。黄布继续盯远程小程序 / CMS / `getUserAppFeatures` v3。  
明文 `美股期权`、Covered Call、`Binance Music`、`secret menu` 仍没有。

## 扫描误报

R8 签名串里出现旧类名（`MusicBriefingViewModel`、`WebWeaveNativeViewController`、`JarvisBizWidgetSlotFragment`）只说明签名文本变了，类本身要整包搜类名。  
`res/raw/` 两千多个哈希文件是资源轮换。  
`you found`、`US Eastern`、`coming soon` 短句不能单独当彩蛋。
