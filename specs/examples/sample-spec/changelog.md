# Changelog

## 2026-07-27

- Separated use cases and interfaces into required artifacts.
- Added an exact spec-folder contract under `contracts/`.
- Reduced the data model to currently required concepts.
- Made `implementation.md` optional and removed the unused sample file.
- Protected product, interface, and critical model contracts from solution-driven changes.
- Made `SPECS.md` self-contained and project-specific principles optional.
- Added a read-only specification review before implementation.
- Added a post-implementation comparison against the protected contracts.
- Removed mandatory per-spec versioning; Git and this changelog record contract evolution.
- Updated requirements and verification for the new folder contract.

## 2026-02-20 (0.2.1)

- Aligned sample spec with updated templates (priority rationale + independent test, edge cases, key entities).
- Expanded `how-to-test.md` with clarification-marker and FR-* coverage checks.
- Updated `implementation.md` decisions table to include consequences and added risks/mitigations.
- Bumped version to 0.2.1.

## 2026-02-20

- Added numbered requirements (FR-001 through FR-003).
- Added success criteria (SC-001).
- Added user scenario with Given/When/Then acceptance.
- Added decisions table to `implementation.md`.
- Added cross-artifact consistency checklist to `how-to-test.md`.
- Bumped version to 0.2.0.

## 2026-02-10

- Added required `data-model.md`.
- Bumped `version`.

## 2026-02-09

- Added required `implementation.md`.
- Bumped `version`.

## 2026-02-07

- Folded acceptance criteria into spec.md.
- Removed status.md (status is in frontmatter).
- Updated `how-to-test.md` with explicit steps and expected results.
- Set `status` to `active` and bumped `version`.

## 2026-02-05

- Initial version.
