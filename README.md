# code-intel-rust

Nix packaging for the local `code-intel-rust` Bun CLI.

## Package

- Binary: `code-intel-rust`
- Entrypoint: `src/cli.ts`
- Current role: structural and semantic Rust code intelligence
- Planned direction: Bun CLI frontend for operator and agent queries, with direct commands or daemon-backed execution

## What this repo does

- Packages the local Bun CLI with `bun2nix`
- Exposes the canonical `code-intel-rust` binary
- Keeps runtime code under `src/` and agent-facing guidance under `skills/`

## Files

- `flake.nix`: flake entrypoint
- `nix/package.nix`: Nix derivation
- `nix/package-manifest.json`: pinned local package metadata and binary entrypoint

## Usage

```bash
nix build
./result/bin/code-intel-rust ast outline src/lib.rs
./result/bin/code-intel-rust lsp serve
./result/bin/code-intel-rust lsp definition src/lib.rs 12 4 --repo-root /path/to/worktree
```

Cross-tool usage:

```bash
repo-map query "**/*" --term agent --term scheduler --lang rs --json
code-intel-rust ast outline src/agent/scheduler.rs --repo-root /path/to/worktree
code-intel-rust lsp references src/agent/scheduler.rs 18 8 --repo-root /path/to/worktree
```

Use `repo-map` for discovery, then `code-intel-rust ast ...` for the first precise pass. Only move to `lsp ...` when you need semantic definitions, references, hover, diagnostics, or call hierarchy.
