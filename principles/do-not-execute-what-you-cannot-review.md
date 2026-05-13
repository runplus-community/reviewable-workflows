# Do Not Execute What You Cannot Review

Execution handoffs should make commands, scripts, runners, generated files, and runtime assumptions visible before they run.

This principle applies to local shells, CI jobs, generated runners, build scripts, package hooks, and any workflow behavior that crosses into an execution context.

Expected properties:

- the execution handoff is visible before it runs
- the commands or runner behavior can be inspected
- changes to the handoff are version-controlled
- workflow changes can be reviewed in pull requests like other code changes

This does not mean execution is automatically safe. It means the execution path is visible enough for review, discussion, and audit.
