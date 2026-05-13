# Threat Model

Reviewable Workflow Handoffs is a visibility and auditability effort.

It does not claim to prevent all supply-chain attacks.

## Helps With

Reviewable handoffs can help reduce:

- hidden execution paths
- undocumented local source transfer
- unreviewed workflow changes
- unclear package or local repository boundaries
- reliance on tribal knowledge for build and source handoff behavior
- surprises between local and CI behavior

## Does Not Solve

Reviewable Workflow Handoffs does not replace:

- dependency scanning
- code review
- package signing
- SBOMs
- SLSA
- OpenSSF Scorecard
- Sigstore
- sandboxing
- CI hardening
- secret management
- runtime policy enforcement
- maintainer trust decisions

## Main Claim

The correct security claim is:

> Reviewable workflow handoffs reduce hidden workflow behavior and make handoffs easier to audit before execution or consumption.

Do not make broad prevention claims about supply-chain attacks.

## Reviewer Questions

Before trusting a handoff, a reviewer should be able to ask:

- What is being handed over?
- What will execute or consume it?
- What files, commands, metadata, generated artifacts, caches, or local repositories are involved?
- What changed since the previous version?
- What behavior still depends on trust outside the repo?
