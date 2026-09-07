# 我的路书 · 多用户版(建站包)

一个纯静态 PWA:`index.html` 一个文件包含全部界面与逻辑,配合腾讯云开发(CloudBase)做登录与路书存储,地图用高德 Web JS API。

## 文件

- `index.html` — 应用本体(登录、我的路书、总览地图、编辑器、分享、个人信息)
- `manifest.json` — PWA 清单(名称、图标、启动方式)
- `icon-180/192/512.png`、`favicon-32.png` — 图标

## 本地预览

任意静态服务器即可,例如:

```bash
python3 -m http.server 8080
# 浏览器打开 http://localhost:8080
```

不要用 `file://` 直接打开 —— manifest 和部分接口需要 http(s)。

## 部署到 GitHub Pages

1. 新建仓库(公开或私有均可,Pages 需要公开或付费计划)。
2. 把本目录内所有文件放到仓库根目录,推送到 `main`。
3. 仓库 Settings → Pages → Source 选 `Deploy from a branch`,Branch 选 `main` / `(root)`,保存。
4. 一两分钟后访问 `https://<用户名>.github.io/<仓库名>/`。
5. 手机 Safari 打开该网址 → 分享 → **添加到主屏幕**,即可像 App 一样全屏使用。

> 注意:部署在子路径时,`manifest.json` 里的 `start_url` / `scope` 用的是相对路径(`./`),无需改动。

## 上线前必做的两件事

1. **高德 key**:在高德开放平台申请 *Web 端(JS API)* key + 安全密钥,并在控制台把域名加入白名单。
2. **数据隔离**:在云开发控制台把路书集合的权限设为「仅创建者可读写」,否则默认规则可能允许他人读取你的行程与备注。分享链接依赖随机 token,请勿把 token 写进公开页面。

## 相关设计稿

同项目里的 `路书 App.dc.html` 是 iOS 版界面与交互原型(时间轴 / 地图 / 卡片三种编排视图、沿途搜索、导航接力、路书广场、分享导出),用于指导本包后续改版。
