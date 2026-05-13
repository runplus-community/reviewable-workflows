# GOPICKLE-001: Reviewable Go Source Handoff

Status: Draft

Handoff type: Reviewable Source Handoff

Language: Go

Reference implementation: [`runplus-community/gopickle`](https://github.com/runplus-community/gopickle)

## Purpose

`GOPICKLE-001` defines a reviewable Go source handoff using a local file-backed `GOPROXY`.

The goal is to make local Go module reuse visible, versioned, and reviewable before another Go project consumes it.

> Do not bundle what you cannot inspect.

## Reviewability Goal

A reviewer should be able to inspect:

- which Go module is being exposed
- which files are included in the module zip
- which files are intentionally excluded
- which module version is assigned
- which generated proxy artifacts are produced
- which `GOPROXY` value a consumer project will use

## Inputs

Expected inputs include:

- one or more `go.mod` files
- source files under the module root
- optional version token or explicit `--module-version`
- optional comment metadata
- optional auto-discovery from the current directory

## Outputs

The reference implementation writes standard Go module proxy artifacts under `.local/proxy/<pickle>/`.

For a module version, visible outputs include:

- `list`
- `<version>.mod`
- `<version>.info`
- `<version>.zip`
- `<version>.goproxy_info`

It also prints a shell-safe `GOPROXY` value through `gopickle env <pickle>`.

## Required Visible Metadata

A conforming implementation should expose enough metadata to identify:

- module path
- module version
- source root
- generated artifact paths
- generation time or equivalent build marker
- optional user comment, if supplied

## Security Notes

This spec does not prove that source is safe.

It helps make local Go source handoff easier to inspect before consumption.

## Non-Goals

This spec does not replace:

- SLSA
- OpenSSF Scorecard
- SBOMs
- package signing
- dependency scanning
- provenance systems
- CI hardening
- sandboxing
- normal source review
