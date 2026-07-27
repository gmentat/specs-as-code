# Smoke test

## Prompt

> Add a draft spec called `notifications` for a Python application whose users need an in-app notification when a background task finishes.

## Pass criteria

- [ ] The agent read `SPECS.md` and `specs/INDEX.md`.
- [ ] The folder contains all six required artifacts.
- [ ] `implementation.md` is absent unless the agent records a concrete, non-obvious decision.
- [ ] `use-cases.md` defines the current user outcome and acceptance example.
- [ ] Every data-model element and interface supports that use case.
- [ ] The notification interface has an exact typed Python declaration, not only a prose description.
- [ ] A `contracts/` directory exists only if a separate canonical contract is justified.
- [ ] No speculative fields, operations, or abstractions were added.
- [ ] `spec.md` has valid frontmatter and testable requirements.
- [ ] `how-to-test.md` covers the use case, requirements, invariants, and interface.
- [ ] The agent reports a read-only specification review, corrects findings that affect behavior, contracts, or verification, and reruns it.
- [ ] The spec is indexed and its changelog contains an appended entry.

## Cleanup

Delete the created spec folder and revert its `specs/INDEX.md` entry.
