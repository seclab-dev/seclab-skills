# Page Patterns

## 窗口应用根布局

窗口应用页面优先使用稳定的纵向结构：

- 模板结构统一使用 `div`，不要使用 `header`、`main`、`section`、`article` 等 HTML 语义结构标签。
- 页面语义放在 class、`data-page`、`data-ui`、`data-slot` 中，便于风格统一、调试和自动化定位。

```vue
<template>
  <!-- 顶层使用 class 语义表示 -->
  <div class="view-shell" data-page="example">
    <div class="view-toolbar" data-ui="toolbar">...</div>
    <div class="view-content" data-slot="content">...</div>
  </div>
</template>
```

```css
.view-shell {
  height: 100%;
  min-height: 0;
  display: flex;
  flex-direction: column;
  background: var(--sdl-bg-panel);
}

.view-toolbar {
  flex-shrink: 0;
  display: flex;
  align-items: center;
  gap: var(--sdl-space-3);
  padding: var(--sdl-space-3) var(--sdl-space-4);
  border-bottom: 1px solid var(--sdl-border-subtle);
}

.view-content {
  flex: 1;
  min-height: 0;
  overflow: auto;
  padding: var(--sdl-space-4);
}
```

## 管理页

- 顶部工具栏放搜索、筛选、刷新、主操作。
- 主体用表格或左右 split，不要用营销式 hero。
- 表格列必须可扫描：名称/状态/来源/时间/操作。
- 批量或低频操作放 `SecLabActionMenu`，常用主操作放 `SecLabButton type="primary"`。
- 详情查看、创建和编辑默认使用 `SecLabDialog`；危险确认使用 `SecLabModal`。
- 仅当辅助内容窄、单列、轻量，且用户需要在打开期间持续观察或操作主页面时，才使用 `SecLabDrawer`。
- 包含宽表格、多列描述、长路径、长标识、多分组或大量数据的详情不得使用 `SecLabDrawer`。

## Dashboard

- 用紧凑指标卡和图表面板，不堆大装饰卡。
- 指标卡包含：标签、值、单位、状态趋势或更新时间。
- ECharts 容器要有稳定高度，图表底盘透明。
- 图表标题和图例使用小字号，避免遮挡数据。

## 日志页

- 时间范围、级别、来源、关键词筛选放在固定工具栏或可折叠筛选区。
- 日志 message、target、trace、IP、路径使用等宽字体或局部等宽。
- 大文本不直接撑开行；用截断、tooltip、详情模态框或展开行。
- “加载更多”遵循页面既有交互，不随意改变滚动触发或占位行设计。

## 表单页

- 短表单、复杂表单和多分组配置默认使用 Dialog；多步骤流程使用 Tabs 或分组，而不是超长单列。
- 仅当配置项少、单列可完整表达，并且调整时必须持续参照主页面时，才使用 `SecLabDrawer`。
- 错误靠近输入项，必要时使用 `SecLabAlert` 给全局错误。
- 二值项用 `SecLabSwitch` 或 `SecLabCheckbox`，枚举用 `SecLabSelect`。
- 数字、端口、超时等要有单位和边界提示。

## 参考页面

- 日志和筛选：`frontend/src/apps/views/PlatformLogView.vue`
- 复杂管理页：`frontend/src/apps/views/SimulationView.vue`
- 节点管理：`frontend/src/apps/views/NodeManagerView.vue`
- 运维资源页：`frontend/src/apps/views/DockerManagerView.vue`
- 编辑器页：`frontend/src/apps/views/FileEditorView.vue`
- 终端页：`frontend/src/apps/views/TerminalView.vue`
