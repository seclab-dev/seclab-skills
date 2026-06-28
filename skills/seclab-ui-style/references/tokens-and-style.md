# SDL Tokens And Style

## 事实来源

- 公共 Token 源文件：`linked-repos/seclab-ui/packages/tokens/index.css`
- 发布入口：`@seclab-dev/tokens/index.css`
- 主控 `frontend/src/styles/theme.css` 只维护全局重置、滚动条和桌面壁纸等项目专属适配。
- 主控默认使用浅色主题，同时支持深色主题。
- 不要在 skill 中重新发明颜色或阴影；如果 token 不存在，先检查是否已有近似 token。

## 常用 Token

- 背景：`--sdl-bg-canvas`、`--sdl-bg-base`、`--sdl-bg-panel`、`--sdl-bg-card`、`--sdl-bg-muted`、`--sdl-bg-input`
- 文本：`--sdl-text-primary`、`--sdl-text-secondary`、`--sdl-text-muted`、`--sdl-text-subtle`、`--sdl-text-inverse`
- 品牌：`--sdl-primary`、`--sdl-primary-hover`、`--sdl-primary-active`、`--sdl-secondary`、`--sdl-accent`
- 状态：`--sdl-success`、`--sdl-warning`、`--sdl-danger`、`--sdl-info` 及对应 `*-soft`
- 边框：`--sdl-border-subtle`、`--sdl-border-default`、`--sdl-border-strong`、`--sdl-border-brand`
- 字体：`--sdl-font-family`、`--sdl-font-mono`
- 字号：`--sdl-font-title`、`--sdl-font-subtitle`、`--sdl-font-body`、`--sdl-font-body-sm`、`--sdl-font-caption`、`--sdl-font-code`
- 间距：`--sdl-space-1` 到 `--sdl-space-8`
- 圆角：`--sdl-radius-xs`、`--sdl-radius-sm`、`--sdl-radius-md`、`--sdl-radius-lg`、`--sdl-radius-pill`
- 层级：`--sdl-z-index-window`、`--sdl-z-index-header`、`--sdl-z-index-popover`、`--sdl-z-index-modal`、`--sdl-z-index-toast`

## 使用规则

- 优先使用 token，不在业务组件里散落硬编码颜色。
- 状态语义固定：成功/在线用 success，警告/排队用 warning，高危/删除/失败用 danger，通信/扫描/提示用 info 或 primary。
- 日志、ID、路径、命令、哈希、端口、IP 使用 `--sdl-font-mono` 或 `--sdl-font-code`。
- 工具栏和紧凑表单使用 `--sdl-space-2`/`--sdl-space-3`；主内容边距通常使用 `--sdl-space-4`。
- 窗口应用内部标题不要使用 hero 级字号；紧凑面板标题通常使用 `--sdl-font-subtitle` 或 `--sdl-font-body`。
- 避免单一色相统治页面。主色只用于操作、选中和关键状态，不用大片蓝紫渐变当背景。

## 布局约束

- 窗口内容根节点通常是 `height: 100%; min-height: 0; display: flex; flex-direction: column;`。
- 可滚动区域必须设置 `min-height: 0`，避免表格、日志、编辑器撑破窗口。
- 固定格式 UI（表格列、工具栏按钮、图表容器、编辑器、终端）要有稳定尺寸或 `min/max` 约束。
- 文本不能溢出按钮、Tag、表格单元格；长 ID/路径优先使用等宽字体、截断、tooltip 或详情抽屉。
