# Reviewable Workflows

Open workflow specs from `runplus-community`.

Developer workflows should be explicit, version-controlled, and reviewable before execution.

> Do not execute what you cannot review.

Reviewable Workflows, also referred to as `rw3`, is the spec-level home for a family of developer workflow standards and reference implementations. This repo defines the shared language, principles, threat model, and expected properties for workflows that ship with the code they affect.

For packaging and extraction workflows, the companion principle is:

> Do not bundle what you cannot inspect.

## Status

This repo is in its initial spec-foundation phase.

The first goal is to make the public thesis, terminology, repo relationships, and initial spec families clear before the individual specs are expanded.

## What This Repo Is

`reviewable-workflows` is not a single tool repo.

It is the standard, philosophy, and cross-project documentation layer for Reviewable Workflows:

- what a reviewable workflow is
- why reviewability matters
- how workflow specs are named and versioned
- what behavior reference implementations should expose
- how build, packaging, extraction, and execution workflows should be inspected before they run
- how contributors can propose new workflow specs

The reference tools live in their own repos. Their specs live here.

## Intended Repo Structure

```text
reviewable-workflows/
  README.md
  specs/
    goshbuild.md
    rushbuild.md
    gopickle.md
    rustpickle.md
  principles/
    reviewable-workflows.md
    do-not-execute-what-you-cannot-review.md
    threat-model.md
  examples/
    go/
    rust/
  CONTRIBUTING.md
  SECURITY.md
  LICENSE
```

This README is the front door. The `specs/` directory is the normative home for individual workflow specs. The `principles/` directory explains the shared philosophy and security posture.

## Core Principle

Modern projects execute many workflows before the application itself runs:

- build scripts
- test scripts
- package hooks
- CI commands
- code generators
- extraction tools
- shell scripts
- install-time commands

Those workflows are often scattered across README files, CI configs, package manager hooks, and tribal knowledge.

Reviewable Workflows takes the opposite position:

> The workflow should ship with the code.

Workflow changes should be reviewable in pull requests like any other code change.

## Spec Families

Reviewable Workflows currently has two initial workflow families.

### Reviewable Build Workflows

Reviewable build workflows answer:

> What commands will run?

The `*shbuild` tools make build execution visible through shell-based workflow artifacts that can be inspected before use.

| Spec ID | Reference implementation | Purpose |
| --- | --- | --- |
| `GOSHB-001` | [`goshbuild`](https://github.com/runplus-community/goshbuild) | Reviewable Go build workflows |
| `RUSHB-001` | [`rushbuild`](https://github.com/runplus-community/rushbuild) | Reviewable Rust build workflows |

### Reviewable Packaging and Extraction Workflows

Reviewable packaging and extraction workflows answer:

> What files, source, or project materials are included?

The `*pickle` tools make project packaging and language-native source handoff more inspectable before reuse.

| Spec ID | Reference implementation | Purpose |
| --- | --- | --- |
| `GOPICKLE-001` | [`gopickle`](https://github.com/runplus-community/gopickle) | Reviewable Go project packaging and extraction workflows |
| `RUSTPICKLE-001` | [`rustpickle`](https://github.com/runplus-community/rustpickle) | Reviewable Rust project packaging and extraction workflows |

## Spec Naming

Initial spec IDs use a short project prefix plus a three-digit number:

| Spec ID | Name |
| --- | --- |
| `GOSHB-001` | Reviewable Go Build Workflow |
| `RUSHB-001` | Reviewable Rust Build Workflow |
| `GOPICKLE-001` | Reviewable Go Project Packaging/Extraction Workflow |
| `RUSTPICKLE-001` | Reviewable Rust Project Packaging/Extraction Workflow |

Spec IDs should be stable once referenced by a tool repo. New versions should be added deliberately rather than silently changing the meaning of an existing spec.

## Reference Implementation Map

```text
runplus-community/reviewable-workflows
  -> specs, principles, threat model, and shared documentation

runplus-community/goshbuild
  -> Go build reference implementation

runplus-community/rushbuild
  -> Rust build reference implementation

runplus-community/gopickle
  -> Go packaging/extraction reference implementation

runplus-community/rustpickle
  -> Rust packaging/extraction reference implementation
```

The tool repos are not isolated utilities. They are reference implementations of reviewable workflow specs.

## Expected Properties

A reviewable workflow should make its execution path easier to inspect before use.

At minimum, a workflow spec should define:

- the committed files that describe the workflow
- the commands or operations that may run
- the expected inputs, outputs, and generated artifacts
- the language or runtime assumptions
- the review surface for pull requests
- the security boundaries and non-goals
- the reference implementation behavior
- the compatibility and versioning rules

The goal is not to hide complexity inside a larger framework. The goal is to make workflow behavior small enough, explicit enough, and stable enough to review.

## Review Surface

A reviewer should be able to answer these questions before running a workflow:

- What files define the workflow?
- What commands, scripts, or generated artifacts may execute?
- What inputs does the workflow read?
- What outputs does the workflow write?
- What language toolchains or package managers are involved?
- What parts are generated, cached, vendored, or extracted?
- What behavior changed in this pull request?

If those questions cannot be answered from committed files, the workflow is not reviewable enough.

## Security Note

Reviewable Workflows does not replace dependency scanning, code review, package signing, sandboxing, CI security, or runtime policy enforcement.

It helps reduce hidden execution paths and improves workflow auditability by making workflow behavior visible, versioned, and reviewable before execution.

## Proposing a New Spec

A new workflow spec should start small and explain:

- the problem it addresses
- the files that make the workflow reviewable
- the execution or packaging path
- the minimum reference implementation behavior
- the security non-goals
- at least one concrete example

Specs should favor plain files, predictable behavior, and review-friendly examples over heavy framework design.

## Contributing

Contributions should improve:

- clarity
- smallness
- inspectability
- reproducibility
- useful examples
- documentation
- tests
- security notes

Avoid heavy abstractions unless they are necessary for reviewability. A workflow that is hard to understand is hard to trust.

## License

MIT. See [LICENSE](LICENSE).
