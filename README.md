# Specs as Code

A docs-only convention for humans and coding agents.

`SPECS.md` is self-contained and designed to be copied into any project. Its core workflow is:

**use cases → data model → interfaces/contracts → specification → tests → spec review → implementation → conformance**

`implementation.md` is optional. Small contracts stay in `interfaces.md`; machine-readable or longer contracts live under `contracts/`. After code changes, compare the implementation with the contracts before declaring it complete.

Before implementation, run a read-only review of the specification and rerun it after correcting any findings.

## Start

1. Read `SPECS.md`.
2. Use `specs/INDEX.md` to find the relevant spec.
3. Use `specs/TEMPLATE/` when creating one.

## Smoke test

Open this repository in an agent tool and use the prompt in `TEST.md`.

## Examples

- [Product details](specs/examples/product-details/interfaces.md) keeps its canonical OpenAPI definition under `contracts/`.
- [Feature flags](specs/examples/python-feature-flags/interfaces.md) keeps a small typed Python contract inline.

## Reuse

Copy `SPECS.md` into a project and reference it from the repository's agent instructions. That is sufficient to use the convention.

The templates and examples under `specs/` are optional starter material. Add `specs/PRINCIPLES.md` only when the project needs additional project-wide rules.

## License

See `LICENSE`.
