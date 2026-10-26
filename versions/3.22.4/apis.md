# 3.22.4 接口

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`，`User-Agent: Binance/3.22.4 (Android)`

路径来自 dex + 瘦 arsc + 小配置 assets 的差集，再在旧包里做整文件字节搜索。5 条 `/bapi/` 在 3.18.4 到 3.22.3 都没有。没有删掉的旧 `/bapi/`。

写操作没有打。private 未登录按 `100001005` 理解。

## 实打

| 方法 | 路径 | 鉴权 | 含义 | 实打 |
|---|---|---|---|---|
| GET | `/bapi/accounts/v1/private/account/entityMirror/openEntityMirrorAccount` | 要登录 | 开实体镜像账户。和巴西合约迁到 ADGM 的文案放一起看 | 401 `100001005 Please log in first.` |
| GET | `/bapi/accounts/v1/private/account/entityMirror/queryMigrationResult` | 要登录 | 查迁移结果 | 401 `100001005 Please log in first.` |
| GET | `/bapi/accounts/v1/private/authcenter/mirror/switchLogin` | 要登录 | 镜像账户切换登录。裸词 `switchLogin` 是旧的 | 401 `100001005 Please log in first.` |
| GET | `/bapi/futures/v2/private/future/account/query-account-migration-status` | 要登录 | 合约账户迁移状态 | 401 `100001005 Please log in first.` |
| GET | `/bapi/fe/mimir/v2/private/get-ai-landing-share-link` | 要登录 | AI 落地页分享链接。和迁移不是一条产品线 | 401 `100001005 Please check if you are logged in.` |

## 全量新 /bapi/

下面每条都在旧包字节搜索里确认过。没有别的新路径。

镜像账户和合约迁移：

- `/bapi/accounts/v1/private/account/entityMirror/openEntityMirrorAccount`
- `/bapi/accounts/v1/private/account/entityMirror/queryMigrationResult`
- `/bapi/accounts/v1/private/authcenter/mirror/switchLogin`
- `/bapi/futures/v2/private/future/account/query-account-migration-status`

AI 落地页：

- `/bapi/fe/mimir/v2/private/get-ai-landing-share-link`

## 不是新接口

`https://app.binance.com/uni-qr/report-landing` 从这一包消失。它不是 `/bapi/`，而且只在 3.22.3 出现过。
