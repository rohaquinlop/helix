# Helix Editor - Agent Instructions

## Build & Test Commands

```bash
cargo check              # type check
cargo test --workspace   # unit tests
cargo integration-test   # integration tests
cargo fmt --all --check  # formatting
cargo clippy --workspace --all-targets -- -D warnings  # lint
cargo doc --no-deps --workspace --document-private-items  # docs (fail on warnings)
```

## XTask Commands

```bash
cargo xtask docgen       # generate docs (auto-runs on PRs)
cargo xtask query-check  # validate tree-sitter queries
cargo xtask theme-check  # validate themes
```

## Important Constraints

- **MSRV**: 1.90 (configured in `rust-toolchain.toml`)
- All lint checks must pass before commit (CI blocks on failures)
- Doc generation is required for PRs (auto-committed or CI will fail)
- Run `cargo test` and `cargo clippy` locally before pushing

## Project Structure

- `helix-term/` - TUI implementation, commands, keymaps
- `helix-view/` - Document, Editor, View models
- `helix-core/` - Core editing logic, text manipulation
- `helix-lsp/` - Language Server Protocol client
- `helix-dap/` - Debug Adapter Protocol
- `runtime/` - Themes, queries (tree-sitter), language configs

## Debugging

- Print using `log::info!`, `log::warn!`, `log::error!`
- Run with `cargo run -- -v <file>` for info-level logs
- Or `cargo run -- --log foo.log` then `tail -f foo.log` in another terminal