# zbisure.github.io — 学习地图

交互式学习页合集，托管在 GitHub Pages：<https://zbisure.github.io/>

## 结构

```
index.html          # 学习主页（主题卡片列表）
unknowns/index.html # 01 · 未知项野外指南（Finding Your Unknowns）
```

## 增加新学习主题

1. 新建目录 `<topic>/`，放入自包含的 `index.html`（不依赖外部 CDN，内联 CSS/JS，适配明暗双主题）
2. 在根 `index.html` 的 `.cards` 里复制注释中的卡片模板，填上编号、日期、标签、标题和描述
3. 提交并 push，Pages 自动部署

## 设计约定

- 视觉语言：地形图/野外手册——纸面底色、等高线装饰、测绘蓝强调色
- 字体：衬线显示（Songti SC/Georgia）+ 无衬线正文（PingFang SC）+ 等宽（SF Mono/Menlo），全部系统字体，无外部字体
- 每页结构：心智模型 → 实操内容（可复制模板）→ 自测 quiz（通过才算学会）
