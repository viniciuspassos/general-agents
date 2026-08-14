## Workflow

- Before editing, read relevant docs and search for existing behavior.
- Check the current branch and `git status`; preserve unrelated changes.
- If the working tree is dirty, stop and ask how to preserve the changes. Never stash automatically.
- If not on `main`, ask whether to check out `main`; if declined, wait for direction.
- On a clean `main`, run `git pull --ff-only`; stop if it cannot fast-forward.
- Create a task branch using the repository convention, or `feature/<slug>` as fallback.

## Code style

- Functions: 4-20 lines. Files: under 500 lines. Split by responsibility when longer.
- One thing per function, one responsibility per module (SRP).
- Names: specific and unique. Avoid `data`, `handler`, `Manager`.
  Prefer names that return <5 grep hits in the codebase.
- Types: explicit. No `any`, no `Dict`, no untyped functions.
- No code duplication. Extract shared logic into a function or module.
- Prefer early returns; keep nesting to at most 2 levels.
- Follow framework conventions and keep paths predictable.
- Change behavior in its owning module; preserve the source of truth and avoid god modules.
- Exception messages include the offending value and expected shape unless the value is sensitive.

## Tests and validation

- Every new or changed function requires a test; TDD is optional.
- Tests must exercise real behavior, never be added or weakened merely to pass.
- Remove a test only when its corresponding function or behavior is removed.
- Bug fixes require regression tests. Tests must be F.I.R.S.T.
- Mock external I/O with named fake classes, not inline stubs.
- Run the project's configured linter, or the language-standard linter if none is configured.
- Run relevant formatting, type-checking, tests, and builds; report anything not run.
- Use structured logs for observability and plain text for CLI output; never log sensitive data.
- Update documentation when public behavior, architecture, or operations change.
