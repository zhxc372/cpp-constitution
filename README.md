# cpp-constitution

[English](README.md) | [中文](https://github.com/zhxc372/cpp-ai-constitution/blob/master/README_CN.md)

CLI installer for [cpp-ai-constitution](https://github.com/zhxc372/cpp-ai-constitution) — safety-first C++ review skill for AI coding agents.

One command to install C++ AI review skills into your project. Zero intrusion.

---

## Install

```bash
pipx install git+https://github.com/zhxc372/cpp-ai-constitution.git#subdirectory=cli
cd /your/cpp/project
cpp-constitution install .
```

### One-shot (no install)

```bash
uvx --from git+https://github.com/zhxc372/cpp-ai-constitution.git#subdirectory=cli cpp-constitution install .
```

Then ask your AI agent:
```
review src/main.cpp
```

---

## What Gets Generated

**Zero intrusion** — all files go into the platform's skill directory:

```
your-project/
└── .opencode/skills/cpp-core-review/    # everything here
    ├── SKILL.md                         # review logic (YAML frontmatter)
    ├── project-config.md                # C++ version, build, exceptions
    ├── references/                      # 9 rule files (loaded on demand)
    ├── config/                          # clang-tidy profiles
    └── GOTCHAS.md                       # known AI failure patterns
```

No `AGENTS.md` at root. No `CONSTITUTION.md` at root. No pollution.

---

## Usage

### Interactive

```bash
cpp-constitution install .
```

### Non-interactive

```bash
cpp-constitution install . --platform opencode --std c++20 --build xmake --no-interact
```

### Backward compat

`init` works as an alias for `install`.

---

## 13 Platforms

| Platform | Type | Target |
|----------|------|--------|
| OpenCode | Skill | `.opencode/skills/cpp-core-review/` |
| Claude Code | Skill | `.claude/skills/cpp-core-review/` |
| Trae | Skill | `.trae/skills/cpp-core-review/` |
| CodeBuddy | Skill | `.codebuddy/skills/cpp-core-review/` |
| Gemini CLI | Skill | `.gemini/skills/cpp-core-review/` |
| Cursor | Rule | `.cursor/rules/cpp-review.mdc` |
| Windsurf | Rule | `.windsurfrules` |
| GitHub Copilot | Rule | `.github/copilot-instructions.md` |
| Amazon Q | Rule | `.amazonq/rules/cpp-review.md` |
| 通义灵码 | Rule | `.lingma/rules/cpp-review.md` |
| Void | Rule | `.void/rules/cpp-review.md` |
| Codex CLI | Generic | `AGENTS.md` |
| Generic | Generic | `AGENTS.md` |

---

## Two Install Paths

| Path | Repository | How |
|------|-----------|-----|
| **Plugin** (marketplace) | [cpp-ai-constitution](https://github.com/zhxc372/cpp-ai-constitution) | `/install-plugin` or platform marketplace |
| **CLI** (pipx/uvx/npx) | This repo | `pipx install cpp-constitution` |

Same skill content, different delivery. Plugin users get auto-updates. CLI users get more control.

---

## Source of Truth

This repository is a **distribution mirror** for the CLI package only.

Rules, skills, references, adapters, evals, and plugin registration live in:

**[zhxc372/cpp-ai-constitution](https://github.com/zhxc372/cpp-ai-constitution)**

---

## License

MIT-0
