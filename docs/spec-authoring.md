# Spec Authoring

Specs should be small, direct, and reviewable.

The purpose of a spec is to define the review surface and expected behavior for a workflow family. It should not hide behavior behind broad framework language.

## Recommended Shape

Each spec should include:

- spec ID and title
- status
- reference implementation link
- purpose
- scope
- reviewability requirements
- expected properties
- security notes
- non-goals

## Spec IDs

Initial spec IDs use a short project prefix plus a three-digit number:

| Spec ID | Name |
| --- | --- |
| `GOSHB-001` | Reviewable Go Build Workflow |
| `RUSHB-001` | Reviewable Rust Build Workflow |
| `GOPICKLE-001` | Reviewable Go Local Source Handoff Workflow |
| `RUSTPICKLE-001` | Reviewable Rust Local Source Handoff Workflow |

Spec IDs should be stable once referenced by a tool repo.

## Status Values

Use simple status values:

- `Draft`
- `Experimental`
- `Stable`
- `Deprecated`

## Examples

Keep runnable examples in supporting repos.

Specs may include small documentation examples or link to example files in the reference implementation repo.

## Security Language

Avoid overclaiming security.

Do not say:

> This prevents supply-chain attacks.

Say:

> This helps reduce hidden execution paths and improves workflow auditability.
