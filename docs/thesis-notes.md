# Thesis Notes

Reviewable Workflows is not just a collection of small CLI tools.

The deeper thesis is:

> Developer workflow handoffs should be visible, language-native where possible, version-controlled, and reviewable before they run or before another project consumes them.

## Two Handoff Problems

The first four reference implementations point to two related problems.

### 1. Execution Handoff

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

### 2. Local Source Handoff

`gopickle` and `rustpickle` address the moment when one local project needs to consume another local project.

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

The insight is not merely "copy files." The insight is that local dependency flow can be made reviewable using the package manager's native model.

## Shared Shape

Both families turn hidden workflow behavior into review surfaces.

| Family | Question | Review Surface |
| --- | --- | --- |
| `*shbuild` | What will run? | runner, payload, checksum, build command, cache key |
| `*pickle` | What source is consumed? | generated local repo, version, metadata, include/exclude rules, consumer config |

This gives Reviewable Workflows a broader thesis:

> Handoffs are where workflow behavior becomes hard to see. Make the handoff artifact reviewable.

## Language-Native Matters

The tools should not invent large framework abstractions when the language ecosystem already has useful primitives.

Examples:

- Go already understands `GOPROXY`.
- Cargo already understands directory sources and patch configuration.
- Shell runners are inspectable and portable across common CI/local environments.

The standard should prefer explicit language-native handoffs over opaque orchestration.

## Security Position

Reviewable Workflows is a supply-chain hygiene story, but it should not overclaim.

Correct claim:

> Reviewable workflows reduce hidden execution paths and make workflow behavior easier to audit.

Incorrect claim:

> Reviewable workflows prevent supply-chain attacks.

The security value is visibility, not magic safety.

## Spec Repo Boundary

This repo should remain the research and standards layer.

It should not copy the implementation code, generated runners, demo projects, or smoke-test harnesses from the supporting repos. Those artifacts are useful evidence for the specs, but they should stay in:

- `goshbuild`
- `rushbuild`
- `gopickle`
- `rustpickle`

The spec repo should instead capture the cross-project thesis, terms, requirements, threat model, and links to evidence.

## Research Directions

A dedicated research pass should explore:

- how many developer workflow risks come from hidden handoff behavior
- how local dependency development is handled across ecosystems
- where language-native local repository mechanisms already exist
- how reviewable workflow artifacts should be represented in pull requests
- what minimum metadata a handoff artifact should expose
- how to describe generated artifacts without forcing implementation code into the spec repo
- where reviewability ends and sandboxing, signing, or policy enforcement begins

## Working Vocabulary

- Reviewable workflow: a workflow whose behavior can be inspected from committed files before use.
- Execution handoff: the step where source/build workflow becomes runnable execution.
- Local source handoff: the step where one local project becomes consumable by another local project.
- Handoff artifact: a runner, local repository, generated config, or metadata file that carries workflow behavior across a boundary.
- Review surface: the files and metadata a reviewer must inspect to understand the handoff.
