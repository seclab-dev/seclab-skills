---
name: seclab-ui-style
description: >
  使用 SecLab Design Language (SDL) 与自研基础 UI 套件创建符合 Security Lab Platform 风格的
  Vue 3 窗口组件、Dashboard、Monaco 编辑器、xterm 终端与 ECharts 可视化。
---

# SecLab UI Style Skill

本 skill 用于 SecLab 前端页面、窗口应用、Dashboard、表格管理页、日志页、图表、Monaco 编辑器和 xterm 终端的实现与重构。SecLab 前端必须优先使用自研 UI 组件和 SDL token，保持专业、安全运维控制台的高密度工程风格。

开始视觉设计前读取 `../../shared/brand/seclab-brand.md`；具体 Token 数值仍以 `seclab-ui/packages/tokens/index.css` 为准。

## 必须遵守

- 事实来源优先：公共 Token、组件和图标分别以 `seclab-ui/packages/tokens`、`seclab-ui/packages/vue`、`seclab-ui/packages/icons` 为准；主控本地文件只负责消费和项目专属适配。
- 组件优先：业务 UI 优先使用 `SecLab*` 自研组件，不引入 Element Plus、Ant Design、Naive UI 等第三方 UI 框架。
- 文案国际化：新增业务文案必须走 `frontend/src/locales/zh.ts` 和 `frontend/src/locales/en.ts`，不要在模板里硬编码面向用户的中文或英文。
- DOM 标记：业务页面和关键区域必须提供稳定可搜索的 `data-page`、`data-ui`、`data-slot`，便于调试和自动化。
- Template 结构标签：SecLab 业务窗口与管理页模板统一使用 `div` 组织结构，不使用 `header`、`main`、`section`、`article` 等 HTML 语义结构标签；页面语义只通过 class、`data-page`、`data-ui`、`data-slot` 表达。
- 容器选择：详情、查看、创建和编辑内容优先使用 `SecLabDialog`；仅当内容窄、轻量、线性，且必须在操作时持续保留主页面上下文时才使用 `SecLabDrawer`。
- 风格边界：禁止黑客卡通、骷髅、绿色字符雨、大面积霓虹、科幻 HUD、强饱和蓝紫渐变和装饰性 orb/blob。
- 布局边界：不要把页面 section 做成漂浮卡片；不要卡片套卡片；只在重复项、Modal/Dialog/Drawer、工具面板中使用卡片。
- 交付验证：修改主控前端后运行 `pnpm -C frontend format`、`pnpm -C frontend lint`、`pnpm -C frontend build`；修改 UI 库后运行 `pnpm check`。

## 任务路由

根据任务类型读取对应 reference；如果任务跨多个类型，按顺序读取多个文件。

- 改 token、颜色、字体、间距、圆角、密度：读 `references/tokens-and-style.md`。
- 写或改自研组件调用、表格、表单、按钮、弹窗、抽屉：读 `references/components.md`。
- 写或改窗口应用、Dashboard、管理页、日志页、详情页：读 `references/page-patterns.md`。
- 写或改 ECharts、Monaco、xterm、视觉 QA 或交付检查：读 `references/visual-qa.md`。

## 产品气质

- Engineering：结构清晰、状态明确、操作可预测、高可扫描性。
- Observability：强调遥测、日志、指标、拓扑、事件流和可追溯操作。
- Information Density：优先紧凑、稳定、可重复使用的业务界面，而不是营销式或展示型页面。
- Domain Fit：安全测试和分布式基础设施控制平面，视觉应冷静、克制、可信。
