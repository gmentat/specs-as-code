# How to test

## Verification steps

1. Confirm this spec folder contains:
   - `spec.md`
   - `implementation.md`
   - `how-to-test.md`
   - `data-model.md`
   - `changelog.md`
   Expected: all files exist. (Covers FR-001)

2. Open `spec.md` and confirm YAML frontmatter includes:
   - `id`
   - `title`
   - `area`
   - `status` (one of: `draft`, `active`, `deprecated`)
   - `version`
   Expected: frontmatter parses as YAML. (Covers FR-002)

3. Confirm this spec is listed in `specs/INDEX.md`.
   Expected: there is a link to `examples/sample-spec/spec.md` and it resolves. (Covers FR-003)

4. Search this spec folder for `[NEEDS CLARIFICATION:` markers.
   Expected: no unresolved markers remain. (`spec.md` status is `active`.)

5. Confirm every requirement (FR-*) in `spec.md` is covered by at least one verification step in this file.
   Expected:
   - FR-001 is covered by step 1.
   - FR-002 is covered by step 2.
   - FR-003 is covered by step 3.

## Cross-artifact consistency checklist

- [x] Every entity in `data-model.md` is referenced in `spec.md`
- [x] Every requirement (FR-*) in `spec.md` is addressed by `implementation.md`
- [x] Every requirement (FR-*) in `spec.md` has a matching verification step above
- [x] Every acceptance criterion in `spec.md` has a matching verification step above
- [x] Terminology is consistent across all five files (no renamed concepts, no drift)
- [x] If `spec.md` status is `active`: no unresolved `[NEEDS CLARIFICATION]` markers in any file
