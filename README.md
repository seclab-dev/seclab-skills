# SecLab Skills

`seclab-skills` 是 SecLab 组织级 AI Skill 源，用于统一设计语言、图标生成、界面实现和可重复开发流程。

业务代码、组件实现和最终视觉资产不存放在本仓库。消费仓库通过本地软链接使用 skill，修改回到本仓库完成。

## 目录结构

```text
seclab-skills/
├── skills/
│   ├── seclab-app-icon/
│   ├── seclab-icon-system/
│   └── seclab-ui-style/
├── shared/
│   └── brand/
└── README.md
```

## Skill 清单

| Skill | 职责 |
| --- | --- |
| `seclab-app-icon` | 生成和验证内置应用、应用库入口与 Compose 套件 PNG 图标。 |
| `seclab-icon-system` | 维护按钮、工具栏、菜单和状态等 24px SVG 图标。 |
| `seclab-ui-style` | 使用 SDL Token 和 SecLab Vue 3/React 19 组件实现、审查前端界面。 |

共享品牌规范位于 `shared/brand/seclab-brand.md`。运行时 Token、组件和 SVG 图标以消费仓当前安装版本的 `@seclab-dev/*` 公开包为准；本地 `seclab-ui` 源码仓是可选开发信息源。

## 接入方式

```bash
mkdir -p .agents/skills
ln -s /absolute/path/to/seclab-skills/skills/seclab-app-icon \
  .agents/skills/seclab-app-icon
```

本地绝对路径软链接不得提交到 Git。

## UI 环境探测

`seclab-ui-style` 提供无第三方依赖、只读的环境探测器，用于识别消费仓的 Vue/React 技术栈、SecLab 包版本、公开声明与可选源码仓：

```bash
node skills/seclab-ui-style/scripts/inspect-seclab-context.mjs \
  --root /path/to/consumer-project
```

追加 `--format json` 可获得稳定结构化输出；追加 `--seclab-ui <path>` 可显式提供本地源码仓。脚本不联网、不 clone、不写文件。

## 维护规则

1. 只在本仓库维护 skill 真实文件。
2. 单个 skill 的专用脚本保留在对应 skill 内。
3. 两个以上 skill 复用的稳定脚本再提升到 `shared/scripts/`。
4. 业务专属规则留在业务仓库。
5. 最终 PNG、SVG、页面和组件资产提交到消费仓库。

## 验证

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py \
  skills/seclab-app-icon
```

修改多个 skill 时逐个验证。带脚本的 skill 需要使用真实输入验证成功和失败场景。
