# Do Not Execute What You Cannot Review

> Do not execute what you cannot review.

This is the core Reviewable Workflows principle.

Developer tooling often asks maintainers to run scripts, generators, hooks, package commands, and CI steps whose behavior is difficult to inspect before execution.

Reviewable Workflows pushes that behavior into committed, inspectable files.

## What Should Be Reviewable

- shell workflows
- generated runners
- build steps
- test steps
- extraction steps
- packaging steps
- dependency handoff steps
- CI workflow behavior

## Pull Request Standard

A workflow change should be reviewed like a code change.

A reviewer should be able to see:

- what will run
- why it changed
- what files it affects
- what generated outputs it creates
- what security assumptions it makes

If a workflow cannot be reviewed from committed files, it should be made more explicit before it becomes the default path.
