# 3.20.6 文案

判定「新」：3.18.4 + 3.19.5 + 完整 3.19.8 + 3.20.1 Play base + 3.20.3 Play base + **3.20.5 Play base** 整包（dex + 完整 arsc + assets）UTF-8 / UTF-16LE 都没有。  
本轮扫描包是 universal `BNApp64 (2).apk`。上一版是 Play base，瘦 arsc 里没有的译文 **不等于这一版新写的功能**。

## 确认新增

整包字节搜索确认，下面 4 句只在 3.20.6：

| 原文 | 用途 |
|---|---|
| `Can't skip any more tracks` | 播放器限制：不能再跳过 |
| `Can't do that at the moment` | 当前做不了 |
| `Can't get that content here` | 这里拿不到内容 |
| `This app can't do that` | 这个 App 做不了 |

没有配套的新 Music Activity，也没有 `Binance Music` 整句。`MusicBriefingViewModel` 是 3.20.3 的旧类名。

## 旧文案，不要当成新的

完整 arsc 里大量德/法/西/葡/印尼/日/中文，是 3.20.1–3.20.5 英文功能的译文。英文原句已经在旧包里。

| 原文（英文，旧） | 最早 | 这版多出来的是 |
|---|---|---|
| Quick Backup / `Security Upgrade` / `Restore %d Wallets` | 3.20.5 | 德文、中文「恢复 %d 个钱包」「安全升级」 |
| 美股定投 `Stock recurring buy is now available...` | 3.20.3 | 「股票定投现已上线」及各语言 |
| Benzinga / `Stock Splits History` / DTC | 3.19.5、3.20.1 | EPS、市盈率、分红、拆股的译文 |
| AOR / Agentic Wallet / Hot Wallet / Trade Hub | 3.20.1 | 各语言整句 |
| `Join the Options Competitions and Share 20,000 USDT in Rewards!` | 3.20.1 | 「参加期权竞赛，瓜分 20,000 USDT 奖励！」 |
| `Real-time quotes are available on one device at a time.` | 3.20.5 | 「您的期权报价延迟 15 分钟……」 |
| `Options (Coming soon)` / AI Pro / Dual Identity / `Dina Degen` | 3.17.1 起 | 仍在，不是预告新品 |
| 烟花 / to the moon / `我进场就像放烟花` | 三版完整 arsc 都有 | 完整包能搜到，不是 3.20.6 新句 |

## 没进包

| 在找的 | 结论 |
|---|---|
| `Continue to X` / yellow cloth / under the cloth | 仍没有。`bnc://x` 仍只是短串 |
| 明文 `美股期权` / Covered Call / Cash-Secured Put | 仍没有 |
| `Binance Music` / `Music Briefing` 整句 | 仍没有。类名 `MusicBriefingViewModel` 是 3.20.3 旧的 |
| `secret menu` / `you found` 当彩蛋 | 没有 secret menu。`you found` 是旧包里的子串误报 |
| `/stocks/quiz` / `buzz-appeal-quiz` / Pre-IPO / four.meme | 仍没有 |
