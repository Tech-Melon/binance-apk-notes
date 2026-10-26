# 3.22.4 参数和字段

键名在 3.22.4、3.22.3、3.21.6、3.20.6 上做了整包字节搜索（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
「新」= 这些包里只有 3.22.4 有。  
这是安装包里的字符串键，不是反编译出来的每个类字段，也不是服务端开关的当前值。

`mp-bids-mfa-ui` 的 i18n 相对 3.22.3 同一文件多了 37 个键，英 / 中 / 俄三份一起加。其中 6 个 MFA 键裸名是旧的，见文末。

## 确认新增的产品字段

| 键 | 像什么 |
|---|---|
| `WITHDRAW_STOCKS_OTHER_FEE_FREEZE_AMOUNT_v1` | 美股处理费或抵押品未结清，冻住 `{0} BTC` 提现 |
| `INFO_STOCKS_OTHER_FEE_FREEZE_AMOUNT_v1` | 短句：资金因美股交易要求被冻结 |
| `MSG_STOCKS_OTHER_FEE_FREEZE_AMOUNT_v1` | 和第一条同一句的另一处文案位 |
| `BINANCE_CHAT_GENERAL_WARNING_TITLE_v1` | 聊天室警告标题。英文 `Warning`，中文「警告」 |
| `BINANCE_CHAT_SEEK_DONATION_WARNING_BODY_v1` | 向别人要钱、乞讨、募资 |
| `BINANCE_CHAT_SPAM_WARNING_BODY_v1` | 垃圾信息和无理由反复互动 |
| `BINANCE_CHAT_PROMOTION_WARNING_BODY_v1` | 推第三方频道或付费服务 |
| `LINK_REDIRECT_WITHDRAW_NEW` | 提现防钓鱼。不是本人就不要点链接 |
| `PAYMENT_CRYPTOBOX_FUTURE_CLAIM_SCAM_REJECT_v1` | 可疑活动时不能领合约红包 |
| `ANTI_SCAM_CD_ACCOUNT_GENERIC_1H_LINK_v2` | 提现反诈，禁用 1 小时。同表还有 24 小时、欺诈 URL、同 gas 来源等兄弟键 |
| `SCAM_BLACK_ADDRESS_WITHDRAW_FORBIDDEN_v5` | 转到欺诈相关地址时限制提现。`v3` 是旧键，这版只改了措辞 |
| `accounts-qr-login-tips-low-web` | 确认是本人在网页端登录 |
| `accounts-qr-login-title-low-web` | 标题：登录币安网页端 |
| `accounts-qr-login-tips-low-electron` | 桌面端确认句 |
| `accounts-qr-login-title-low-electron` | 标题：登录币安桌面端 |

同一份 i18n 里一起新增、裸键没有再逐条对 3.20.6 单搜的，都是反诈和红包兄弟键：

- `ANTI_SCAM_CD_ACCOUNT_GENERIC_1H_LINK_SRDS_v2`
- `ANTI_SCAM_CD_ACCOUNT_GENERIC_24H_LINK_v2`
- `ANTI_SCAM_CD_ACCOUNT_GENERIC_24H_LINK_SRDS_v2`
- `ANTI_SCAM_CD_BLACK_URL_RELATED_ADDRESS_LINK_v3`
- `ANTI_SCAM_CD_BLACK_URL_RELATED_ADDRESS_SRDS_v2`
- `ANTI_SCAM_CD_FAKE_URL_LINK_v3`
- `ANTI_SCAM_CD_POTENTIALLY_FRAUDULENT_URL_LINK_v3`
- `ANTI_SCAM_CD_SAME_GAS_SOURCE_ADDRESS_LINK_v3`
- `ANTI_SCAM_CD_SAME_GAS_SOURCE_ADDRESS_SRDS_v2`
- `ANTI_SCAM_CD_SILENT_SUFFERER_SRDS_v2`
- `ANTI_SCAM_POPUP_BLACK_ADDRESS_DOMAIN_1`
- `ANTI_SCAM_POPUP_BLACK_ADDRESS_DOMAIN_v1`
- `ANTI_SCAM_POPUP_BLACK_ADDRESS_DOMAIN_v2`
- `ANTI_SCAM_POPUP_BLACK_ADDRESS_DOMAIN_v3`
- `SCAM_BLACK_DOMAIN_WITHDRAW_FORBIDDEN_SRDS_v2`
- `PAYMENT_CRYPTOBOX_CONTENT_SCENARIO_NOT_ELIGIBLE_v2`

它们不在 3.22.3 的这份 i18n 里。代表键 `ANTI_SCAM_CD_ACCOUNT_GENERIC_1H_LINK_v2` 和 `SCAM_BLACK_ADDRESS_WITHDRAW_FORBIDDEN_v5` 在 3.22.3 / 3.21.6 / 3.20.6 整包都没有。

## 确认新增的开关

没有新的 `*Enabled` 裸键。

## 查询参数

没有。迁移深链没有带出新的 `key=` 或 `dialogType=`。  
`switchLogin` 这个裸词是旧的，新的是路径 `/bapi/accounts/v1/private/authcenter/mirror/switchLogin`。

## 抄进文案表、但裸名是旧的

这些在 3.21.6 和 3.22.3 里已经有，不能写成新字段：

- `mfa-scene-action-pay`
- `mfa-scene-action-withdraw`
- `mfa-scene-action-crypto-box`
- `mfa-scene-action-transfer-web3`
- `mfa-resend-countdown`
- `mfa-verify-scene-tip`

`Resend ({{second}}s)` 这句英文是新的，键名不是。

## 调试字段

`Sell clicked`、`fetchWalletTag failed`、`dWalletConfig providerAppIdMethods size=`、`not opened -> BannerNoFuturesAccount` 是日志或状态串。  
`BannerNoFuturesAccount` 裸名只在这一包，写在 [surface.md](surface.md)，不进字段表。  
R8 签名整段不记。
