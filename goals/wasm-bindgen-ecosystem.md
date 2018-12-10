# Goal: `wasm-bindgen` Ecosystem

We should build an ecosystem of tools and libraries around `wasm-bindgen`.

## Owner

**Nick Fitzgerald**

- GitHub: [fitzgen](https://github.com/fitzgen)
- IRC nick: `fitzgen`
- Email: fitzgen@mozilla.com

## Details

`wasm-bindgen` is a lightweight, only-pay-for-what-you-use, ergonomic solution
to accessing the DOM APIs from Rust and wasm. It is designed to support the
upcoming ["Host Bindings" proposal][host-bindings], which will eliminate the
need for JS shims between wasm and the DOM, unlocking faster DOM access than
JS. We should build an ecosystem of crates and tooling around `wasm-bindgen`.

For Rust 2018 edition, we should have the foundation of this ecosystem in place:

* [ ] `wasm-bindgen` should support all `std::`, `core::`, and builtin Rust
      types.

* [ ] We should have all JS builtin and Web/DOM APIs imported by `wasm-bindgen`
      in a `-sys` style crate so that every downstream user doesn't need to have
      bespoke imports. Something that both root crates and intermediate library
      crates can build upon. This `-sys` crate should be automatically generated
      from WebIDL.

As stretch or longer term goals, we should have:

* [ ] Automatically generated bindings to JS libraries via TypeScript interface
      definitions.

* [ ] Many higher-level libraries built on top of the Web `-sys` crate(s).

## How to Help

This work is largely happening in the [`rustwasm/wasm-bindgen`
repository][wasm-bindgen] right now. Read the ["Contributing"
section][contributing] of its guide to dive into `wasm-bindgen` development.

We need help with:

* Exposing the ECMAScript standard's global functions and objects in the
  `wasm_bindgen::js` module. This is a great way to start with `wasm-bindgen`
  and there is lots of work that can be done in concurrent pull requests from
  various contributors! [Check out the meta issue for more details.][js-globals]

* The WebIDL frontend to `wasm-bindgen`.

  * All DOM and Web APIs are described in WebIDL in their standards, and
    browsers automatically generate glue code from the WebIDL. We can use it to
    automatically generate `wasm-bindgen` imports for all of the Web APIs. This
    is how we will build the Web `-sys` crate(s).

  * The WebIDL-specific code lives in `wasm-bindgen/crates/webidl`.

  * [Issues labeled "frontend:webidl" in the `wasm-bindgen`
    repository.][webidl-issues]

* Supporting more Rust types in imported and exported `wasm-bindgen` functions.

  * [Issues labeled "more-types" in the `wasm-bindgen` repository.][more-types]

* The TypeScript frontend to `wasm-bindgen`.

  * We can automatically generate `wasm-bindgen` imports for a JS library if we
    have TypeScript definitions for it. Most popular libraries have these
    definitions.

  * The TypeScript-specific code lives in `wasm-bindgen/crates/typescript`.

  * Talk to `@spastorino` on IRC or GitHub if you're interested in helping out
    with this project.

  * [Issues labeled "frontend:typescript" in the `wasm-bindgen`
    repository.][typescript-issues]

[host-bindings]: https://github.com/WebAssembly/host-bindings/blob/master/proposals/host-bindings/Overview.md
[wasm-bindgen]: https://github.com/rustwasm/wasm-bindgen
[contributing]: https://rustwasm.github.io/wasm-bindgen/contributing/
[webidl-issues]: https://github.com/rustwasm/wasm-bindgen/issues?q=is%3Aissue+is%3Aopen+label%3Afrontend%3Awebidl
[more-types]: https://github.com/rustwasm/wasm-bindgen/issues?q=is%3Aissue+is%3Aopen+label%3Amore-types
[typescript-issues]: https://github.com/rustwasm/wasm-bindgen/issues?q=is%3Aissue+is%3Aopen+label%3Afrontend%3Atypescript
[js-globals]: https://github.com/rustwasm/wasm-bindgen/issues/275
