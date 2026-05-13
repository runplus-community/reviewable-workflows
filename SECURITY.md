# Security Policy

Reviewable Workflows is a visibility and auditability project.

It does not replace dependency scanning, code review, package signing, sandboxing, CI security, or runtime policy enforcement.

## Supported Scope

This repo contains specs, principles, threat model notes, and shared documentation.

Security-sensitive issues may include:

- misleading security claims
- spec language that hides execution behavior
- unsafe recommendations for workflow execution
- unclear boundaries between specs and reference implementations
- documentation that encourages unreviewed execution

Implementation vulnerabilities should usually be reported in the relevant supporting repo:

- [`goshbuild`](https://github.com/runplus-community/goshbuild)
- [`rushbuild`](https://github.com/runplus-community/rushbuild)
- [`gopickle`](https://github.com/runplus-community/gopickle)
- [`rustpickle`](https://github.com/runplus-community/rustpickle)

## Reporting

Do not report suspected security vulnerabilities in a public issue.

Use GitHub's private vulnerability reporting flow if it is available for this repo. If it is not available, contact the maintainers through a private channel before publishing details.

## Security Claim

The correct project claim is:

> Reviewable workflows reduce hidden execution paths and make workflow behavior easier to audit.

Do not claim that Reviewable Workflows prevents all supply-chain attacks.
