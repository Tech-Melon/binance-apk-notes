# 3.22.3 接口

Host：`https://www.binance.com`  
头：`Accept: application/json`，`lang: en`，`clienttype: android`，`User-Agent: Binance/3.22.3 (Android)`

路径来自 dex + 瘦 arsc + 小配置 assets 的差集，再在旧包里做整文件字节搜索。215 条 `/bapi/` 在 3.18.4 到 3.21.6 都没有。没有 3.21.7–3.22.2。

写操作和 `cancel` 没有打。private 未登录按 `100001005` 理解。

## 实打

| 方法 | 路径 | 鉴权 | 含义 | 实打 |
|---|---|---|---|---|
| GET | `/bapi/equity/v1/public/equity/option/get-config` | public | 美股期权客户端配置 | 200 `000000`。`closeOnlyMinutes=45`，`liquidationPeriod=30` |
| GET | `/bapi/c2c/v1/public/c2c/helpCenter/videos` | public | P2P 帮助视频 | 200 `000000`。样例 `WHAT_IS_P2P_TRADING`、`HOW_TO_BUY`，后面还有 4 条 |
| GET | `/bapi/c2c/v1/public/c2c/share/config` | public | 分享口令规则 | 200 `000000`。`matchRegex` 用货币符号夹 11 位字符，`delimiters` 有 `€`、`₤` 等 |
| GET | `/bapi/c2c/v1/public/c2c/express/get-fiat-channel` | public | 法币充值通道 | 200 `000000`。样例 `EUR`、`BRL`，`flow=deposit`，深链 `/funds/fiatDeposit?asset=`，后面还有 3 条 |
| GET | `/bapi/c2c/v1/friendly/c2c/ai-assistant/config` | public | P2P AI 助手位 | 200 `000000`。`position` 是空数组 |
| GET | `/bapi/bigdata/v1/private/bigdata/strategy/app/aipro/version` | 要登录 | AI Pro 策略版本 | 401 `100001005 Please log in first.` |
| GET | `/bapi/bigdata/v1/private/bigdata/strategy/app/more` | 要登录 | AI Pro 策略更多 | 401 `100001005` |
| GET | `/bapi/defi/v1/public/wallet-direct/buw/wallet/token/is-stable-or-native` | public | 是否稳定币或原生币 | 400 `000002`。空参和 `symbol=BTC` 都缺参数 |
| GET | `/bapi/defi/v1/public/wallet-direct/tracker/wallet/discover/home-callout-summary` | public | 钱包发现页摘要 | 400 `000002` |
| GET | `/bapi/c2c/v1/public/c2c/express/get-trading-options` | public | P2P Express 交易选项 | 400 `000002` |
| GET | `/bapi/c2c/v1/friendly/c2c/banner/list` | public | P2P banner | 400 `000002` |
| GET | `/bapi/c2c/v1/friendly/c2c/trade-rule/info` | public | 交易规则 | 400 `000002` |
| GET | `/bapi/c2c/v2/public/c2c/adv/filter-conditions` | public | 广告筛选条件 | 400 `000002` |
| GET | `/bapi/c2c/v1/public/c2c/sys-config/get-tips-config` | public | 提示配置 | 400 `000002` |
| GET | `/bapi/c2c/v1/public/c2c/adv/launch-country/country-match-enabled` | public | 上架国家是否匹配 | 400 `000002` |

`/bapi/earn/v1/private/earn/btcy/user/redeem/cancel`、`/bapi/futures/v1/private/future/order/cancel-all-orders`、两条 OTC `cancel-all-order` 是写操作或撤单，没有打。

antibot 那行 JS 从 `var apiBasePath = '/bapi/composite/v1/public/antibot'` 变成带三元表达式的写法。路径本身不是新的。

## 全量新 /bapi/

下面每条都在旧包字节搜索里确认过。private 未登录按 `100001005` 理解。

AI Pro：

- `/bapi/bigdata/v1/private/bigdata/strategy/app/aipro/version`
- `/bapi/bigdata/v1/private/bigdata/strategy/app/more`

钱包：

- `/bapi/defi/v1/public/wallet-direct/buw/wallet/token/is-stable-or-native`
- `/bapi/defi/v1/public/wallet-direct/tracker/wallet/discover/home-callout-summary`

Earn、期权、撤单：

