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
  - 适合详情、编辑表单、较长配置
- `SecLabDialog`
  - 使用 `visible`、`title`、`width`、`closeOnClickOverlay`
  - 适合创建、确认前的复杂表单或短流程
- `SecLabModal`
  - 适合简单确认，不承载复杂表单

## 使用规则

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
