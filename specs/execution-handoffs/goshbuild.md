# GOSHB-001: Reviewable Go Execution Handoff

Status: Draft

Handoff type: Reviewable Execution Handoff

Language: Go

Reference implementation: [`runplus-community/goshbuild`](https://github.com/runplus-community/goshbuild)

## Purpose

`GOSHB-001` defines a reviewable Go execution handoff using a source-preserving shell runner.

The goal is to make Go build and execution behavior visible, versioned, and reviewable before it runs locally or in CI.

> Do not execute what you cannot review.

## Reviewability Goal

A reviewer should be able to inspect:

- which Go module or source tree is being handed off
- which generated runner will execute
- what source payload or source reference is included
- what checksum or integrity marker protects the payload
- how extraction happens
- which Go build command runs
- how cache identity is derived
- what executable receives the original arguments

## Inputs

Expected inputs include:

- Go module source directory
- `go.mod`
- Go source and asset files
- optional ignore rules
- output runner path

The reference implementation runs `go mod vendor` before packing so vendored dependencies can travel with the source payload.

## Outputs

Visible outputs may include:

- self-contained `.run.sh` runner
- acceptance test script for the runner
- embedded base64 tar payload
- payload SHA-256
- conversion artifacts
- pack transcript
- cache directory entries at runtime

## Required Visible Metadata

A conforming implementation should expose enough metadata to identify:

- module name
- source directory
- payload hash
- runner path
- test path, if generated
- build/cache identity inputs

## Security Notes

This spec does not guarantee safe execution.

It helps make Go execution handoff easier to inspect before local or CI execution.

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
- normal code review
