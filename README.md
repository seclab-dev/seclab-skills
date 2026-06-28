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
| `seclab-ui-style` | 使用 SDL Token 和 SecLab UI 组件实现前端界面。 |

共享品牌规范位于 `shared/brand/seclab-brand.md`。运行时 Token、组件和 SVG 图标以 `seclab-ui` 对应包为准。

## 接入方式

```bash
mkdir -p .agents/skills
ln -s /absolute/path/to/seclab-skills/skills/seclab-app-icon \
  .agents/skills/seclab-app-icon
```

本地绝对路径软链接不得提交到 Git。

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
