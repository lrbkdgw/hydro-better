# hydro-better

一个 Hydro 站点的篡改猴（Tampermonkey / Violentmonkey / Userscripts）美化脚本。

- 站点：`https://zsoj.gbfish.cn/`（以及脚本头部 `@match` 里的其它 Hydro 站点）
- 当前版本：**v1.8.0**
- 脚本文件：`Hydro-UI-Beautifier.user.js`
- 历史版本：`versions/Hydro-UI-Beautifier-<版本号>.user.js`

## 安装

推荐用「从 URL 安装」，这样脚本管理器自己也能帮你检查更新：

```
https://raw.githubusercontent.com/lscminxi/hydro-better/main/Hydro-UI-Beautifier.user.js
```

- Tampermonkey：仪表盘 → 实用工具 → 「从 URL 安装」→ 粘贴上面的地址。
- Violentmonkey：设置 → 「从 URL 安装」。
- 或者直接打开上面的地址，脚本管理器会自动弹出安装页。

首次本地安装的话，打开 `Hydro-UI-Beautifier.user.js` 把内容复制进「新建脚本」也可以，但那样脚本管理器不认识更新源，只能依赖脚本内置的更新检测（见下）。

## v1.8.0 更新内容

1. **自动更新检测**
   - 脚本会读取本仓库 `main` 分支上脚本头部的 `@version`（每 6 小时最多检查一次，只发一个 `raw` 请求，失败不影响使用）。
   - 有新版时：右下角悬浮按钮上出现红点，设置面板标题显示「有新版本 vX.Y.Z」，并弹一次提示。
   - 设置面板「诊断/配置 → 自动更新」可以：立即检查更新、安装新版本（打开脚本地址交给管理器接管）、打开 GitHub 仓库、复制脚本地址。
   - 检查结果与上次检查时间缓存在 `localStorage` 的 `hydro_beautifier_update` 里。
   - 脚本头部已补上 `@updateURL` / `@downloadURL`，所以从 URL 安装后 Tampermonkey 自身的自动更新也会生效。
2. **代码块改为不透明**
   - `pre` / `pre > code` 使用实色背景（深色 `#1b2030`，浅色卡片下 `#f6f8fc`），不再让背景图和半透明卡片透过来。
   - 自动跳过程序坞 / Monaco / CodeMirror / 设置面板里的编辑器，不会染指评测机代码框。
   - 消息页面里的代码块同样生效。

## 发布新版本（维护者）

1. 修改 `Hydro-UI-Beautifier.user.js`：同时更新脚本头 `// @version` 和代码里的 `const VERSION`。
2. 复制一份到 `versions/Hydro-UI-Beautifier-<新版本号>.user.js` 留档。
3. 提交并推送到 `main`。用户端下一次检查（或打开页面 2.5 秒后）即可看到更新提示。

## 说明

所有配置只保存在当前站点的浏览器本地，不会修改 Hydro 服务端数据。
