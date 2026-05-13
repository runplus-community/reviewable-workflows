# Project Map

RunPlus Community is building Reviewable Workflow Handoffs.

The five repos form one spec-and-reference system:

```text
runplus-community/
  reviewable-workflows   # spec, thesis, concepts, comparisons

  gopickle               # Go source handoff reference implementation
  rustpickle             # Rust source handoff reference implementation

  goshbuild              # Go execution handoff reference implementation
  rushbuild              # Rust execution handoff reference implementation
```

## 2x2 Matrix

```text
                         Go                 Rust
Source Handoff       gopickle           rustpickle
Execution Handoff    goshbuild          rushbuild
```

## Handoff Families

### Reviewable Source Handoffs

Source handoffs make project files and dependency content visible before another project, team, reviewer, or tool consumes them.

Slogan:

> Do not bundle what you cannot inspect.

Reference implementations:

- [`gopickle`](https://github.com/runplus-community/gopickle): [`GOPICKLE-001`](../specs/source-handoffs/gopickle.md)
- [`rustpickle`](https://github.com/runplus-community/rustpickle): [`RUSTPICKLE-001`](../specs/source-handoffs/rustpickle.md)

### Reviewable Execution Handoffs

Execution handoffs make commands and workflow behavior visible before they run locally or in CI.

Slogan:

> Do not execute what you cannot review.

Reference implementations:

- [`goshbuild`](https://github.com/runplus-community/goshbuild): [`GOSHB-001`](../specs/execution-handoffs/goshbuild.md)
- [`rushbuild`](https://github.com/runplus-community/rushbuild): [`RUSHB-001`](../specs/execution-handoffs/rushbuild.md)

## Boundary

`reviewable-workflows` owns the shared concepts, draft specs, threat model, and comparisons.

The four tool repos own implementation code, runnable examples, generated artifacts, test harnesses, and language-specific behavior.

Specs should link to reference implementations. Reference implementations should link back to their specs.

## Short Mental Model

`gopickle` and `rustpickle` are the labeled shelf for source: inspect the package before another project consumes it.

`goshbuild` and `rushbuild` are the reviewable meal kit for execution: inspect the ingredients, recipe, and seal before building and running locally.
