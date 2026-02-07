# Smoke test (specs-as-code)

## Prompt (copy/paste)

> Add a new spec called `notifications`.

## Pass criteria

- [ ] Agent read `SPECS.md` before making changes
- [ ] Agent found and used `specs/INDEX.md`
- [ ] Created a spec folder with `spec.md`, `how-to-test.md`, `changelog.md`
- [ ] `spec.md` has YAML frontmatter (id, title, area, status, version)
- [ ] New spec is listed in `specs/INDEX.md`
- [ ] `changelog.md` was appended to (not rewritten)

## Cleanup

Delete the agent-created spec folder and revert `specs/INDEX.md`.
