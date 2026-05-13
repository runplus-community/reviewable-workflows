# RUSTPICKLE-001: Reviewable Rust Source Handoff

Status: Draft

Handoff type: Reviewable Source Handoff

Language: Rust

Reference implementation: [`runplus-community/rustpickle`](https://github.com/runplus-community/rustpickle)

## Purpose

`RUSTPICKLE-001` defines a reviewable Rust source handoff using a local file-backed Cargo source.

The goal is to make local Rust crate reuse visible, versioned, and reviewable before another Rust crate consumes it.

> Do not bundle what you cannot inspect.

## Reviewability Goal

A reviewer should be able to inspect:

- which crate or workspace is being exposed
- which files are included in the generated Cargo source
- which files are intentionally excluded
- which crate version is assigned
- which generated Cargo source artifacts are produced
- which Cargo `source` or `[patch.crates-io]` config a consumer project will use

## Inputs

Expected inputs include:

- one or more `Cargo.toml` manifests
- source files under the crate root
- optional version token or explicit `--crate-version`
- optional comment metadata
- optional auto-discovery from the current directory

## Outputs

The reference implementation writes a Cargo directory source under `.local/cargo/<pickle>/directory/`.

For a crate version, visible outputs include:

- rewritten or copied `Cargo.toml`
- source files
- `.cargo-checksum.json`
- `.rustpickle_info`
- Cargo source replacement config
- optional Cargo patch config

## Required Visible Metadata

A conforming implementation should expose enough metadata to identify:

- crate name
- crate version
- source root
- generated artifact paths
- generation time or equivalent build marker
- optional user comment, if supplied

## Security Notes

This spec does not prove that source is safe.

It helps make local Rust source handoff easier to inspect before consumption.

## Non-Goals

This spec does not replace:

- SLSA
- OpenSSF Scorecard
- SBOMs
- crate signing
- dependency scanning
- provenance systems
- CI hardening
- sandboxing
- normal source review
