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

**内容规范的唯一出处是 `CONTENT-SPEC.md`**（冻结层 / 自由层 / 非目标 / 站点级不变量），新页一律从 `_template/index.html` 复制起步。速记：

- **结构**：每主题一个目录 `<topic>/index.html` + 根 `index.html` 卡片列表。
- **HTML 规范**：自包含单文件，不依赖外部 CDN，内联 CSS/JS，明暗双主题（系统偏好 + 右上角手动切换）。
- **视觉语言**：地形图 / 野外手册——纸面底色、等高线装饰、测绘蓝强调色；全部系统字体（Songti SC/Georgia、PingFang SC、SF Mono/Menlo），无外部字体。
- **每页骨架**：hero → §1 心智模型 → 正文（形态自由）→ 来源书架（一手来源带日期）→ 自测 quiz（末节，全对才过）→ footer 返回主页。可复制模板是**自由层**（可选）。
- **翻译原则**：界面文案译中文；**外来英文 prompt 保留原文 + 「中文大意」对照**——prompt 是拿来用的，不是拿来读的；自产中文模板直接中文，无需对照。
- **数字与链接**：quiz 题数只写在 JS `QS` 数组里（导航/计分条由 JS 填充）；站内一律相对路径；提及站内页面必须真链接，姊妹篇双向互链。

## 加新主题 & 发布

1. 复制 `_template/index.html` 为 `<topic>/index.html`，按 `CONTENT-SPEC.md` 填内容。
2. 在根 `index.html` 的 `.cards` 里复制注释模板，填编号 / 日期 / 标签 / 标题 / 描述。
3. **跑完下面的发布前检查清单**，再 `git add / commit / push`——Pages 由 GitHub Actions workflow（`.github/workflows/pages.yml`）部署，**push 即自动上线**（实测 ~20s）。

## 发布前检查清单（新页与改动存量页都要跑）

1. 本地 `file://` 打开正常——说明站内没有绝对 URL、相对路径没断。
2. 明暗两主题都过目（含右上角手动切换），移动宽度（≤600px）过目。
3. quiz 三条路径跑通：答对、答错（有「重读 §X →」锚点）、重置重考；题数各处显示一致。
4. 复制按钮实际复制成功。
5. 外链逐个可达；一手来源带日期；来源书架收全了本页一手来源。
6. 主页卡片与页面事实核对（编号 / 日期 / 标签 / 描述，尤其里面的数字）。
7. push 后线上 URL 实测 200。

## 本机环境陷阱

- **别裸调 `node`**：非交互 zsh 会触发坏掉的 nvm lazy-load（刷屏 `command not found: _lazy_load_nvm` 后崩溃）。
  用绝对路径 `~/.nvm/versions/node/v22.17.1/bin/node`（v22，原生 fetch/WebSocket）。
- **push 凭据**：gh CLI 已以 `zbisure` 账号 https 登录（`/opt/homebrew/bin/gh`），`git push` 走 gh 凭据助手；未配 SSH key，走 https。
