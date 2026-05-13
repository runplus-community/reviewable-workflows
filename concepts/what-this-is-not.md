# What This Is Not

Reviewable Workflow Handoffs is a visibility and reviewability effort.

It is intentionally not a replacement for the surrounding developer tooling and security ecosystem.

## Not A New Universal Build System

Reviewable Workflow Handoffs does not try to replace Make, Just, Task, Bazel, Buck, Pants, Nix, GitHub Actions, or devcontainers.

Those systems define tasks, builds, environments, or CI behavior.

This project focuses on the handoff boundary: what source or execution behavior is being passed to another context, and whether it can be inspected before trust is required.

## Not A Security Guarantee

Reviewable Workflow Handoffs does not make source safe, make shell execution safe, or make supply-chain attacks impossible.

It makes handoffs easier to inspect.

## Not A Replacement For Supply-Chain Controls

Reviewable Workflow Handoffs does not replace:

- SLSA
- OpenSSF Scorecard
- Sigstore
- SBOMs
- dependency scanning
- package signing
- provenance
- CI hardening
- sandboxing
- code review

These practices are complementary.

## Not A Claim That Shell Is Inherently Safer

Shell can be hard to audit.

The claim is narrower: a checked-in, explicit, inspectable handoff artifact can be easier to review than scattered implicit setup, tribal knowledge, or binary-only handoff.

## Not A Claim That Native Package Managers Are Enough

Go and Cargo already provide useful local source and dependency mechanisms.

Reviewable source handoffs define reviewability expectations around those native mechanisms. They do not replace the package managers themselves.
