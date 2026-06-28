---
name: seclab-icon-system
description: >
  为 SecLab 按钮、工具栏、菜单、状态、数据展示和紧凑应用语义场景生成、验证及维护自有
  24px SVG UI 图标。不用于应用库、桌面、任务栏或 Compose 套件入口的 PNG 图标；
  后者必须使用 seclab-app-icon。
---

# SecLab Icon System

为按钮、工具栏、菜单、状态、数据展示和紧凑应用语义场景制作可主题化的 24px SVG 图标。应用库、桌面、任务栏和套件入口图标使用 `$seclab-app-icon`。

## Workflow

1. Read `../../shared/brand/seclab-brand.md` and `references/icon-style.md` before drawing new icons.
2. 通用 UI 图标放入 `packages/icons/svgs/common/`；窗口标题、通知来源、菜单和空状态使用的应用语义图标放入 `packages/icons/svgs/apps/`。
3. Use `24x24` SVGs with `viewBox="0 0 24 24"`, `currentColor` as the structural stroke color, and `var(--sdl-primary)` only for controlled emphasis.
4. 使用 `common` 与 `apps` 独立命名空间，`fallback.svg` 只放在 `common`。
5. Update UI code to render icon names through the project icon component instead of displaying strings directly.
6. 分别校验 `packages/icons/svgs/common` 和 `packages/icons/svgs/apps`，再在 `seclab-ui` 运行 `pnpm check`。

## Hard Rules

- Do not use emoji, text glyphs, external icon fonts, raster images, or embedded base64.
- 应用 SVG 只用于紧凑语义场景，不得替代桌面、任务栏、应用库或套件入口 PNG。
- Do not copy vendor logos unless the user explicitly asks and the repo already has the rights to use them.
- Do not use cyberpunk, hacker, neon, or decorative game-like styling.
- Keep icons readable at `16px`, `24px`, `28px`, and `40px`.
- Prefer a consistent 2px stroke, rounded line caps, and rounded joins.
- Keep SVG files hand-editable and deterministic.

## Output Contract

- File names: lowercase letters, digits, and hyphens only.
- Missing icon behavior: render `fallback.svg`, never fall back to emoji.
- Validation must pass before considering icon work complete.
