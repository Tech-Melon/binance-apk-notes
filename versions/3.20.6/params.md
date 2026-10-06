# 3.20.6 参数和字段

键名在完整 3.19.8、3.20.1、3.20.3、3.20.5、3.20.6 上做了整包字节搜索（dex + 完整 arsc + assets，UTF-8 和 UTF-16LE）。  
对照的上一包是 Play base 3.20.5。这份是 universal，包装差不当成参数变化。

## 确认新增的产品字段

没有。

## 确认新增的开关

没有。差集里像参数的只有日志键 `color=`，不记。

## 查询参数

没有。也没有新的 `/bapi/`、`https://`、`bnc://`。

4 句只在这一包里的英文（`Can't skip any more tracks` 等）是播放器限制文案，写在 [changelog.md](changelog.md)，不是参数。

## 调试字段

没有。

## 旧键，不要当成新的

3.20.1 的 `isAor`、`direction=IN`，3.20.3 的 `For You(B9)` 和 `ai/landing` 的 `source=`，3.20.5 的 `aorExchangeRate` / `aorOptIn`，在这份完整包里都还在。完整 arsc 把更早版本的译文补了回来，键不是这版新的。
