# Security Policy

Reviewable Workflow Handoffs is a visibility and auditability project.

It does not replace dependency scanning, code review, package signing, sandboxing, CI security, SLSA, OpenSSF Scorecard, Sigstore, SBOMs, or runtime policy enforcement.

## Supported Scope

This repo contains specs, concepts, threat model notes, comparisons, and shared documentation.

Security-sensitive issues may include:

- misleading security claims
- spec language that hides execution behavior
- unsafe recommendations for workflow execution
- unclear boundaries between specs and reference implementations
- documentation that encourages unreviewed execution or unreviewed source consumption

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

> Reviewable workflow handoffs reduce hidden workflow behavior and make handoffs easier to audit before execution or consumption.

Do not make broad prevention claims about supply-chain attacks.
