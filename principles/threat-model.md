# Threat Model

Reviewable Workflows is a visibility and auditability effort.

It does not claim to prevent all supply-chain attacks.

## Helps With

Reviewable Workflows can help reduce:

- hidden execution paths
- undocumented build behavior
- unreviewed workflow changes
- unclear packaging and extraction boundaries
- reliance on tribal knowledge for project workflows
- surprises between local and CI behavior

## Does Not Solve

Reviewable Workflows does not replace:

- dependency scanning
- code review
- package signing
- sandboxing
- CI hardening
- secret management
- runtime policy enforcement
- maintainer trust decisions

## Main Claim

The correct security claim is:

> Reviewable workflows reduce hidden execution paths and make workflow behavior easier to audit.

Do not claim that Reviewable Workflows prevents supply-chain attacks.

## Reviewer Questions

Before running a workflow, a reviewer should be able to ask:

- What files define the workflow?
- What commands or operations will run?
- What external tools, package managers, or runtimes are involved?
- What files are read, written, generated, cached, vendored, or extracted?
- What changed since the previous version?
- What behavior still depends on trust outside the repo?
