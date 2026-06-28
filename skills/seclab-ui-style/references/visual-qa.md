# Visual QA, Charts, Editors, Terminals

## ECharts

- 主色限制：`#00C8FF`、`#00D4B4`、`#7C6CFF`、`#FFB547`、`#FF5E7A`。
- 背景透明，容器使用 SDL 背景。
- 网格线使用弱边框，例如 `rgba(148, 163, 184, 0.12)`。
- 坐标轴和图例文本使用 `--sdl-text-muted` 语义，字号通常 10-12px。
- 图表容器必须有稳定高度，窗口尺寸变化后要 resize。

## Monaco

- 优先复用 `frontend/src/components/editor/MonacoEditor.vue` 和 `sdl-monaco-theme.ts`。
- 编辑器字体使用 `var(--sdl-font-mono)`，字号通常 13-14px。
- 编辑器容器必须 `min-height: 0`，避免在窗口内撑破布局。
- 工具栏按钮使用自研组件，不在编辑器周围添加重装饰。

## xterm

- 使用 `@xterm/xterm` 与 `@xterm/addon-fit`。
- 终端背景使用 `#0F172A` 或 SDL canvas/panel 深色。
- 光标、选区、链接高亮使用 `--sdl-primary` 语义，避免荧光绿。
- 终端容器必须在窗口 resize 后 fit，且不能被 header/footer 挤出。

## 视觉检查

- 桌面窗口、抽屉、Dialog 在窄宽下不溢出。
- 工具栏按钮、Tag、输入框文本不重叠、不截断关键字。
- 表格空状态、加载状态、错误状态都存在。
- 固定列、操作列、滚动容器不造成横向布局跳动。
- 图表、编辑器、终端必须非空白，容器尺寸稳定。
- 深色和浅色 token 不直接硬编码冲突。

## 交付检查

前端改动完成后运行：

```bash
pnpm -C frontend format
pnpm -C frontend lint
pnpm -C frontend build
```

如果改动图表、编辑器、终端、复杂响应式窗口，优先用浏览器或截图实际检查至少一个常用桌面尺寸和一个窄窗口尺寸。
