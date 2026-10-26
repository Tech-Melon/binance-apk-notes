# 3.22.4 相对 3.22.3

对照：`币安 3.22.3.apk`（Play base）→ `币安 3.22.4.apk`（Play base）。  
「这句是新的」在 3.18.4 / 3.19.5 / 完整 3.19.8 / 3.20.1 / 3.20.3 / 3.20.5 / 3.20.6 / 3.21.6 / **3.22.3** 上整包对过（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
**两边包装相同。** 文件差集可以当产品候选。相对 3.20.6 universal 缺 so / 缺中文仍是包装。  
`versionCode` 从 `100302203` 到 `100302204`。

## 产品

1. **巴西站合约迁到 ADGM 国际账户**  
   文案写明：按巴西新规，**2026-10-30** 起合约要挪到单独的 ADGM 国际账户。没有就在同意时建一个。ADGM 是文案里的缩写，通常指阿布扎比全球市场。  
   主标题 `Futures Account Migration`。按钮 `Agree and Migrate`、`Confirm Migration`，也可以 `Stay in Brazil`。另有 `Acknowledge & Switch account`。  
   迁的时候仓位冻结，不能交易、平仓、减仓或划转。未成交的限价和止损限价会取消，要在新账户重下。持仓和保证金会自动转到新建的 ADGM 账户及子账户。未实现盈亏和开仓价保持不变。现货和其他产品不动。开始之后不能撤销。  
   当前巴西账户上的合约 API 权限会拿掉，迁移后要在 ADGM 账户重新建 API key。账户之间可以随时互转。  
   历史仍留在当前 Binance Brasil 账户。波动可能导致迁移刚结束就被强平，文案写明币安不为此负责。  
   没迁完、仍留在巴西账户上的合约仓位，要自己平掉或转走。另一句是：合约此后只在 ADGM 国际账户可交易，去 Profile 开通或切换。  
   新类 `FuturesBrMigrationRepository`、`FuturesBrMigrationBillboard`、`FuturesBrMigrationBubble`、`FuturesComplianceRepository`。  
   小程序插件 `com.binance.android.nezha.plugin.mirrorAccount.MirrorAcountPlugin`。类名就是少了一个 c。  
   状态串 `BannerNoFuturesAccount` 只在这一包，不是新的 Manifest Activity。  
   四条迁移接口和一条 AI 落地页分享链接都要登录，见 [apis.md](apis.md)。
2. **美股费用没结清，会冻住 BTC 提现**  
   `{0} BTC is currently unavailable for withdrawal due to pending U.S. stock trading processing fees or collateral requirements.`  
   中文：`由于美股交易处理费或抵押品要求尚未结清，{0} BTC 暂时无法提现。`  
   另一句：`Funds are frozen due to U.S. stock trading requirement` / `由于美股交易要求，资金已被冻结`。  
   键 `WITHDRAW_STOCKS_OTHER_FEE_FREEZE_AMOUNT_v1`、`INFO_STOCKS_OTHER_FEE_FREEZE_AMOUNT_v1`、`MSG_STOCKS_OTHER_FEE_FREEZE_AMOUNT_v1`。  
   3.22.3 的正股可买和期权适当性评估还在。这是提现侧的限制句，不是新的交易页。
3. **聊天室三条警告，以及一批反诈提现文案**  
   内置小程序 `mp-bids-mfa-ui`（id `cH6sYTb5RTJEkpuwrbn7zm`，描述是 risk challenge）的英 / 中 / 俄文案表各多 37 个键，一个旧键改了措辞。  
   聊天室警告只提醒，不立刻限制功能。原因三选一：向别人要钱、乞讨或募资；持续垃圾信息和无理由互动；给其他用户推第三方频道或付费服务。再犯可能临时禁言或限制互动。标题键 `BINANCE_CHAT_GENERAL_WARNING_TITLE_v1`，正文三键见 [params.md](params.md)。  
   反诈提现是同一张表里的新键：仿冒网站、欺诈地址、同 gas 来源、曾经转过欺诈地址后再被「专家」二次收割。多条写明可签风险披露后继续提现，也有写明限制不能手动解除。  
   旧键 `SCAM_BLACK_ADDRESS_WITHDRAW_FORBIDDEN_v3` 改了一处英文措辞，从 `withdrawals from your account have been temporarily restricted` 变成 `making withdrawals from your account has been temporarily restricted`。键名不是新的。  
   红包：检测到自动化或频繁领取就领不了；合约红包在账户有可疑活动时直接关掉领取。  
   `LINK_REDIRECT_WITHDRAW_NEW`：提现如果不是本人发起，当短信或邮件钓鱼，不要点链接、不要给验证码。确认是本人就 10 分钟后再试。
4. **网页端和桌面端扫码登录的确认句**  
   `Confirm this is you logging in on the web.` / `Log in to Binance Web`  
   `Confirm this is you logging in on the desktop.` / `Log in to Binance Desktop`  
   中文是「请确认是您本人在网页端登录」「登录币安网页端」，桌面端同一套。  
   键 `accounts-qr-login-tips-low-web`、`accounts-qr-login-title-low-web`，以及 `low-electron` 两条。  
   `mfa-scene-action-pay`、`mfa-scene-action-withdraw`、`mfa-resend-countdown` 这些键 3.21.6 就有，只是被抄进这份文案表。英文整句 `Resend ({{second}}s)` 这一包才有。
5. **资产快照多了一句**  
   `As of %1$s, your total asset value was %2$s %3$s, with a 24-hour change of %4$s (approximately %5$s).`  
   只在这一包。没有对应的新 Activity，不另起产品名。

## 从包里去掉的字符串

Manifest 相对 3.22.3 **没有**少 Activity，也没有新 Activity。

`https://app.binance.com/uni-qr/report-landing` 在 3.22.3 有，这一包没有。3.21.6 和 3.20.6 也都没有。它只在上一版的包里待过一版。没有对应的 `/bapi/` 被删掉。

## 基础设施

- 小程序运行时仍 **5.16.4**。三个内置 MP id 不变。
- `mp-bids-mfa-ui` 的 i18n、css、qjs、jwt CRC 变了。另外两个 MP 只变了 jwt，不当产品。
- Flutter package 仍 15。没有新的具名资源文件。
- 权限相对 3.22.3 **无增减**。相对 3.20.6 少 `REQUEST_INSTALL_PACKAGES`，是包装。
- `res/raw/` 相对 3.22.3 大约 421 增、415 删，哈希文件名轮换。
- `META-INF/services/` 三个混淆类名对调，是 R8，不是新服务。
- DEX 全量 CRC 会变，是 R8 重打包，不当成业务重写。
- 没有新的 `lib/arm64-v8a`。两边 so 都是 0。

参数见 [params.md](params.md)。类名见 [surface.md](surface.md)。接口见 [apis.md](apis.md)。
