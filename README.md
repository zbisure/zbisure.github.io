# zbisure.github.io — 学习地图

交互式学习页合集，托管在 GitHub Pages：<https://zbisure.github.io/>

## 结构

```
index.html            # 学习主页（主题卡片列表）
CONTENT-SPEC.md       # 学习页内容规范（冻结层/自由层/非目标）——唯一出处
_template/index.html  # 新页工程脚手架（token、quiz 引擎、主题切换、复制按钮已内置）
unknowns/index.html   # 01 · 未知项野外指南（Finding Your Unknowns）
unknowns/demos/       # Thariq 11 个交互演示页的中文译版（01–11）
agentic/              # 02 · Agentic 开发作战手册
loop-engineering/     # 03 · 循环工程野外手册
agentic-way/          # 04 · Agentic 之道·正本清源
```

## 增加新学习主题

1. 复制 `_template/index.html` 为 `<topic>/index.html`，按 `CONTENT-SPEC.md` 填内容
2. 在根 `index.html` 的 `.cards` 里复制注释中的卡片模板，填上编号、日期、标签、标题和描述
3. 跑完 `CLAUDE.md` 里的发布前检查清单，提交并 push，Pages 自动部署

## 设计约定

细则见 `CONTENT-SPEC.md`。速记：

- 视觉语言：地形图/野外手册——纸面底色、等高线装饰、测绘蓝强调色
- 字体：衬线显示（Songti SC/Georgia）+ 无衬线正文（PingFang SC）+ 等宽（SF Mono/Menlo），全部系统字体，无外部字体
- 每页骨架：心智模型 → 正文（可复制模板为可选自由层）→ 来源书架（一手来源带日期）→ 自测 quiz（通过才算学会）
