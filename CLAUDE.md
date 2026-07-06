# zbisure.github.io — 学习地图（项目约定）

> 给在本仓库工作的 AI agent（Claude Code / Codex）的自包含上下文。
> 关键背景**不依赖任何 memory**——无论从哪个目录开会话，读这份文件即可上手。

## 项目是什么

个人 GitHub Pages 学习站：把学到的主题做成交互式学习页（心智模型 + 可复制模板 + 自测 quiz），持续增补。
线上 <https://zbisure.github.io/>，仓库 `zbisure/zbisure.github.io`，本地 `~/Sites/zbisure.github.io/`。

## Obsidian 存档：在哪里读、在哪里写 ⭐

进度、决策、项目私有文档存在 **Obsidian wiki vault**，不放进 repo：

- **存档目录**：`~/Documents/Obsidian/wiki/40-Projects/zbisure.github.io/`
- **`index.md`** — 项目总览：`status` / `next` / 「现在到哪了」/「接下来做什么」。**开工先读这里**了解进度。
- **`progress.md`** — 倒序工作日志（做了 / 产出 / 决定 / 下一步）。
- **写进度**：用 `project-log` skill 维护 `index.md` + `progress.md`（自动更新状态、写工作日志、保持项目总览 Base）。
  用户说「记录进度 / 同步进度 / 记到 obsidian」时**直接执行**；完成一个大工作块（功能上线、重要决策、长调研收尾）后**主动提议**。
- **知识边界**：项目私有文档留在该文件夹；可复用的通用概念升入 `20-Tech/LLM-WIKI`（走 `llm-wiki-ingest` 流程）。
  首个主题的方法论手册：vault 内 `2026-07-06-finding-unknowns-playbook`。

## 站点内容约定

完整版见仓库 `README.md`。要点：

- **结构**：每主题一个目录 `<topic>/index.html` + 根 `index.html` 卡片列表。
- **HTML 规范**：自包含，不依赖外部 CDN，内联 CSS/JS，适配明暗双主题。
- **视觉语言**：地形图 / 野外手册——纸面底色、等高线装饰、测绘蓝强调色；全部系统字体（Songti SC/Georgia、PingFang SC、SF Mono/Menlo），无外部字体。
- **每页结构**：心智模型 → 可复制模板 → 自测 quiz（通过才算学会）。
- **翻译原则**：界面文案译中文；可复制的**功能性 prompt 保留英文原文 + 加「中文大意」对照**——prompt 是拿来用的，不是拿来读的。

## 加新主题 & 发布

1. 新建 `<topic>/index.html`（按上面 HTML 规范）。
2. 在根 `index.html` 的 `.cards` 里复制注释模板，填编号 / 日期 / 标签 / 标题 / 描述。
3. `git add / commit / push`——Pages 由 GitHub Actions workflow（`.github/workflows/pages.yml`）部署，**push 即自动上线**（实测 ~20s）。

## 本机环境陷阱

- **别裸调 `node`**：非交互 zsh 会触发坏掉的 nvm lazy-load（刷屏 `command not found: _lazy_load_nvm` 后崩溃）。
  用绝对路径 `~/.nvm/versions/node/v22.17.1/bin/node`（v22，原生 fetch/WebSocket）。
- **push 凭据**：gh CLI 已以 `zbisure` 账号 https 登录（`/opt/homebrew/bin/gh`），`git push` 走 gh 凭据助手；未配 SSH key，走 https。
