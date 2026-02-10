# How to test

1. Confirm this spec folder contains:
   - `spec.md`
   - `implementation.md`
   - `how-to-test.md`
   - `data-model.md`
   - `changelog.md`
   Expected: all files exist.

2. Open `spec.md` and confirm YAML frontmatter includes:
   - `id`
   - `title`
   - `area`
   - `status` (one of: `draft`, `active`, `deprecated`)
   - `version`
   Expected: frontmatter parses as YAML.

3. Confirm this spec is listed in `specs/INDEX.md`.
   Expected: there is a link to `examples/sample-spec/spec.md` and it resolves.
