# Examples

This repo is the spec and thesis layer for Reviewable Workflow Handoffs.

Runnable examples live in the reference implementation repos so the examples stay close to the code that exercises them.

## Source Handoff Examples

### Go: `gopickle`

`gopickle` demonstrates reviewable Go source handoffs through a local file-backed `GOPROXY`.

- Repo: [`runplus-community/gopickle`](https://github.com/runplus-community/gopickle)
- Spec: [`GOPICKLE-001`](../specs/source-handoffs/gopickle.md)
- Library module example: [`examples/hello`](https://github.com/runplus-community/gopickle/tree/dev/examples/hello)
- Consumer module example: [`examples/hello-usage-module`](https://github.com/runplus-community/gopickle/tree/dev/examples/hello-usage-module)
- Demo script: [`examples/gofeed-standrd-local-repo.gopickle.sh`](https://github.com/runplus-community/gopickle/blob/dev/examples/gofeed-standrd-local-repo.gopickle.sh)

Review question:

> What local Go library source is being exposed through `GOPROXY`, and what proxy artifacts will the consumer project use?

### Rust: `rustpickle`

`rustpickle` demonstrates reviewable Rust source handoffs through Cargo-native source and patch configuration.

- Repo: [`runplus-community/rustpickle`](https://github.com/runplus-community/rustpickle)
- Spec: [`RUSTPICKLE-001`](../specs/source-handoffs/rustpickle.md)
- Crate example: [`examples/hello`](https://github.com/runplus-community/rustpickle/tree/dev/examples/hello)
- Consumer crate example: [`examples/hello-usage-crate`](https://github.com/runplus-community/rustpickle/tree/dev/examples/hello-usage-crate)
- Demo script: [`examples/rustfeed-standrd-local-repo.rustpickle.sh`](https://github.com/runplus-community/rustpickle/blob/dev/examples/rustfeed-standrd-local-repo.rustpickle.sh)

Review question:

> What local Rust crate source is being exposed, and what Cargo source or patch configuration will the consumer crate use?

## Execution Handoff Examples

### Go: `goshbuild`

`goshbuild` demonstrates reviewable Go execution handoffs through a generated `.run.sh` runner.

- Repo: [`runplus-community/goshbuild`](https://github.com/runplus-community/goshbuild)
- Spec: [`GOSHB-001`](../specs/execution-handoffs/goshbuild.md)
- Demo module: [`demo-app`](https://github.com/runplus-community/goshbuild/tree/dev/demo-app)
- Demo harness: [`test_goshbuild.sh`](https://github.com/runplus-community/goshbuild/blob/dev/test_goshbuild.sh)

Review question:

> What source, checksum, build path, and shell runner behavior will execute?

### Rust: `rushbuild`

`rushbuild` demonstrates reviewable Rust execution handoffs through a generated `.run.sh` runner.

- Repo: [`runplus-community/rushbuild`](https://github.com/runplus-community/rushbuild)
- Spec: [`RUSHB-001`](../specs/execution-handoffs/rushbuild.md)
- Demo crate: [`demo-apps/rust-demo`](https://github.com/runplus-community/rushbuild/tree/dev/demo-apps/rust-demo)
- Demo harness: [`test_rushbuild.sh`](https://github.com/runplus-community/rushbuild/blob/dev/test_rushbuild.sh)

Review question:

> What source, checksum, Cargo build path, and shell runner behavior will execute?

## Boundary

Do not copy runnable implementation code into this spec repo.

Specs and examples should link to reference implementations. The supporting repos own executable code, demo apps, generated artifacts, and test harnesses.
