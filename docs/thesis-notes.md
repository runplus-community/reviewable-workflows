# Thesis Notes

Reviewable Workflow Handoffs is not just a collection of small CLI tools.

The deeper thesis is:

> Developer workflow handoffs should be visible, language-native where possible, version-controlled, and reviewable before they run or before another project consumes them.

## Two Handoff Problems

The first four reference implementations point to two related problems.

### 1. Source Handoff

`gopickle` and `rustpickle` address the moment when one local project, tool, reviewer, or AI agent needs to consume source from another project.

Traditional handoffs often use:

- ad hoc copying
- path rewrites
- unpublished package assumptions
- manual instructions
- temporary local hacks that are hard to reproduce

The `*pickle` pattern uses the language ecosystem's own local repository mechanisms:

- Go: file-backed `GOPROXY`
- Rust: Cargo directory source or `[patch.crates-io]`

The workflow makes the local source handoff explicit:

- identify the source module or crate
- select a version
- generate language-native local repository artifacts
- expose the consumer configuration
- document included and excluded files
- keep metadata with the generated source

The insight is not merely "copy files." The insight is that local source flow can be made reviewable using the package manager's native model.

### 2. Execution Handoff

`goshbuild` and `rushbuild` address the moment when source code becomes something executable.

Traditional handoffs often choose between:

- shipping only source and asking users to reconstruct the build path
- shipping only a binary and hiding the source/build path
- burying the real build behavior in CI, README instructions, or local scripts

The `*shbuild` pattern keeps the source-preserving handoff visible:

- package source into a runner
- include or reference the build workflow
- verify the payload before extraction
- build with the local language toolchain
- cache by source, platform, toolchain, and payload identity
- execute the result with normal arguments

The insight is not merely "generate a shell script." The insight is that the runnable handoff itself can carry a reviewable source and build story.

## Shared Shape

Both families turn hidden workflow behavior into review surfaces.

| Family | Question | Review Surface |
| --- | --- | --- |
| Source handoff | What source is consumed? | generated local repo, version, metadata, include/exclude rules, consumer config |
| Execution handoff | What will run? | runner, payload, checksum, build command, cache key |

This gives Reviewable Workflow Handoffs a clear thesis:

> Handoffs are where workflow behavior becomes hard to see. Make the handoff artifact reviewable.

## Language-Native Matters

The tools should not invent large framework abstractions when the language ecosystem already has useful primitives.

Examples:

- Go already understands `GOPROXY`.
- Cargo already understands directory sources and patch configuration.
- Shell runners are inspectable and portable across common CI/local environments.

The standard should prefer explicit language-native handoffs over opaque orchestration.

## Spec Repo Boundary

This repo should remain the research and standards layer.

It should not copy the implementation code, generated runners, demo projects, or smoke-test harnesses from the supporting repos. Those artifacts are useful evidence for the specs, but they should stay in:

- `gopickle`
- `rustpickle`
- `goshbuild`
- `rushbuild`

The spec repo should instead capture the cross-project thesis, terms, requirements, threat model, comparisons, and links to evidence.
