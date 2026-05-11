# cpp-constitution

One command to install C++ AI review skills into your project.

## Quick Start

### Persistent install

```bash
pipx install git+https://github.com/zhxc372/cpp-ai-constitution.git#subdirectory=cli
cd /your/cpp/project
cpp-constitution init .
```

### One-shot run (no install)

```bash
uvx --from git+https://github.com/zhxc372/cpp-ai-constitution.git#subdirectory=cli cpp-constitution init .
```

Then ask your AI agent:
```
review src/main.cpp
```

## What Gets Generated

```
your-project/
├── CONSTITUTION.md              # 10-line project config
├── AGENTS.md                    # AI entry point (auto-triggers skill)
├── GOTCHAS.md                   # Known AI failure patterns
├── config/
│   ├── clang-tidy.minimal.yml
│   ├── clang-tidy.strict.yml
│   └── clang-tidy.migration.yml
├── references/                  # 9 C++ rule files (loaded on demand)
├── scripts/validate.sh
└── .opencode/skills/cpp-core-review/SKILL.md  ⭐
```

## Usage

### Interactive

```bash
cpp-constitution init .
```

### Non-interactive

```bash
cpp-constitution init . --platform opencode --std c++20 --build xmake --no-interact
```

## Supported Platforms

| Platform | Generated entry |
|----------|----------------|
| OpenCode | `.opencode/skills/cpp-core-review/SKILL.md` |
| Claude Code | `.claude/skills/cpp-core-review/SKILL.md` |
| Cursor | `.cursorrules` |
| Codex CLI | `skills/` |
| Gemini CLI | `.gemini/skills/` |
| Generic | `AGENTS.md` only |

## Supported Build Systems

CMake, XMake, Make, Meson, Autotools, None

## Distribution Strategy

| Command | Status | Purpose |
|---------|--------|---------|
| `pipx install cpp-constitution` | Primary | Persistent install |
| `uvx cpp-constitution init .` | Supported | One-shot execution |
| `npx cpp-constitution init .` | Planned | JS ecosystem thin wrapper |

## Source of Truth

This repository is a **distribution mirror** for the CLI package.

The rule system, skills, references, adapters, and development workflow live in:

**[zhxc372/cpp-ai-constitution](https://github.com/zhxc372/cpp-ai-constitution)**

Do not edit generated rules here directly. All changes should be made in the source repository.

## License

MIT-0