- `/bapi/earn/v1/private/earn/btcy/user/redeem/cancel`
- `/bapi/equity/v1/public/equity/option/get-config`
- `/bapi/futures/v1/private/future/order/cancel-all-orders`
- `/bapi/margin/v1/private/new-otc/limit/cancel-all-order`
- `/bapi/margin/v1/private/new-otc/tp-sl/cancel-all-order`
- `/bapi/margin/v1/private/new-otc/tp-sl/open-orders`

C2C / P2P，205 条：

- `/bapi/c2c/v1/friendly/c2c/adv/fetch-tags-refresh-time-for-express`
- `/bapi/c2c/v1/friendly/c2c/ai-assistant/config`
- `/bapi/c2c/v1/friendly/c2c/banner/list`
- `/bapi/c2c/v1/friendly/c2c/commission-rate/taker`
- `/bapi/c2c/v1/friendly/c2c/review/list-by-page`
- `/bapi/c2c/v1/friendly/c2c/review/user-review-statistics`
- `/bapi/c2c/v1/friendly/c2c/trade-rule/fiat-list`
- `/bapi/c2c/v1/friendly/c2c/trade-rule/info`
- `/bapi/c2c/v1/friendly/c2c/user/is-agreement-disclaimer-required`
- `/bapi/c2c/v1/private/binance-chat/message/translate`
- `/bapi/c2c/v1/private/c2c/additional-kyc-verify/check-liveness-and-process`
- `/bapi/c2c/v1/private/c2c/additional-kyc-verify/get-additional-kyc-verify-config`
- `/bapi/c2c/v1/private/c2c/additional-kyc-verify/get-order-additional-kyc-verify-info`
- `/bapi/c2c/v1/private/c2c/adv-order/updateAdvListStatus`
- `/bapi/c2c/v1/private/c2c/adv/additional-kyc/query-exempted-config`
- `/bapi/c2c/v1/private/c2c/adv/commission-rate`
- `/bapi/c2c/v1/private/c2c/adv/getAdvPayTimeConfig`
- `/bapi/c2c/v1/private/c2c/adv/option-config`
- `/bapi/c2c/v1/private/c2c/adv/payment-alert/add`
- `/bapi/c2c/v1/private/c2c/adv/publish-eligibility-check`
- `/bapi/c2c/v1/private/c2c/adv/risk-check`
- `/bapi/c2c/v1/private/c2c/adv/tags-config-fetch`
- `/bapi/c2c/v1/private/c2c/asset/balance`
- `/bapi/c2c/v1/private/c2c/asset/get-user-assets-to-btc`
- `/bapi/c2c/v1/private/c2c/banner/prohibit`
- `/bapi/c2c/v1/private/c2c/chat/common/quick-reply`
- `/bapi/c2c/v1/private/c2c/chat/file/pre-upload`
- `/bapi/c2c/v1/private/c2c/chat/get-risk-warning-hints`
- `/bapi/c2c/v1/private/c2c/chat/img/pre-upload`
- `/bapi/c2c/v1/private/c2c/chat/ping-by-type`
- `/bapi/c2c/v1/private/c2c/chat/ping-chat-stream`
- `/bapi/c2c/v1/private/c2c/chat/translation/auto-enable-eligible`
- `/bapi/c2c/v1/private/c2c/chat/translation/languages`
- `/bapi/c2c/v1/private/c2c/chat/video/pre-upload`
- `/bapi/c2c/v1/private/c2c/complaint/cancel/`
- `/bapi/c2c/v1/private/c2c/complaint/escalate`
- `/bapi/c2c/v1/private/c2c/complaint/flow-infos/`
- `/bapi/c2c/v1/private/c2c/complaint/initiate`
- `/bapi/c2c/v1/private/c2c/complaint/initiate/can`
- `/bapi/c2c/v1/private/c2c/complaint/list/`
- `/bapi/c2c/v1/private/c2c/complaint/listAllComplaintReasons`
- `/bapi/c2c/v1/private/c2c/complaint/negotiate`
- `/bapi/c2c/v1/private/c2c/complaint/provide-info`
- `/bapi/c2c/v1/private/c2c/complaint/risk-check`
- `/bapi/c2c/v1/private/c2c/complaint/self-service/flow-infos`
- `/bapi/c2c/v1/private/c2c/dispute/report`
- `/bapi/c2c/v1/private/c2c/dispute/report/counterparty-order-list`
- `/bapi/c2c/v1/private/c2c/dispute/report/query-reason`
- `/bapi/c2c/v1/private/c2c/dispute/report/query-template`
- `/bapi/c2c/v1/private/c2c/dispute/validate`
- `/bapi/c2c/v1/private/c2c/file-upload/s3-antivirus-presigned-url`
- `/bapi/c2c/v1/private/c2c/file-upload/s3-transcoding-presigned-url`
- `/bapi/c2c/v1/private/c2c/marketplace/goods/publish-permission-check`
- `/bapi/c2c/v1/private/c2c/marketplace/report/counterparty-order-list`
- `/bapi/c2c/v1/private/c2c/marketplace/report/query-reason`
- `/bapi/c2c/v1/private/c2c/marketplace/report/submit`
- `/bapi/c2c/v1/private/c2c/marketplace/report/validate`
- `/bapi/c2c/v1/private/c2c/merchant/endRest`
- `/bapi/c2c/v1/private/c2c/merchant/get-exchange-rate-list`
- `/bapi/c2c/v1/private/c2c/merchant/info`
- `/bapi/c2c/v1/private/c2c/merchant/recommended-list-private-trade`
- `/bapi/c2c/v1/private/c2c/merchant/startBussiness`
- `/bapi/c2c/v1/private/c2c/merchant/startRest`
- `/bapi/c2c/v1/private/c2c/notification-configuration/user/get`
- `/bapi/c2c/v1/private/c2c/notification-configuration/user/update`
- `/bapi/c2c/v1/private/c2c/order-dispute/query`
- `/bapi/c2c/v1/private/c2c/order-match/additional-kyc/verify`
- `/bapi/c2c/v1/private/c2c/order-match/cancel-check`
- `/bapi/c2c/v1/private/c2c/order-match/cancelOrder`
- `/bapi/c2c/v1/private/c2c/order-match/check-unread-messages`
- `/bapi/c2c/v1/private/c2c/order-match/confirm-check`
- `/bapi/c2c/v1/private/c2c/order-match/confirm-order-payed`
- `/bapi/c2c/v1/private/c2c/order-match/convert-order-list`
- `/bapi/c2c/v1/private/c2c/order-match/get-express-optimal-adv-amount`
- `/bapi/c2c/v1/private/c2c/order-match/get-order-status-and-add-kyc`
- `/bapi/c2c/v1/private/c2c/order-match/get-trade-complete-times`
- `/bapi/c2c/v1/private/c2c/order-match/getCounterpartyCertifiedInfo/`
- `/bapi/c2c/v1/private/c2c/order-match/getUserUndoOrderNumbers`
- `/bapi/c2c/v1/private/c2c/order-match/multipleOrderCheck`
- `/bapi/c2c/v1/private/c2c/order-match/notify-payment-proof`
- `/bapi/c2c/v1/private/c2c/order-match/notifyOrderPayed`
- `/bapi/c2c/v1/private/c2c/order-match/order-cancel-reasons`
- `/bapi/c2c/v1/private/c2c/order-match/order-list-user-trade`
- `/bapi/c2c/v1/private/c2c/order-match/order-list-with-unread-message`
- `/bapi/c2c/v1/private/c2c/order-match/pay-time-limit/confirm-extend`
- `/bapi/c2c/v1/private/c2c/order-match/pay-time-limit/query-extend`
- `/bapi/c2c/v1/private/c2c/order-match/pre-place-order-page-info`
- `/bapi/c2c/v1/private/c2c/order-match/query-scope-config`
- `/bapi/c2c/v1/private/c2c/order-match/tips`
- `/bapi/c2c/v1/private/c2c/order-match/tips-with-highlight-words`
- `/bapi/c2c/v1/private/c2c/order-match/virtual-number`
- `/bapi/c2c/v1/private/c2c/payment/online/entry`
- `/bapi/c2c/v1/private/c2c/payment/online/query`
- `/bapi/c2c/v1/private/c2c/payment/online/query-external`
- `/bapi/c2c/v1/private/c2c/payment/online/verify-account`
- `/bapi/c2c/v1/private/c2c/payment/online/verify-account-status`
- `/bapi/c2c/v1/private/c2c/reminder/delete`
- `/bapi/c2c/v1/private/c2c/reminder/edit`
- `/bapi/c2c/v1/private/c2c/reminder/query`
- `/bapi/c2c/v1/private/c2c/reminder/submit`
- `/bapi/c2c/v1/private/c2c/reminder/submit-check`
- `/bapi/c2c/v1/private/c2c/review/detail`
- `/bapi/c2c/v1/private/c2c/review/order-review`
- `/bapi/c2c/v1/private/c2c/review/remove`
- `/bapi/c2c/v1/private/c2c/review/reply-comment`
- `/bapi/c2c/v1/private/c2c/review/review`
- `/bapi/c2c/v1/private/c2c/review/review-auth-config`
- `/bapi/c2c/v1/private/c2c/review/review-comment-tag-stat`
- `/bapi/c2c/v1/private/c2c/scam-notification/check`
- `/bapi/c2c/v1/private/c2c/share/adv-search-share`
- `/bapi/c2c/v1/private/c2c/share/adv-share`
- `/bapi/c2c/v1/private/c2c/share/advertiser-share`
- `/bapi/c2c/v1/private/c2c/swap/average-convert-price`
- `/bapi/c2c/v1/private/c2c/swap/config`
- `/bapi/c2c/v1/private/c2c/swap/confirm`
- `/bapi/c2c/v1/private/c2c/swap/pre-check`
- `/bapi/c2c/v1/private/c2c/sys-config/adv-trans-amount-limit`
- `/bapi/c2c/v1/private/c2c/sys-config/getMessageParams/`
- `/bapi/c2c/v1/private/c2c/sys-config/multi-lang/text/query`
- `/bapi/c2c/v1/private/c2c/task-center/get-eligible-task`
- `/bapi/c2c/v1/private/c2c/task-center/has-completed-task`
- `/bapi/c2c/v1/private/c2c/trade-rule/adv-rules`
- `/bapi/c2c/v1/private/c2c/user-follower/count`
- `/bapi/c2c/v1/private/c2c/user-follower/count/third-party`
- `/bapi/c2c/v1/private/c2c/user-follower/follower-list`
- `/bapi/c2c/v1/private/c2c/user-follower/following-list`
- `/bapi/c2c/v1/private/c2c/user-follower/recommendation-list`
- `/bapi/c2c/v1/private/c2c/user-follower/update`
- `/bapi/c2c/v1/private/c2c/user/counter-party-chat-restriction/query`
- `/bapi/c2c/v1/private/c2c/user/disclaimer-accept`
- `/bapi/c2c/v1/private/c2c/user/is-new-user-onboarding`
- `/bapi/c2c/v1/private/c2c/user/profile`
- `/bapi/c2c/v1/private/c2c/user/quiz/request`
- `/bapi/c2c/v1/private/c2c/user/quiz/submit`
- `/bapi/c2c/v1/private/c2c/user/user-restriction/query`
- `/bapi/c2c/v1/private/c2c/user/user-suspension/query`
- `/bapi/c2c/v1/private/c2c/useradalert/addAlertPreCheck`
- `/bapi/c2c/v1/private/c2c/useradalert/addUserAdAlert`
- `/bapi/c2c/v1/private/c2c/useradalert/getAdQuotePrice`
- `/bapi/c2c/v1/private/c2c/useradalert/queryUserAdAlert`
- `/bapi/c2c/v1/private/c2c/useradalert/removeUserAdAlert`
- `/bapi/c2c/v1/public/c2c/adv/launch-country/country-match-enabled`
- `/bapi/c2c/v1/public/c2c/express/get-fiat-channel`
- `/bapi/c2c/v1/public/c2c/express/get-trading-options`
- `/bapi/c2c/v1/public/c2c/helpCenter/videos`
- `/bapi/c2c/v1/public/c2c/share/config`
- `/bapi/c2c/v1/public/c2c/share/shared-adv`
- `/bapi/c2c/v1/public/c2c/sys-config/get-tips-config`
- `/bapi/c2c/v1/public/c2c/sys-config/quick-comment-tags`
- `/bapi/c2c/v1/public/c2c/sys-config/seller-cancel-reason-fiats`
- `/bapi/c2c/v1/public/c2c/sys-config/seller-cancel-reason-ttl`
- `/bapi/c2c/v1/public/c2c/trade-rule/asset-list`
- `/bapi/c2c/v1/public/c2c/trade-rule/valid-asset-list`
- `/bapi/c2c/v2/friendly/c2c/adv/privilege-adv`
- `/bapi/c2c/v2/friendly/c2c/adv/search`
- `/bapi/c2c/v2/friendly/c2c/portal/config`
- `/bapi/c2c/v2/friendly/c2c/user/profile-and-ads-list`
- `/bapi/c2c/v2/private/c2c/adv/adv-base-config`
- `/bapi/c2c/v2/private/c2c/adv/detail`
- `/bapi/c2c/v2/private/c2c/adv/is-confirm-required`
- `/bapi/c2c/v2/private/c2c/adv/list-by-page`
- `/bapi/c2c/v2/private/c2c/adv/publish-check`
- `/bapi/c2c/v2/private/c2c/adv/publish-eligibility-check`
- `/bapi/c2c/v2/private/c2c/adv/selected-by-number-list`
- `/bapi/c2c/v2/private/c2c/adv/update-status`
- `/bapi/c2c/v2/private/c2c/adv/update-trade-methods`
- `/bapi/c2c/v2/private/c2c/adv/update-trade-methods-eligibility-check`
- `/bapi/c2c/v2/private/c2c/blacklist/getReasons`
- `/bapi/c2c/v2/private/c2c/chat/exit-chat`
- `/bapi/c2c/v2/private/c2c/chat/mark-user-message-read`
- `/bapi/c2c/v2/private/c2c/chat/query-chat-by-page`
- `/bapi/c2c/v2/private/c2c/chat/sync-order-data`
- `/bapi/c2c/v2/private/c2c/order-match/can-seller-reason-cancel`
- `/bapi/c2c/v2/private/c2c/order-match/cancelOrder`
- `/bapi/c2c/v2/private/c2c/order-match/check-can-remind-counter-party`
- `/bapi/c2c/v2/private/c2c/order-match/check-cancel-order`
- `/bapi/c2c/v2/private/c2c/order-match/check-force-complete`
- `/bapi/c2c/v2/private/c2c/order-match/checkMakeOrder`
- `/bapi/c2c/v2/private/c2c/order-match/confirm-hit-buyer-name`
- `/bapi/c2c/v2/private/c2c/order-match/confirm-validate-buyer-name`
- `/bapi/c2c/v2/private/c2c/order-match/decide-seller-cancel`
- `/bapi/c2c/v2/private/c2c/order-match/force-cancel`
- `/bapi/c2c/v2/private/c2c/order-match/force-release`
- `/bapi/c2c/v2/private/c2c/order-match/get-top-ranked-optimal-order-prices`
- `/bapi/c2c/v2/private/c2c/order-match/order-tips`
- `/bapi/c2c/v2/private/c2c/order-match/remind-counter-party`
- `/bapi/c2c/v2/private/c2c/order-match/user-order-stats`
- `/bapi/c2c/v2/private/c2c/pay-method/add`
- `/bapi/c2c/v2/private/c2c/pay-method/add-check`
- `/bapi/c2c/v2/private/c2c/pay-method/delete/`
- `/bapi/c2c/v2/private/c2c/pay-method/detail/`
- `/bapi/c2c/v2/private/c2c/pay-method/iin`
- `/bapi/c2c/v2/private/c2c/pay-method/seller-payable-paymethod`
- `/bapi/c2c/v2/private/c2c/pay-method/update`
- `/bapi/c2c/v2/private/c2c/pay-method/user-paymethods`
- `/bapi/c2c/v2/private/c2c/trade-method/detail/`
- `/bapi/c2c/v2/private/c2c/trade-rule/adv-rules`
- `/bapi/c2c/v2/private/c2c/user/share-ads-and-profile`
- `/bapi/c2c/v2/public/c2c/adv/detail-with-advertiser`
- `/bapi/c2c/v2/public/c2c/adv/filter-conditions`
- `/bapi/c2c/v2/public/c2c/adv/quoted-price`
- `/bapi/c2c/v2/public/c2c/trade-method/list-by-page`
- `/bapi/c2c/v2/public/c2c/trade-method/list-online-identifiers`
- `/bapi/c2c/v3/private/c2c/adv/publish`
- `/bapi/c2c/v3/private/c2c/adv/update`

## 客户端里消失的旧路径

这些精确字符串不在 3.22.3。不等于产品下线。

3.20.6 和 3.21.6 都有：

- `/bapi/apex/v1/public/apex/market/holiday-atmosphere`
- `/bapi/mp/gc/tenant/v2/private/leaderboards/`
- `/bapi/mp/v3/tenant/apps/qrcode/get-content`

只在 3.21.6、3.20.6 完整包里没有、这一包也没有：

- `/bapi/defi/v1/private/wallet-direct/buw/alpha-event/competition/query`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/pool/detail`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/pool/statistics`
- `/bapi/defi/v1/private/wallet-earn/simple/yield/token/info`
- `/bapi/defi/v1/public/wallet-direct/buw/wallet/ai-widget/hot-zone/config`
- `/bapi/defi/v1/public/wallet-direct/buw/wallet/ai-widget/query`
- `/bapi/defi/v4/private/wallet-earn/simple/yield/protocol/list`
