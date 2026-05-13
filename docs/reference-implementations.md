# Reference Implementations

Reviewable Workflows is the spec layer. The supporting repos are reference implementations of Reviewable Workflow Handoffs.

For the complete 4 + 1 repo map, see [Project Map](project-map.md).

```text
                         Go                 Rust
Source Handoff       gopickle           rustpickle
Execution Handoff    goshbuild          rushbuild
```

## Current References

| Repo | Spec | Handoff type |
| --- | --- | --- |
| [`gopickle`](https://github.com/runplus-community/gopickle) | [`GOPICKLE-001`](../specs/source-handoffs/gopickle.md) | Reviewable Go source handoff |
| [`rustpickle`](https://github.com/runplus-community/rustpickle) | [`RUSTPICKLE-001`](../specs/source-handoffs/rustpickle.md) | Reviewable Rust source handoff |
| [`goshbuild`](https://github.com/runplus-community/goshbuild) | [`GOSHB-001`](../specs/execution-handoffs/goshbuild.md) | Reviewable Go execution handoff |
| [`rushbuild`](https://github.com/runplus-community/rushbuild) | [`RUSHB-001`](../specs/execution-handoffs/rushbuild.md) | Reviewable Rust execution handoff |

## Boundary

This repo should not copy implementation code from the reference repos.

Runnable examples, demo apps, test harnesses, generated artifacts, and language-specific implementation code belong in the supporting repos.

This repo may include:

- spec text
- concepts
- diagrams
- terminology
- threat model notes
- comparisons
- cross-project documentation
- links to examples in supporting repos

## Implementation Insights

The initial reference tools show two distinct workflow families:

- `gopickle` and `rustpickle` make source handoffs reviewable by using language-native local repository mechanisms: file-backed `GOPROXY` for Go and Cargo directory or patch configuration for Rust.
- `goshbuild` and `rushbuild` make execution handoffs reviewable by preserving source inside a runner, verifying the payload, rebuilding locally, and caching by source and toolchain identity.

## Linking Rule

Tool repos should link back to the spec they implement.

Specs should link forward to the reference implementation that exercises the spec.
