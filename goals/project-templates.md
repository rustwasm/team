# Goal: Project Templates

We should provide high-quality, opinionated templates for jump-starting Rust and
WebAssembly projects.

## Owner

**Nick Fitzgerald**

- GitHub: [fitzgen](https://github.com/fitzgen)
- IRC nick: `fitzgen`
- Email: fitzgen@mozilla.com

## Details

We should provide a template (or templates) with all of our tooling, libraries,
and ecosystem bundled. Users shouldn't have to fiddle around or do a bunch of
work to install the toolchain and development environment manually, they should
get everything out of the box. Once `cargo` supports initializing new projects
from a template, we should support that system.

For Rust 2018 edition, we should have:

* [X] A template for jump-starting Rust and WebAssembly projects

  * [ ] That is focused on writing wasm modules in Rust -- not "owning" the way
        that the wasm and JS end up on the Webpage.

  * [ ] That uses a pure-Rust post-build pipeline instrumented by
        `wasm-pack`. This is necessary so that Rust developers can share wasm
        libraries without needing a whole JS toolchain installed.

  * [ ] That plays nice with `cargo`'s template system.

Longer term goals:

* More different kinds of templates for different scenarios and JS bundlers.

## How to Help

Relevant repositories:

* [`rustwasm/rust_wasm_template`](https://github.com/rustwasm/rust_wasm_template)

* [`rust-lang/cargo`](https://github.com/rust-lang/cargo)

Things we need help with:

* [ ] [Help add support for custom templates to
      `cargo`.](https://github.com/rust-lang/cargo/issues/5151)

* [Open issues in the `rustwasm/rust_wasm_template`
  repository.](https://github.com/rustwasm/rust_wasm_template/issues)

* Generally molding `rustwasm/rust_wasm_template` into the ideal template
  described for Rust 2018 edition above.
