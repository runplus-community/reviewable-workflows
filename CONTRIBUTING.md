# Contributing

Thanks for contributing to Reviewable Workflow Handoffs.

This repo is the spec and documentation layer for `runplus-community` Reviewable Workflow Handoffs.

## Repo Boundary

Use this repo for:

- specs
- concepts
- threat model notes
- comparisons
- cross-project documentation
- links to reference implementations

Do not add runnable implementation code here. Code, demos, test harnesses, and generated artifacts belong in the supporting repos:

- [`goshbuild`](https://github.com/runplus-community/goshbuild)
- [`rushbuild`](https://github.com/runplus-community/rushbuild)
- [`gopickle`](https://github.com/runplus-community/gopickle)
- [`rustpickle`](https://github.com/runplus-community/rustpickle)

## Contribution Priorities

Good contributions improve:

- clarity
- smallness
- inspectability
- reproducibility
- documentation quality
- security notes
- links between specs and reference implementations

Avoid heavy abstractions unless they make workflow behavior easier to review.

## Changing Specs

When changing a spec:

- keep the spec ID stable
- explain the review surface
- state security non-goals
- link to the reference implementation
- avoid adding requirements that the reference implementation cannot exercise

## Security Issues

Do not report suspected security vulnerabilities in a public issue.

Use GitHub's private vulnerability reporting flow if it is available for this repo. If it is not available, contact the maintainers through a private channel before publishing details.
