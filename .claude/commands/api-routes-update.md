---
name: api-routes-update
description: Workflow command scaffold for api-routes-update in clawrefang.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /api-routes-update

Use this workflow when working on **api-routes-update** in `clawrefang`.

## Goal

Make changes to the API routes, often alongside related server, middleware, or static asset updates.

## Common Files

- `crates/openfang-api/src/routes.rs`
- `crates/openfang-api/src/server.rs`
- `crates/openfang-api/src/middleware.rs`
- `crates/openfang-api/src/ws.rs`
- `crates/openfang-api/static/index_body.html`
- `crates/openfang-api/static/js/pages/*.js`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit crates/openfang-api/src/routes.rs to add or change API endpoints.
- Optionally update server.rs, middleware.rs, or ws.rs for related logic.
- Update static assets (HTML, JS) if the API surface or UI changes.
- Update Cargo.toml and/or Cargo.lock if dependencies are affected.
- Commit all related changes together.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.