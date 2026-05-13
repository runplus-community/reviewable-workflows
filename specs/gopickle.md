# GOPICKLE-001: Reviewable Go Local Source Handoff Workflow

Status: Draft

Reference implementation: [`runplus-community/gopickle`](https://github.com/runplus-community/gopickle)

## Purpose

`GOPICKLE-001` defines a reviewable local source handoff workflow for Go projects.

The workflow should make local Go module reuse explicit by turning a source module into a file-backed `GOPROXY` that another Go project can consume through normal Go module behavior.

> Do not bundle what you cannot inspect.

## Scope

This spec covers Go project packaging and local source handoff workflows where included files and generated outputs can be reviewed before another project consumes them.

The reference implementation is `gopickle`, which creates a local file-backed `GOPROXY` from Go modules.

## Reviewability Requirements

A `GOPICKLE-001` workflow should make these things visible:

- the source module being exposed locally
- the files included in the generated module zip
- the generated Go proxy artifacts: `.mod`, `.info`, `.zip`, `list`, and metadata
- the version or identity assigned to the package
- the `GOPROXY` value needed by a consumer project
- any files intentionally excluded from the package

A reviewer should be able to inspect what will be bundled or exposed before another project consumes it.

## Expected Properties

- The packaging workflow should be repeatable.
- Included and excluded files should be explainable.
- Generated outputs should use language-native Go module concepts where practical.
- Consumer projects should keep normal Go module behavior where possible.
- Local reuse should avoid ad hoc copying when a language-native local source path can be made explicit.
- The workflow should remain small enough to inspect.

## Security Notes

`GOPICKLE-001` does not claim to prove that packaged code is safe.

It helps reduce hidden packaging behavior by making included source and generated handoff artifacts easier to audit.

## Non-Goals

This spec does not replace:

- source review
- dependency scanning
- module signing
- artifact provenance systems
- CI hardening
- sandboxing
