# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

`grid-fence-tui` is a Rust terminal UI application built with [ratatui](https://ratatui.rs/) (v0.30). It is in early development — `src/main.rs` is currently a placeholder.

## Commands

```bash
# Build
cargo build

# Run
cargo run

# Run tests
cargo test

# Run a single test
cargo test <test_name>

# Check without producing a binary
cargo check

# Lint
cargo clippy

# Format
cargo fmt
```

## Architecture

- **Entry point**: `src/main.rs`
- **UI framework**: `ratatui` — the idiomatic ratatui pattern is an event loop that alternates between drawing the UI and handling input events. The main terminal state is managed via `ratatui::init()` / `ratatui::restore()` (or manual `crossterm` setup in older versions).
- **Rust edition**: 2024

When implementing the TUI, the typical structure is:
1. An `App` struct holding application state
2. A `run` function with an event loop: draw → handle events → update state
3. Widget rendering in a separate `ui` function passed to `terminal.draw()`
