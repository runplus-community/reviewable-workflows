# Glossary

Reviewable Workflow Handoffs uses a small vocabulary so specs and reference tools can stay precise.

## Handoff

A handoff is the moment when code, files, commands, generated artifacts, dependency content, or workflow behavior is passed from one context to another.

Examples:

- a source module is exposed to another project
- a generated runner is handed to a shell or CI job
- a local dependency source is configured for a consumer project
- a build workflow becomes the thing a maintainer is expected to run

## Reviewable Handoff

A handoff is reviewable when the receiver can inspect what is being handed over before consuming it or executing it.

Reviewable does not mean automatically safe. It means visible enough to inspect and discuss.

## Source Handoff

A source handoff passes source files, dependency content, or local repository artifacts to another project, team, reviewer, or tool.

Source handoffs answer:

> What files or source content are being consumed?

## Execution Handoff

An execution handoff passes commands, scripts, runners, generated workflow files, or build behavior to a developer shell or CI system.

Execution handoffs answer:

> What will run?

## Producer

The producer creates the handoff artifact or configuration.

Examples:

- `gopickle` creating a file-backed `GOPROXY`
- `rustpickle` creating a Cargo directory source
- `goshbuild` creating a Go runner
- `rushbuild` creating a Rust runner

## Consumer

The consumer receives or uses the handoff.

Examples:

- a Go project configured to use a local `GOPROXY`
- a Rust crate configured with a Cargo patch
- a CI job executing a generated runner
- a developer shell running a source-preserving handoff artifact

## Review Surface

The review surface is the set of files, metadata, commands, and generated artifacts that a reviewer should inspect before trust is required.

## Language-Native

Language-native means using the package manager, build tool, or ecosystem mechanism that developers already understand where practical.

Examples:

- Go `GOPROXY`
- Cargo directory sources and patch configuration
- shell-visible runners for local and CI execution
