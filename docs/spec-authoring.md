# Spec Authoring

Specs should be small, direct, and reviewable.

The purpose of a spec is to define the review surface and expected behavior for a workflow handoff family. It should not hide behavior behind broad framework language.

## Recommended Shape

Each spec should include:

- spec ID and title
- status
- purpose
- handoff type
- language
- reference implementation repo
- reviewability goal
- inputs
- outputs
- required visible metadata or manifest behavior
- security notes
- non-goals

## Spec IDs

Initial spec IDs use a short project prefix plus a three-digit number:

| Spec ID | Name |
| --- | --- |
| `GOPICKLE-001` | Reviewable Go Source Handoff |
| `RUSTPICKLE-001` | Reviewable Rust Source Handoff |
| `GOSHB-001` | Reviewable Go Execution Handoff |
| `RUSHB-001` | Reviewable Rust Execution Handoff |

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

> This makes supply-chain attacks impossible.

Say:

> This helps reduce hidden workflow behavior and improves handoff auditability.
