# Changelog

格式遵循 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，并遵循 [Semantic Versioning](https://semver.org/lang/zh-CN/)。

## [Unreleased]

### Added

- 为 `seclab-ui-style` 增加只读消费仓探测脚本和 React 19 专用参考。
- 为 UI skill 增加环境事实解析、Vue/React 渐进路由和 UI 元数据。

### Changed

- 三个 skills 统一采用分析、事实解析、执行和验收工作流。
- 将 Token、组件和图标事实来源改为消费仓当前安装版本优先，本地源码与 GitHub 仅作补充。
- 修正公共 SVG 图标源码目录和默认验证路径，并补充 Vue/React 消费规则。

## [0.1.0-alpha.1] - 2026-06-28

### Added

- 首次发布 SecLab 组织级 AI Skill 仓库。
- 提供 `seclab-app-icon`，用于生成和验证应用、应用库入口与套件 PNG 图标。
- 提供 `seclab-icon-system`，用于维护通用 24px SVG UI 图标。
- 提供 `seclab-ui-style`，用于约束 SecLab 前端界面实现风格。
- 提供共享品牌规范，统一图标、色彩和视觉气质。
