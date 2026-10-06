# 3.20.6 页面和客户端表面

Manifest 同时对过 Play base 3.20.5 和完整 3.19.8。  
这份是 universal。缺的不是页面，多出来的 so / 中文 / `REQUEST_INSTALL_PACKAGES` 是包装。

## Manifest 新增的 Activity

没有。相对 3.20.5 没有新增，也没有删除。相对完整 3.19.8，也没有「两版都没有、只在 3.20.6 出现」的 Activity。

## 裸类名确认是新的

没有。`MusicBriefingViewModel`、`MusicHistoryViewModel` 在 3.20.3 就有。

## Manifest 去掉的 Activity

没有。

## 域名和依赖

没有新的对外域名。  
`libweb_weave.so`、`libamap_AGenUI.so` 相对完整 3.19.8 是多出来的文件。对应的 Java（`WebWeaveNativeViewController` 从 3.20.1，AGenUI 从 3.20.3）更早。3.20.1–3.20.5 是 Play base，没有 `lib/`，所以 so 不能写成这版新功能。

具名文件里，同时不在 3.20.5、也不在完整 3.19.8 的，只有 `classes28.dex`。

## 这轮没有单独立项的

- 播放器那 4 句英文：见 [changelog.md](changelog.md)
- `res/raw/` 与 eKYC / 人脸模型：完整包从 3.19.8 带回的资源，不是新页面
- 服务端开关的当前值
