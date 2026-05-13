# Spec Sketch: npm Reviewable Handoffs After Axios 2026

Status: Exploratory

This sketch translates the Axios 2026 case study into possible npm-focused Reviewable Workflow Handoffs specs.

It is not a proposal for a new package manager. It is a visibility layer for package contents, dependency metadata, lifecycle scripts, provenance, and install behavior.

## Why npm Needs A Handoff Lens

In npm, dependency installation can cross several trust boundaries before application code runs:

- package registry to developer machine
- package registry to CI system
- package manifest to transitive dependency graph
- package tarball to local filesystem
- lifecycle script to shell execution
- install-time script to network download

The Axios 2026 compromise shows that a dangerous handoff can be hidden in package metadata and install-time behavior.

## Candidate Specs

### NPM-SOURCE-HANDOFF-001

Purpose:

Make npm package contents and dependency changes reviewable before a project consumes a package version.

Review surface:

- package name and version
- package tarball digest
- included files manifest
- dependency diff from previous version
- lifecycle script inventory
- source repository URL
- source commit, tag, or release link when available
- provenance or trusted-publishing status when available

Non-goal:

This does not prove that package contents are safe.

### NPM-EXECUTION-HANDOFF-001

Purpose:

Make install-time execution behavior reviewable before lifecycle scripts run locally or in CI.

Review surface:

- direct lifecycle scripts
- transitive lifecycle scripts
- commands that would run during install
- package that owns each script
- new scripts compared with the previous lockfile or dependency state
- declared network access, if available
- policy decision: allow, warn, block, or require manual review

Non-goal:

This does not guarantee safe execution.

### PACKAGE-REGISTRY-HANDOFF-001

Purpose:

Make registry-to-consumer handoffs reviewable across package ecosystems.

Review surface:

- package identity
- artifact digest
- source link
- provenance metadata
- publish actor or automation identity where available
- package-content diff
- dependency diff
- install-time behavior summary

Non-goal:

This does not replace registry security, maintainer account protection, signing, provenance, malware scanning, or dependency review.

## Possible User Flows

### Developer Install Preview

```text
package manager resolves dependency update
        |
        v
handoff manifest is generated
        |
        v
developer reviews package diff and lifecycle scripts
        |
        v
install proceeds only after policy allows it
```

### CI Gate

```text
pull request changes lockfile
        |
        v
CI generates handoff review
        |
        v
new lifecycle scripts or missing provenance are flagged
        |
        v
maintainer approves, rejects, or requests investigation
```

### Registry View

```text
new package version is published
        |
        v
registry shows source link, provenance status, tarball diff, dependency diff, lifecycle scripts
        |
        v
consumer sees review surface before install
```

## High-Signal Changes

The spec should avoid asking humans to review every byte for every install.

High-signal changes include:

- new lifecycle scripts
- new dependencies with lifecycle scripts
- package contents that do not match a tagged release
- missing provenance for a package that usually has provenance
- newly introduced install-time network behavior
- major tarball content changes without corresponding source changes
- dependency updates that cross trust boundaries

## Relationship To Existing Tools

This sketch should complement:

- npm lockfiles
- `npm install --ignore-scripts`
- npm provenance and trusted publishing
- package signing
- malware scanning
- dependency scanning
- SBOMs
- SLSA
- OpenSSF Scorecard
- CI hardening

It should not claim to replace any of them.

## Open Questions

- Should lifecycle scripts be disabled by default in high-risk contexts?
- Should registries expose package-content diffs as first-class metadata?
- Should CI systems require explicit approval for new lifecycle scripts?
- How should package managers represent source-to-registry mismatch?
- Can handoff manifests be standardized across npm, PyPI, crates.io, and Go modules?
- What is the minimum useful metadata that does not create too much ecosystem friction?

## Safe Claim

> npm-focused Reviewable Workflow Handoffs would not guarantee prevention of package compromise, but they could make package contents, dependency changes, lifecycle scripts, and provenance gaps easier to inspect before install-time code runs.
