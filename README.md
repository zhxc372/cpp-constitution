# cpp-constitution

One command to add structured C++ code review to any project.

```bash
pipx install cpp-constitution
cd /your/cpp/project
cpp-constitution init .
```

## What it does

Generates a C++ review skill into your project. When your AI coding assistant reviews code, it follows a safety-first priority order instead of random nitpicks.

## How it works

```
Your C++ Project
├── CONSTITUTION.md              ← 10-line project config (C++ std, exceptions, build)
├── AGENTS.md                    ← AI entry point (points to skill)
├── .opencode/skills/            ← Review skill (OpenCode)
│   └── cpp-core-review/SKILL.md   ⭐ Core review logic
├── references/                  ← Detailed rules (loaded on demand)
├── config/                      ← clang-tidy profiles
└── scripts/validate.sh          ← Project validation
```

**The skill is the core**, not the constitution.

- CONSTITUTION.md = project config (10 lines, always loaded)
- Skill = review logic (loaded only when you ask for review)
- References = detailed rules (loaded on demand, saves tokens)

## Review Priority

When you say "review src/main.cpp", the skill checks in this order:

1. 🔴 **UB / Safety** — undefined behavior, memory corruption, data races
2. 🟠 **Ownership / Lifetime** — dangling, leaks, use-after-free
3. 🟡 **RAII / Resources** — resource release, cleanup paths
4. **Concurrency** — shared state, thread safety
5. **Error handling** — exception safety or error codes
6. **API / Interface** — design, contracts
7. **Performance** — hot paths, unnecessary copies
8. ⚪ **Style** — naming, formatting (LAST)

## Usage

### Interactive

```bash
cpp-constitution init /path/to/your/project
```

Answer a few questions:

```
? AI Platform: OpenCode
? C++ standard: c++20
? Build system: cmake
? Exceptions enabled: yes
```

### Non-interactive

```bash
cpp-constitution init /path/to/project \
  --platform opencode \
  --std c++20 \
  --build cmake \
  --exceptions \
  --no-interact
```

### Then just code

```bash
cd /your/project
opencode  # or claude, cursor, etc.

# In your AI:
> review src/main.cpp
> audit this crash
> modernize this code
```

## Supported Platforms

| Platform | Skill Location |
|----------|---------------|
| OpenCode | `.opencode/skills/cpp-core-review/` |
| Claude Code | `.claude/skills/cpp-core-review/` |
| Cursor | `.cursorrules` |
| Codex CLI | `skills/` |
| Gemini CLI | `.gemini/skills/` |
| Generic | `skills/` |

## Supported Build Systems

| Build | compile_commands.json |
|-------|----------------------|
| CMake | `cmake -B build -DCMAKE_EXPORT_COMPILE_COMMANDS=ON` |
| Make | `bear -- make` |
| XMake | `xmake project -k compile_commands` |
| Meson | Auto-generated |
| Autotools | `bear -- ./configure && make` |
| None | Manual review only |

## Options

```
cpp-constitution init TARGET [OPTIONS]

Options:
  --platform, -p    AI platform (opencode|claude-code|cursor|codex-cli|gemini-cli|generic)
  --std, -s         C++ standard (c++17|c++20|c++23)
  --build, -b       Build system (cmake|make|xmake|meson|autotools|none)
  --exceptions      Enable exceptions (default)
  --no-exceptions   Disable exceptions (-fno-exceptions)
  --project-name, -n  Project name (default: directory name)
  --no-interact     Skip interactive prompts
```

## License

MIT-0

## Related

- [cpp-ai-constitution](https://github.com/zhxc372/cpp-ai-constitution) — The source project
