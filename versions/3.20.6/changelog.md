# 3.20.6 相对 3.20.5

对照：`币安 3.20.5.apk`（Play base）→ `BNApp64 (2).apk`（universal）。  
「这句是新的」在 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 / 3.20.3 / 3.20.5 上整包对过（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
**两边包装不同。** 完整包带回的 so、中文、`REQUEST_INSTALL_PACKAGES` 不是产品上新。

## 产品

1. **没有新页面、没有新接口**  
   Manifest 相对 3.20.5 **没有**新增或删除 Activity，相对完整 3.19.8 也没有「两版都没有、只在 3.20.6 出现」的 Activity。  
   dex + arsc 差集里 **没有**新的 `/bapi/`、`https://`、`bnc://`。  
   具名文件里，同时不在 3.20.5、也不在完整 3.19.8 的，只有 `classes28.dex`。eKYC / 人脸模型是完整包从 3.19.8 带回的，不是新资源。
2. **4 句只在这一包里的英文**  
   整包字节搜索：3.19.8、3.20.1、3.20.3、3.20.5 都没有，3.20.6 有。  
   `Can't skip any more tracks`  
   `Can't do that at the moment`  
   `Can't get that content here`  
   `This app can't do that`  
   像播放器 / 内容限制，不是新 slogan。`MusicBriefingViewModel`、`MusicHistoryViewModel` 在 **3.20.3** 就有。`Binance Music` 整句仍然没有。

## 看起来像新的，其实是旧功能的翻译

3.20.1–3.20.5 只有 Play base，瘦 arsc 里没有这些语言。3.20.6 的完整 arsc 第一次把它们打进安装包。英文原句在更早的 dex 里。

- 钱包统一安全升级 / Quick Backup 批量恢复（3.20.5）
- 美股定投、Benzinga 一致预期、拆合股、DTC 转仓（3.19.5 / 3.20.1 / 3.20.3）
- AOR、Agentic Wallet、Hot Wallet、Trade Hub（3.20.1）
- `Join the Options Competitions and Share 20,000 USDT in Rewards!`（3.20.1）。这版新的是「参加期权竞赛，瓜分 20,000 USDT 奖励！」这类译文
- 网格密度、Perps 账户再启用、Square token badge

## 基础设施

- 小程序运行时仍 **5.16.4**。三个内置 MP id 不变。相对完整 3.19.8，运行时从 5.16.2 换成 5.16.4，那是 3.20.1 就已经发生的。
- Flutter 相对 3.20.5 仍 15。`module_square` 相对 3.19.8 是多出来的，3.20.1 就有。
- DEX 28。相对 Play base 的 24，多出来的主要是完整包。相对完整 3.19.8 的 27，多 1 个 `classes28.dex`。未压缩 DEX：3.19.8 为 256.56 MB，3.20.5 为 234.35 MB，3.20.6 为 268.41 MB。跨版本体积，不当成这一版把业务重写了。
- `resources.arsc` 83.47 MB。完整 3.19.8 同口径 81.47 MB（旧笔记里的 85.4 MB 是按 1000 进位）。
- 权限相对完整 3.19.8 **无增减**。相对 3.20.5 Play base 多了 `REQUEST_INSTALL_PACKAGES`，这是包装。
- so 见 [README](README.md)。`libweb_weave.so`、`libamap_AGenUI.so` 是相对 3.19.8 多出来的文件；对应 Java 更早。
- 字符串差集里 3.20.5 有 `https://play.google.com/store`，3.20.6 的抽取结果没有。不当产品下线。
