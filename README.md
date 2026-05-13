# Reviewable Workflows

Open workflow specs from `runplus-community`.

Developer workflows should be explicit, version-controlled, and reviewable before execution.

> Do not execute what you cannot review.

Reviewable Workflows, also referred to as `rw3`, is the spec-level home for reviewable developer workflow standards. This repo is for specs, principles, threat model, and shared documentation. Reference implementation code lives in the supporting repos.

## What This Repo Defines

- what a reviewable workflow is
- why workflow reviewability matters
- how workflow specs are named and versioned
- how reference implementations connect to specs
- what security claims and non-goals apply

## Initial Spec Families

### Reviewable Build Workflows

Reviewable build workflows answer:

> What commands will run?

| Spec ID | Reference implementation | Purpose |
| --- | --- | --- |
| `GOSHB-001` | [`goshbuild`](https://github.com/runplus-community/goshbuild) | Reviewable Go build workflows |
| `RUSHB-001` | [`rushbuild`](https://github.com/runplus-community/rushbuild) | Reviewable Rust build workflows |

### Reviewable Local Source and Packaging Workflows

Reviewable local source and packaging workflows answer:

> What files, source, or project materials are included?

> Do not bundle what you cannot inspect.

| Spec ID | Reference implementation | Purpose |
| --- | --- | --- |
| `GOPICKLE-001` | [`gopickle`](https://github.com/runplus-community/gopickle) | Reviewable Go local source handoff workflows |
| `RUSTPICKLE-001` | [`rustpickle`](https://github.com/runplus-community/rustpickle) | Reviewable Rust local source handoff workflows |

## Repo Boundary

This repo should stay documentation-first:

```text
reviewable-workflows/
  specs/
  principles/
  docs/
  SECURITY.md
  CONTRIBUTING.md
```

Runnable code and project examples belong in:

- [`goshbuild`](https://github.com/runplus-community/goshbuild)
- [`rushbuild`](https://github.com/runplus-community/rushbuild)
- [`gopickle`](https://github.com/runplus-community/gopickle)
- [`rustpickle`](https://github.com/runplus-community/rustpickle)

For the deeper project thesis, see [docs/thesis-notes.md](docs/thesis-notes.md).

## Security Note

Reviewable Workflows does not replace dependency scanning, code review, package signing, sandboxing, CI security, or runtime policy enforcement.

It helps reduce hidden execution paths and improves workflow auditability by making workflow behavior visible, versioned, and reviewable before execution.

For packaging and local source handoff, it helps make included source and generated consumer configuration easier to inspect before reuse.

## License

MIT. See [LICENSE](LICENSE).
