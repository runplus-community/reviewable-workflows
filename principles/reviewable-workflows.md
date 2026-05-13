# Reviewable Workflows

Reviewable Workflows is the idea that developer workflows should be explicit, version-controlled, and reviewable before execution.

Modern projects execute many workflows before the application itself runs:

- build scripts
- test scripts
- package hooks
- CI commands
- code generators
- extraction tools
- shell scripts
- install-time commands

When those workflows are scattered across README files, CI configs, hooks, and tribal knowledge, reviewers cannot easily see what will run.

## Principle

> Developer workflows should be explicit, version-controlled, and reviewable before execution.

The workflow should ship with the code. Workflow changes should be reviewable in pull requests like any other code change.

## Reviewable Means

A workflow is reviewable when a maintainer can answer:

- what files define the workflow
- what commands or operations may run
- what inputs are read
- what outputs are written
- what generated, cached, vendored, or extracted materials are involved
- what changed in the pull request

Reviewability does not mean the workflow is automatically safe. It means the workflow behavior is visible enough to audit.
