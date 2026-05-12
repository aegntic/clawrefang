---
name: multi-crate-bugfix-batch
description: Workflow command scaffold for multi-crate-bugfix-batch in clawrefang.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /multi-crate-bugfix-batch

Use this workflow when working on **multi-crate-bugfix-batch** in `clawrefang`.

## Goal

Batch of bugfixes or minor improvements across multiple crates and components in the monorepo.

## Common Files

- `Cargo.toml`
- `Cargo.lock`
- `crates/openfang-api/src/routes.rs`
- `crates/openfang-api/src/server.rs`
- `crates/openfang-api/src/middleware.rs`
- `crates/openfang-api/static/index_body.html`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify bugs or minor improvements in various crates and modules.
- Edit relevant source files (Rust, JS, TOML, etc.) in multiple crates (api, kernel, runtime, cli, channels, etc.).
- Update shared files like Cargo.toml and Cargo.lock to reflect dependency or version changes.
- Commit all changes together with a message like 'batch fixes', 'bugfix batch', or 'bugfixes batch'.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.