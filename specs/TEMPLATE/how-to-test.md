# How to test

## Verification steps

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
   Expected: there is a link to this spec's `spec.md` and it resolves.

4. Search this spec folder for `[NEEDS CLARIFICATION:` markers.
   Expected:
   - If `spec.md` status is `active`: no unresolved markers remain.
   - If `spec.md` status is `draft`: markers are allowed, but each must be a specific question and total count is <= 3.

5. Confirm every requirement (FR-*) in `spec.md` is covered by at least one verification step in this file.
   Expected: there are no orphan requirements. (Tip: add `(Covers FR-###)` to the relevant steps.)

## Cross-artifact consistency checklist

<!-- Run through this checklist when the spec moves to `active` or after significant edits. -->

- [ ] Every entity in `data-model.md` is referenced in `spec.md`
- [ ] Every requirement (FR-*) in `spec.md` is addressed by `implementation.md`
- [ ] Every requirement (FR-*) in `spec.md` has a matching verification step above
- [ ] Every acceptance criterion in `spec.md` has a matching verification step above
- [ ] Terminology is consistent across all five files (no renamed concepts, no drift)
- [ ] If `spec.md` status is `active`: no unresolved `[NEEDS CLARIFICATION]` markers in any file
