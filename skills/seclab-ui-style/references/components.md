# SecLab Components

## 事实来源

- 组件源码：`linked-repos/seclab-ui/packages/vue/src/components/`
- 导出入口：`linked-repos/seclab-ui/packages/vue/src/index.ts`
- 发布入口：`@seclab-dev/vue`
- 主控 `frontend/src/components/ui/` 是兼容导出层，不是组件事实来源。
- 真实 Props 以组件源码和发布类型声明为准。

## 组件清单

- 操作：`SecLabButton`、`SecLabActionMenu`
- 输入：`SecLabInput`、`SecLabSelect`、`SecLabSwitch`、`SecLabCheckbox`、`SecLabDateTimeRangePicker`
- 数据：`SecLabTable`、`SecLabPagination`、`SecLabDescriptions`、`SecLabTag`
- 容器：`SecLabCard`、`SecLabDrawer`、`SecLabDialog`、`SecLabModal`
- 反馈：`SecLabAlert`、`SecLabToast`、`SecLabLoading`、`SecLabEmpty`、`SecLabTooltip`
- 导航：`SecLabMenu`、`SecLabTabs`、`SecLabBreadcrumb`、`SecLabBreadcrumbItem`

## 常用 API 提醒

- `SecLabButton`
  - `type`: `primary | secondary | danger | warning | info`
  - `size`: `small | default | large`
  - 支持 `disabled`、`loading`
- `SecLabTable`
  - Props 是 `data`、`columns`、`border`
  - 列支持 `prop`、`label`、`width`、`minWidth`、`align`、`headerAlign`、`slot`、`headerSlot`、`fixed`
  - 没有 `loading` prop；加载态用外围 `SecLabLoading` 或页面级状态处理
  - 空状态通过 `empty` slot 或默认 `common.noData`
- `SecLabTag`
  - `type`: `primary | success | warning | danger | info | default`
  - `effect`: `light | plain | dark`，当前常用 `light`
- `SecLabTooltip`
  - Prop 是 `text`，不是 `content`
  - `position`: `top | bottom | left | right`
- `SecLabDrawer`
  - 使用 `v-model` / `modelValue`
  - 仅适合窄幅、单列、轻量且需要持续保留主页面上下文的辅助面板
  - 典型场景包括快速预览、简单属性检查和与主列表联动的少量设置
- `SecLabDialog`
  - 使用 `visible`、`title`、`width`、`closeOnClickOverlay`
  - 默认用于详情、查看、创建和编辑内容
  - 适合多列描述、宽表格、长标识、多分组信息、复杂表单和短流程
  - 根据内容设置响应式宽度，正文区域统一滚动
- `SecLabModal`
  - 适合简单确认，不承载复杂表单

## 使用规则

- 容器选择优先级：
  1. 默认选择 `SecLabDialog`。
  2. 内容包含表格、多列描述、长路径、长标识、多分组或大量数据时必须使用 `SecLabDialog`。
  3. 只有内容可在窄幅单列中完整表达，交互短且保持主页面上下文具有明确价值时，才选择 `SecLabDrawer`。
  4. 不要仅因为内容名为“详情”或“配置”就选择 `SecLabDrawer`。
- 图标按钮优先使用现有 `SecLabIcon` 或项目图标系统，避免手写临时 SVG。
- 删除、停止、重置等破坏性操作使用 `SecLabButton type="danger"` 或 action menu 的 danger 样式。
- 状态展示优先用 `SecLabTag`，不要用裸色文本表达在线、失败、告警。
- 表单项优先用 `SecLabFormItem` 组织 label、说明和错误。
- 详情键值对优先用 `SecLabDescriptions`，不要手写松散的两列列表。
- 大量操作不要铺满工具栏，收敛到 `SecLabActionMenu`。

## 标记约定

- 页面根：`data-page="node-manager"`、`data-page="platform-log"` 等。
- 工具栏：`data-ui="toolbar"`。
- 表格：`data-ui="table"`。
- 详情区域：`data-slot="detail"`。
- 弹窗/抽屉内部关键区域继续使用 `data-slot="header|body|footer"`。
