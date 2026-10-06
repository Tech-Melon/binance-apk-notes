# 3.20.5 页面和客户端表面

Manifest 的 Activity 对照的是 Play base `币安 3.20.3.apk`。类名再在完整 3.19.8、3.20.1、3.20.3，以及 3.20.6 里搜裸名字。  
R8 签名里出现旧类，不算新页面。

## Manifest 新增的 Activity

| 类 | 做什么 |
|---|---|
| `com.mpc.wallet.view.activity.WalletBatchRestoreProgressActivity` | Quick Backup 批量恢复进度 |

没有去掉的 Activity。

## 裸类名确认是新的

这些不在 3.19.8、3.20.1、3.20.3 里，从 3.20.5 起有：

| 类名 | 做什么 |
|---|---|
| `UnifiedSecureMultiWalletUpgradeUIComponent` | 多钱包统一安全升级 |
| `UnifiedSecureMultiUpgradeGuideDialog` | 升级引导 |
| `BatchRestoreOrchestrator` | 批量恢复编排 |

## 看起来像新的，类名是旧的

预测事件这版换了路径（`event/detail`、`up-down/list`）。下面这些类名更早就有，不要写成这版新页面：

| 类名 | 从哪一版起 |
|---|---|
| `UpDownTradeFragment` | 3.19.8 |
| `SettledTimelineSheet` | 3.19.8 |
| `SettledMarketListDataBlock` | 3.20.1 |
| `MarketTopicDataBlock` | 3.20.1 |

## Manifest 去掉的 Activity

没有。

## 域名和依赖

没有新的对外域名。资源新增的是 `assets/mpc_unified_secure_upgrade_processing.json`（含 dark / success），见 [changelog.md](changelog.md)。

## 这轮没有单独立项的

- so：这份是 Play base，没有 `lib/`
- `res/raw/` 哈希轮换
- 服务端开关的当前值
