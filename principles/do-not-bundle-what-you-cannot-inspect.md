# Do Not Bundle What You Cannot Inspect

> Do not bundle what you cannot inspect.

This is the Reviewable Workflows principle for packaging, extraction, and local source handoff.

When one project becomes consumable by another project, the included source and generated handoff artifacts should be visible before use.

## What Should Be Inspectable

- source files included in the handoff
- files intentionally excluded from the handoff
- generated package or local repository artifacts
- version or identity metadata
- consumer configuration
- local cache or repository layout

## Why It Matters

Local development often relies on temporary path rewrites, copied folders, unpublished package assumptions, or manual setup steps.

Those approaches can work, but they are easy to forget, hard to review, and hard to reproduce.

Reviewable local source handoff should use explicit files and language-native mechanisms where possible.

Examples:

- Go source handoff through a file-backed `GOPROXY`
- Rust source handoff through a Cargo directory source or patch config

The goal is not to invent a new package manager. The goal is to make local source flow easier to inspect and audit.
