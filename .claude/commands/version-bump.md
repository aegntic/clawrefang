---
name: version-bump
description: Workflow command scaffold for version-bump in clawrefang.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /version-bump

Use this workflow when working on **version-bump** in `clawrefang`.

## Goal

Increment the version of the project (and sometimes dependencies) after a set of changes or a release.

## Common Files

- `Cargo.toml`
- `Cargo.lock`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit Cargo.toml (and sometimes Cargo.lock) to increment the version number.
- Commit with a message like 'version bump', 'bump version', or similar.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.