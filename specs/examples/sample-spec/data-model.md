# Data model

This sample uses a minimal data model to demonstrate the required `data-model.md` file.

## Atomic unit

- `spec_document`: the center-of-gravity object for a spec folder.

## Entities and stable identifiers

- `spec_document`
  - Stable identifier: `id` from `spec.md` frontmatter (for example `examples.sample-spec`).
  - Update model: updated in-place as the contract evolves.
- `spec_file`
  - Stable identifier: repo-relative path (for example `specs/examples/sample-spec/spec.md`).
  - Update model: updated in-place.

## Boundaries

- Primary query boundary: spec folder path (`specs/<area>/<feature>/`).
- Ownership: one spec folder owns its required files.

## Relationships

- One `spec_document` has many `spec_file` entries.
- Required files are linked by naming convention in the same folder.

## Derived vs persisted fields

- Persisted: file contents and frontmatter values on disk.
- Derived: whether the folder is "valid" under the contract (computed from file presence and frontmatter checks).

## Invariants

- Exactly one `spec.md` per spec folder.
- Required files exist: `spec.md`, `implementation.md`, `how-to-test.md`, `data-model.md`, `changelog.md`.
- `spec.md` frontmatter includes `id`, `title`, `area`, `status`, `version`.
