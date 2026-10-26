# 3.22.4 页面和客户端表面

Manifest 的 Activity 对过 3.22.3、3.21.6、3.20.6。类名再搜裸名字。  
R8 签名里出现旧类，不算新页面。这一版 **没有** 新增 Activity，也没有相对 3.22.3 删掉 Activity。

## Manifest 新增的 Activity

没有。

## 裸类名确认是新的

这些不在 3.22.3、3.21.6、3.20.6、3.20.5 里：

| 类名 | 做什么 |
|---|---|
| `FuturesBrMigrationRepository` | 巴西合约迁移。旁边有 `evaluateInternal` 的 R8 名 |
| `FuturesBrMigrationBillboard` | 迁移公告条。源文件名 `FuturesBrMigrationBillboard.kt` |
| `FuturesBrMigrationBubble` | 迁移气泡。源文件名 `FuturesBrMigrationBubble.kt` |
| `FuturesComplianceRepository` | 合约合规仓库。源文件名 `FuturesComplianceRepository.kt` |
| `com.binance.android.nezha.plugin.mirrorAccount.MirrorAcountPlugin` | 镜像账户小程序插件。类名拼成 `Acount` |
| `BannerNoFuturesAccount` | 状态名，出现在 `not opened -> BannerNoFuturesAccount`。不是 Manifest Activity |

`StockRankAnomalyFilter` 的裸名字旧包就有。新的只是 `$copydefault` 签名整段。

## Manifest 去掉的 Activity

相对 3.22.3：没有。

3.22.3 已经去掉的银行转账买币详情、卖出银行卡管理、香草期权偏好页，不是这版新删的。

## 域名和依赖

| 字符串 | 旧 | 新 |
|---|---|---|
| `https://app.binance.com/uni-qr/report-landing` | 3.22.3 有 | **这版没有**。3.21.6 和 3.20.6 也没有 |
| `mp-bids-mfa-ui` / `cH6sYTb5RTJEkpuwrbn7zm` | 小程序还在 | 还在。文案表多 37 键。project 描述是 `risk challenge` |
| 另外两个内置 MP id | 在 | 在。只变了 jwt |
| 小程序运行时 | 5.16.4 | 5.16.4 |
| Flutter package | 15 | 15 |
| `lib/arm64-v8a` | 0 | 0。完整包 3.20.6 有 76 个 so，那是包装 |

没有新的对外域名。接口仍打 `www.binance.com`。

## 这轮没有单独立项的

- so：两边都没有 `lib/arm64-v8a`
- `res/raw/` 哈希轮换（相对 3.22.3 大约 421 增、415 删）
- `META-INF/services/` 三个混淆服务名对调
- 具名新文件：0。相对 3.20.6 才看见的 `PublicSuffixDatabase.list`、`StrategyAgentEventMsg.proto`、skylinef 字体，3.22.3 就已经有
- 服务端开关的当前值
