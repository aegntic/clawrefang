```markdown
# clawrefang Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns, coding conventions, and common workflows used in the `clawrefang` Rust monorepo. You'll learn how to structure code, manage multi-crate changes, update API routes, handle agent metadata, and maintain community and CI configurations. The guide also covers commit practices and how to use suggested commands for frequent tasks.

## Coding Conventions

### File Naming

- **CamelCase** is used for file names.
  - Example: `modelCatalog.rs`, `toolRunner.rs`

### Import Style

- **Relative imports** are preferred.
  - Example:
    ```rust
    use super::kernel;
    use crate::modelCatalog::ModelCatalog;
    ```

### Export Style

- **Named exports** are used.
  - Example:
    ```rust
    pub mod kernel;
    pub fn run_server() { /* ... */ }
    ```

### Commit Patterns

- Commit messages are **freeform**, often short (~17 characters on average).
- Common prefixes: none enforced, but batch operations use phrases like `batch fixes`, `bugfix batch`, or `version bump`.

## Workflows

### Multi-Crate Bugfix Batch

**Trigger:** When fixing multiple bugs or making small improvements across several crates and components.

**Command:** `/batch-fix`

1. Identify bugs or minor improvements in various crates and modules.
2. Edit relevant source files (Rust, JS, TOML, etc.) in multiple crates (e.g., `api`, `kernel`, `runtime`, `cli`, `channels`).
3. Update shared files like `Cargo.toml` and `Cargo.lock` to reflect dependency or version changes.
4. Commit all changes together with a message like `batch fixes`, `bugfix batch`, or `bugfixes batch`.

**Example:**
```sh
# Edit multiple files across crates
git add crates/openfang-api/src/routes.rs crates/openfang-kernel/src/kernel.rs Cargo.toml Cargo.lock
git commit -m "bugfix batch: fix API and kernel issues"
```

---

### Version Bump

**Trigger:** When releasing a new version or starting a new development cycle.

**Command:** `/bump-version`

1. Edit `Cargo.toml` (and sometimes `Cargo.lock`) to increment the version number.
2. Commit with a message like `version bump` or `bump version`.

**Example:**
```toml
# Cargo.toml
version = "0.2.0"
```
```sh
git add Cargo.toml Cargo.lock
git commit -m "version bump"
```

---

### API Routes Update

**Trigger:** When adding, modifying, or fixing API endpoints or their integration with the server.

**Command:** `/update-api-route`

1. Edit `crates/openfang-api/src/routes.rs` to add or change API endpoints.
2. Optionally update `server.rs`, `middleware.rs`, or `ws.rs` for related logic.
3. Update static assets (HTML, JS) if the API surface or UI changes.
4. Update `Cargo.toml` and/or `Cargo.lock` if dependencies are affected.
5. Commit all related changes together.

**Example:**
```rust
// crates/openfang-api/src/routes.rs
pub fn new_route() {
    // ...implementation...
}
```
```sh
git add crates/openfang-api/src/routes.rs crates/openfang-api/src/server.rs Cargo.toml
git commit -m "add new API endpoint"
```

---

### Agent or Extension Metadata Batch Update

**Trigger:** When updating configuration or metadata for many agents or extensions at once.

**Command:** `/batch-update-agents`

1. Edit multiple agent or extension `.toml` files (e.g., `agents/*/agent.toml`, `crates/openfang-extensions/integrations/*.toml`).
2. Optionally update related Rust source files in `kernel`, `types`, or `registry`.
3. Update `Cargo.toml` and/or `Cargo.lock` if dependencies are affected.
4. Commit all changes together.

**Example:**
```toml
# agents/example/agent.toml
name = "Example Agent"
version = "1.1.0"
```
```sh
git add agents/*/agent.toml crates/openfang-extensions/integrations/*.toml
git commit -m "batch update agent metadata"
```

---

### Community or CI Config Update

**Trigger:** When improving community health files, CI workflows, or project documentation.

**Command:** `/update-community`

1. Edit `.github/` workflows, issue templates, or pull request templates.
2. Optionally update `README.md`, `SECURITY.md`, or `docs/*.md`.
3. Optionally make minor code or config changes (e.g., `kernel.rs`, `model_catalog.rs`, `install.sh`).
4. Commit all changes together.

**Example:**
```sh
git add .github/workflows/ci.yml README.md scripts/install.sh
git commit -m "update CI workflow and docs"
```

## Testing Patterns

- **Framework:** Unknown (no explicit Rust test framework detected).
- **File Pattern:** Some test files follow the `*.test.ts` pattern, suggesting TypeScript-based tests for JS/TS components.
- **Rust Tests:** If present, likely use standard Rust `#[cfg(test)]` modules within source files.

**Example (Rust):**
```rust
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_example() {
        assert_eq!(2 + 2, 4);
    }
}
```

**Example (TypeScript):**
```typescript
// example.test.ts
import { myFunction } from './myModule';

test('should work', () => {
  expect(myFunction()).toBe(true);
});
```

## Commands

| Command               | Purpose                                                         |
|-----------------------|-----------------------------------------------------------------|
| /batch-fix            | Batch bugfixes or minor improvements across multiple crates     |
| /bump-version         | Increment project version after changes or for a new release    |
| /update-api-route     | Add, modify, or fix API endpoints and related server logic      |
| /batch-update-agents  | Batch update agent or extension metadata/configuration files    |
| /update-community     | Update community, CI, or documentation files and minor configs  |
```
