# Interfaces

## Clients

- Contributors and coding agents use IF-001 for UC-001.

## IF-001: Spec folder

- **Supports:** UC-001
- **Purpose:** Let a contributor or agent create and validate a spec through the repository filesystem
- **Canonical contract:** [`contracts/spec-folder.md`](contracts/spec-folder.md)

### Semantics

- **Errors:** A contract violation makes the folder invalid and identifies the failed rule.
- **Side effects:** Creating a spec adds its folder and `specs/INDEX.md` entry.
- **Guarantees:** A conforming folder contains the required contracts; optional artifacts may be absent.
