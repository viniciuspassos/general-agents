# Global defaults

Apply to every project. When a project's CLAUDE.md or its established
conventions conflict with these, the project wins.

## Code

- Small, single-purpose functions (~20 lines) and modules (<500 lines).
  Split by responsibility, not just to hit a number.
- Specific, greppable names. Avoid generic ones (`data`, `handler`, `Manager`, `utils`).
- Explicit types; no escape hatches (`any`, bare `dict`/`Dict`, untyped functions).
- Extract duplicated logic into a shared function or module.
- Early returns over nested conditionals; at most 2 levels of nesting inside a function.
- Error messages include the offending value and the expected shape.
- Inject dependencies via constructor/parameters, not globals or imports.
- Wrap third-party libraries behind a thin interface the project owns.

## Comments

- Preserve existing comments when refactoring; they carry intent and provenance.
- Explain WHY, not WHAT.
- Public functions get a docstring: intent + one usage example.
- Cite the issue number or commit SHA when code exists because of a specific
  bug or upstream constraint.

## Tests

- TDD: write a failing test, confirm it fails for the right reason, make it pass
  with minimal code, then refactor.
- Every new behavior gets a test; every bug fix gets a regression test.
- Assert observable behavior (inputs → outputs/side effects), not implementation
  details. Never write tests just to pass or to raise coverage.
- Never delete, skip, or weaken an existing test to go green. If a test looks
  wrong, stop and ask me why it should change.
- Fake external I/O (APIs, DB, filesystem) with named fake classes, not inline stubs.
- Keep tests fast, independent, and deterministic.
- Use the project's single test command from its CLAUDE.md; if none is documented, ask.

## Tooling

- Follow the framework's conventions for structure and file layout.
- Format with the language's default formatter (`gofmt`, `prettier`, `black`,
  `rubocop -A`, …). Don't debate style beyond it.
- Logging: structured JSON for diagnostics; plain text only for user-facing CLI output.
