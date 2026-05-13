# GOSHB-001: Reviewable Go Build Workflow

Status: Draft

Reference implementation: [`runplus-community/goshbuild`](https://github.com/runplus-community/goshbuild)

## Purpose

`GOSHB-001` defines a reviewable build handoff workflow for Go projects.

The workflow should make the transition from source code to runnable execution explicit, version-controlled, and reviewable before execution.

> Do not execute what you cannot review.

## Scope

This spec covers Go build workflows where the build path is represented by committed workflow files or generated handoff artifacts that can be inspected before use.

The reference implementation is `goshbuild`, which packages a Go module into a source-preserving shell runner. The runner embeds the source payload, verifies it before extraction, builds it with the local Go toolchain, caches the resulting binary, and then executes it with the original arguments.

## Reviewability Requirements

A `GOSHB-001` workflow should make these things visible:

- the Go module or source tree being built
- the shell workflow or generated runner that will execute
- the embedded or referenced source payload
- the payload checksum or equivalent integrity marker
- the build command path
- the expected inputs and outputs
- the Go toolchain assumptions
- any generated, cached, vendored, or extracted material

A reviewer should be able to inspect the committed workflow before running it locally or in CI.

## Expected Properties

- The workflow should ship with the project.
- Workflow changes should be reviewable in pull requests.
- Generated handoff artifacts should be identifiable.
- Source should remain inspectable rather than disappearing behind a binary-only handoff.
- Payload verification should happen before extraction when a payload is embedded.
- Cache keys should account for source identity, toolchain identity, platform, and payload identity.
- The build path should avoid hidden steps that are only documented out of band.
- The workflow should remain small enough to inspect.

## Security Notes

`GOSHB-001` does not claim to prevent supply-chain attacks.

It helps reduce hidden execution paths by making Go build behavior easier to audit.

## Non-Goals

This spec does not replace:

- Go module security review
- dependency scanning
- code signing
- CI hardening
- sandboxing
- general code review
