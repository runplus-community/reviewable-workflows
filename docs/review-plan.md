# Review Plan

This plan is for the first technical review of Reviewable Workflow Handoffs before tagging `v0.1.0-draft`.

## Review Target

Primary repo:

- [`runplus-community/reviewable-workflows`](https://github.com/runplus-community/reviewable-workflows)

Reference implementations:

- [`gopickle`](https://github.com/runplus-community/gopickle): Go source handoffs through local `GOPROXY`
- [`rustpickle`](https://github.com/runplus-community/rustpickle): Rust source handoffs through Cargo source or patch configuration
- [`goshbuild`](https://github.com/runplus-community/goshbuild): Go execution handoffs through `.run.sh` runners
- [`rushbuild`](https://github.com/runplus-community/rushbuild): Rust execution handoffs through `.run.sh` runners

## Reviewer Questions

Ask reviewers:

- Is "handoff" understandable as the core term?
- Is the source handoff vs execution handoff split clear?
- Does `gopickle` as a `GOPROXY` source handoff make sense?
- Does `rustpickle` mirror the source-handoff idea well through Cargo source or patch config?
- Are the security claims restrained enough?
- Do the four reference tools feel connected to the spec rather than like unrelated CLIs?

## GitHub Project Tracking

Use the RunPlus Community GitHub Project to track review work:

- Project: <https://github.com/orgs/runplus-community/projects/1/views/1>

Use `gh` for project updates when the local token has GitHub Projects scope.

Current check:

```bash
gh project view 1 --owner runplus-community --format json
```

If `gh` reports a missing `read:project` scope, refresh auth first:

```bash
gh auth refresh -h github.com -s read:project
```

For write updates to the project, the token may also need project write scope:

```bash
gh auth refresh -h github.com -s project
```

After access is available, update the project board with review tasks for:

- spec terminology review
- source/execution split review
- `gopickle` / `GOPROXY` review
- `rustpickle` / Cargo source handoff review
- security and non-goals review
- post-review polish pass
- `v0.1.0-draft` tag decision

## Release Gate

Do not tag `v0.1.0-draft` until:

- at least 3 technical reviewers have given feedback
- terminology feedback has been triaged
- security-claim wording has been rechecked
- one post-review polish pass has been merged to `main`
