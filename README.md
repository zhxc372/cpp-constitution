# cpp-constitution

> ⚠️ This repository has been merged into [cpp-ai-constitution](https://github.com/zhxc372/cpp-ai-constitution).

## Source of Truth

All development continues at:
**https://github.com/zhxc372/cpp-ai-constitution**

The CLI installer lives in `cli/` directory of the main repo.

## Install

```bash
# From the main repo
pipx install git+https://github.com/zhxc372/cpp-ai-constitution.git#subdirectory=cli

# Or clone and install locally
git clone https://github.com/zhxc372/cpp-ai-constitution.git
cd cpp-ai-constitution/cli
pipx install -e .
```

## Usage

```bash
cpp-constitution init /path/to/your/cpp-project
```

## Why archived?

Single source of truth — rules and installer must live in one repo to avoid drift.

See: [cpp-ai-constitution/cli/](https://github.com/zhxc372/cpp-ai-constitution/tree/master/cli)
