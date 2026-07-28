# timestamp-converter — 项目约定

纯前端、单文件的时间戳转换工具。面向人类的说明见 `README.md`；本文件记录**改代码时必须知道的红线与约定**。项目与同级目录 `../json-viewer`、`../xml-viewer` 保持同一套设计与代码风格。

## 红线（不要破坏）

- **单文件、零构建、零依赖**：全部 HTML / CSS / JS 都在 `index.html` 一个文件里。**禁止**引入打包器（Vite/Webpack 等）、框架（React/Vue 等）、npm 依赖或构建步骤。新增能力用原生 JS 实现。
- **纯前端、无后端**：所有解析与转换在浏览器本地完成，不上传任何数据。
- 主题用根元素 `html.dark` 类切换，配色全部走 `:root` / `html.dark` 里的 CSS 变量。新增颜色请复用已有变量，不要硬编码。
- 图标与 logo 保持独立 `favicon.svg`，使用蓝紫渐变 `#2563eb` → `#7c3aed` 圆角方块 + 白色 `ts` 文字。

## 文件结构

- `index.html` — 全部代码（结构 + 样式 + 脚本）。
- `favicon.svg` — 站点图标。
- `.github/workflows/deploy.yml` — GitHub Pages 部署：仓库根即站点根，push 到 `main` 自动部署。
- `README.md` — 面向用户的功能说明与在线访问地址。

## UI 约定

- **按钮文案保持极简**：图标承担表意，文字尽量短（如“暂停”“复制结果”）。
- **工具栏精简**：页头仅保留 GitHub 源码链接与深浅色主题切换，无需导入/URL 按钮。
- 结果卡片统一使用 `.out-card` 样式，带悬停出现的复制按钮。
- 错误与无效状态统一使用红色（`var(--danger)`），提示文案固定为“无法识别的时间戳”。

## 功能约定

- 时间戳解析仅接受整数数字，按长度识别单位：10 位秒、13 位毫秒、16 位微秒、19 位纳秒。
- 相对时间统一输出中文，如“3 天前”“2 小时后”“刚刚”。
- 批量转换结果按 TSV 格式复制（制表符分隔）。
- 主题 localStorage key 固定为 `ts-theme`。

## 在线地址

已部署到 GitHub Pages：https://blog.wangruofeng007.com/timestamp-converter/
