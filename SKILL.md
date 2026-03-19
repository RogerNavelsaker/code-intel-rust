---
name: code-intel-rust
description: Structural and semantic Rust code navigation via ast-grep and a rust-analyzer flox service.
---

# Rust Code Intelligence

Use this skill when you need fast Rust symbol lookup, signatures, structural search, definitions, references, hover docs, diagnostics, or call hierarchy.

## Commands

```bash
# Structural queries
.pi/skills/code-intel-rust/code-intel-rust ast outline <file> [--json]
.pi/skills/code-intel-rust/code-intel-rust ast symbols <file> [--json]
.pi/skills/code-intel-rust/code-intel-rust ast imports <file> [--json]
.pi/skills/code-intel-rust/code-intel-rust ast signature <file> <symbol> [--json]
.pi/skills/code-intel-rust/code-intel-rust ast scope <file> <line> [col] [--json]
.pi/skills/code-intel-rust/code-intel-rust ast search <pattern> [paths...] [--json]

# Semantic queries (requires flox service)
.pi/skills/code-intel-rust/code-intel-rust lsp definition <file> <line> <col> [--json]
.pi/skills/code-intel-rust/code-intel-rust lsp references <file> <line> <col> [--json]
.pi/skills/code-intel-rust/code-intel-rust lsp hover <file> <line> <col> [--json]
.pi/skills/code-intel-rust/code-intel-rust lsp diagnostics <file> [--json]
.pi/skills/code-intel-rust/code-intel-rust lsp calls <file> <line> <col> [--direction in|out] [--json]
```

## Notes
- Human-readable output is the default.
- Add `--json` for compact machine-readable output.
- `ast search` requires `ast-grep` in the flox environment.
- `lsp ...` commands require the `rust-code-intel` flox service to be running.
