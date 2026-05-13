# Reference Implementations

Reviewable Workflows is the spec layer. The supporting repos are reference implementations.

```text
reviewable-workflows = specs, principles, threat model, shared docs
goshbuild            = Go build reference implementation
rushbuild            = Rust build reference implementation
gopickle             = Go local source handoff reference implementation
rustpickle           = Rust local source handoff reference implementation
```

## Current References

| Repo | Spec | Role |
| --- | --- | --- |
| [`goshbuild`](https://github.com/runplus-community/goshbuild) | `GOSHB-001` | Reviewable Go build workflows |
| [`rushbuild`](https://github.com/runplus-community/rushbuild) | `RUSHB-001` | Reviewable Rust build workflows |
| [`gopickle`](https://github.com/runplus-community/gopickle) | `GOPICKLE-001` | Reviewable Go local source handoff workflows |
| [`rustpickle`](https://github.com/runplus-community/rustpickle) | `RUSTPICKLE-001` | Reviewable Rust local source handoff workflows |

## Boundary

This repo should not copy implementation code from the reference repos.

Runnable examples, demo apps, test harnesses, generated artifacts, and language-specific implementation code belong in the supporting repos.

This repo may include:

- spec text
- diagrams
- terminology
- threat model notes
- cross-project documentation
- links to examples in supporting repos

## Implementation Insights

The initial reference tools show two distinct workflow families:

- `goshbuild` and `rushbuild` make execution handoff reviewable by preserving source inside a runner, verifying the payload, rebuilding locally, and caching by source and toolchain identity.
- `gopickle` and `rustpickle` make local source handoff reviewable by using language-native local repository mechanisms: file-backed `GOPROXY` for Go and Cargo directory or patch configuration for Rust.

## Linking Rule

Tool repos should link back to the spec they implement.

Specs should link forward to the reference implementation that exercises the spec.
