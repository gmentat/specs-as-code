# Contributing

Thanks for your interest in improving this repo. This project is a **docs-only** specs-as-code template. Changes should focus on Markdown specs, examples, and workflow guidance.

## How to contribute

1. Open an issue (or start a discussion) describing the change.
2. Make updates in the relevant spec folder under `specs/`.
3. Follow the spec contract:
   - Update `spec.md` (the requirement)
   - Update `how-to-test.md` if the verification procedure changes
   - Append to `changelog.md` (do not rewrite history)
   - Update `specs/INDEX.md` if you add or move specs
4. Run the smoke test in `TEST.md` and confirm the pass criteria.

## Style

- Keep changes minimal and specific.
- Prefer editing existing specs over creating new ones.
- Avoid adding tooling or code unless the specs require it.
