# RUSTPICKLE-001: Reviewable Rust Local Source Handoff Workflow

Status: Draft

Reference implementation: [`runplus-community/rustpickle`](https://github.com/runplus-community/rustpickle)

## Purpose

`RUSTPICKLE-001` defines a reviewable local source handoff workflow for Rust projects.

The workflow should make local Rust crate reuse explicit by turning a source crate into a file-backed Cargo source that another crate can consume through normal Cargo configuration.

> Do not bundle what you cannot inspect.

## Scope

This spec covers Rust project packaging and local source handoff workflows where included files and generated outputs can be reviewed before another project consumes them.

The reference implementation is `rustpickle`, which creates a local file-backed Cargo source from Rust crates.

## Reviewability Requirements

A `RUSTPICKLE-001` workflow should make these things visible:

- the crate or workspace being exposed locally
- the files included in the generated Cargo source
- the generated Cargo source artifacts, including `Cargo.toml`, `.cargo-checksum.json`, and metadata
- the version or identity assigned to the package
- the Cargo `source` or `patch` configuration needed by a consumer project
- any files intentionally excluded from the package

A reviewer should be able to inspect what will be bundled or exposed before another project consumes it.

## Expected Properties

- The packaging workflow should be repeatable.
- Included and excluded files should be explainable.
- Generated outputs should use language-native Cargo concepts where practical.
- Consumer projects should keep normal Cargo behavior where possible.
- Local reuse should avoid ad hoc copying when a language-native local source path can be made explicit.
- The workflow should remain small enough to inspect.

## Security Notes

`RUSTPICKLE-001` does not claim to prove that packaged code is safe.

It helps reduce hidden packaging behavior by making included source and generated handoff artifacts easier to audit.

## Non-Goals

This spec does not replace:

- source review
- dependency scanning
- crate signing
- artifact provenance systems
- CI hardening
- sandboxing
