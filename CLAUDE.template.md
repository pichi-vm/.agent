# <repo> — <one-line purpose>

<Stack and versions — e.g. "Rust (stable), single crate" or
"Rust (nightly-YYYY-MM-DD; artifact deps), workspace".>

## Commands

```sh
cargo fmt --all -- --check
RUSTFLAGS=-D warnings cargo clippy --all-targets --all-features
RUSTFLAGS=-D warnings cargo test
# plus, as this repo's CI runs them: hawkeye check · cargo deny check · gitlint
```

## Done

Green on this repo's full CI job set (above) before reporting done.

## Crates

<one line per workspace member: name -> role. Omit for a single-crate repo.>

## Rules

<repo-specific always/ask/never beyond the shared rules — e.g. dual-licensed or
derived files, generated code, spec-authoritative docs.>

<!-- Shared rules live in the .agent submodule. If .agent/ is empty, run:
     git submodule update --init --recursive -->
@.agent/karpathy/CLAUDE.md
@.agent/pichi.md
@.agent/rust.md
