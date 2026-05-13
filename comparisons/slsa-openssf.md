# Comparison: SLSA, OpenSSF, and Reviewable Workflow Handoffs

Reviewable Workflow Handoffs is adjacent to supply-chain security work. It does not replace it.

## Main Difference

Reviewable Workflow Handoffs focuses on pre-execution and pre-consumption visibility.

It asks:

- What files or source content are being handed over?
- What commands or workflow behavior will run?
- What generated artifact or local repository will the receiver trust?
- Can a reviewer inspect the handoff before use?

SLSA, OpenSSF Scorecard, Sigstore, SBOMs, provenance systems, dependency scanning, and package signing address related but different parts of the software supply-chain problem.

## Relationship

| Practice | Primary focus | Relationship to Reviewable Workflow Handoffs |
| --- | --- | --- |
| SLSA | Build integrity and provenance levels | Complementary; handoff reviewability can make workflow inputs and execution paths easier to inspect before provenance is produced. |
| OpenSSF Scorecard | Repository security posture checks | Complementary; Scorecard can evaluate repo practices, while handoff specs define project-specific review surfaces. |
| Sigstore | Signing and verifying artifacts | Complementary; signatures can identify artifacts, but reviewers still need to understand what the handoff does. |
| SBOMs | Software component inventory | Complementary; SBOMs describe components, while handoff reviewability describes source/command transfer behavior. |
| Dependency scanning | Known vulnerability detection | Complementary; scanning does not explain all local workflow or handoff behavior. |
| CI hardening | Secure CI execution environment | Complementary; Reviewable Workflow Handoffs clarifies what CI is being asked to run or consume. |

## Credible Claim

Use:

> Reviewable workflow handoffs reduce hidden workflow behavior and make handoffs easier to audit before execution or consumption.

Do not use:

> Reviewable Workflow Handoffs makes supply-chain attacks impossible.

## Practical Position

Reviewable Workflow Handoffs should be treated as a visibility layer.

It can make a project easier to review before execution or consumption, but it still depends on normal security practices:

- code review
- dependency review
- signing
- provenance
- CI controls
- sandboxing where appropriate
- maintainer judgment
