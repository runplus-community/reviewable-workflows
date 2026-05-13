# Prefer Language-Native Handoffs

Reviewable Workflow Handoffs should use ecosystem mechanisms that developers already understand when those mechanisms fit the job.

Language-native handoffs reduce unnecessary invention. They let reviewers inspect the handoff through familiar package manager, build tool, or shell conventions.

Examples:

- Go source handoffs can use `GOPROXY`-style module artifacts.
- Rust source handoffs can use Cargo directory sources, patches, source replacement, or vendoring.
- Execution handoffs can use checked-in shell-visible runners when the runner itself is the review surface.

This is a preference, not a universal rule. A spec may define additional conventions when native tooling does not expose enough review surface, but it should explain why.
