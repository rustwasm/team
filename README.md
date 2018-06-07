<meta charset="utf-8"/>

# Rust + WebAssembly = 💖

This repository is a simple, organic means of coordinating work on using Rust
and WebAssembly together.

<!--
doctoc README.md --maxlevel 1
-->

<!-- Generated with https://github.com/thlorenz/doctoc -->
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Vision](#vision)
- [Get Involved!](#get-involved)
- [Status](#status)
  - [The Rust compiler](#the-rust-compiler)
  - [The Rust standard library](#the-rust-standard-library)
  - [JS Interop](#js-interop)
    - [The JS package ecosystem](#the-js-package-ecosystem)
    - [The DOM, GC integration, and more](#the-dom-gc-integration-and-more)
  - [The crate ecosystem](#the-crate-ecosystem)
- [Demos, talks and more](#demos-talks-and-more)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Vision

**Compiling Rust to WebAssembly should be *the* best choice for fast code for
the Web.**

JavaScript Web applications struggle to attain reliable performance.
JavaScript's dynamic type system and garbage collection pauses don't
help. Seemingly small code changes can result in drastic performance regressions
if you accidentally wander off the JIT's happy path.

Rust gives programmers low-level control and reliable performance. It is free
from the non-deterministic garbage collection pauses that plague JavaScript.
Programmers have control over indirection, monomorphization, and memory layout.

And now we can bring Rust's advantages to the Web with WebAssembly.

**Rust is particularly well-suited for the Web.**

Rust's minuscule runtime enables small `.wasm` sizes and incremental or partial
adoption.

* Small `.wasm` sizes: Code size is incredibly important since the `.wasm` must
be downloaded over the network.

* Incremental or partial adoption: Existing code bases don't need to be thrown
away. Programmers can start by porting their most performance-sensitive
JavaScript functions to Rust to gain immediate benefits. And they can even stop
there if they want to, because Rust plays well with others.

Furthermore, Rust has many of the amenities that Web developers have come to
expect:

* strong package management with `cargo`,

* expressive (and zero-cost!) abstractions,

* and a welcoming community 😊

We envision the pipeline that fits Rust into JavaScript package management and
bundler ecosystem to look something like this:

<img alt="Rust to WebAssembly to NPM to bundler to Webpage pipeline" src="./pipeline.png"/>

# Get Involved!

Get involved with the Rust and WebAssembly community in three easy steps!

## 1. Join our IRC Chat

Chat with the Rust and WebAssembly community on IRC at [`#rust-wasm` on
`irc.mozilla.org`][irc].

If you don't have an IRC client of choice already, you can use the [Mibbit Web
IRC client][irc-web-client].

Say "hello" and introduce yourself!

## 2. Do some Rust and WebAssembly Yourself

Read our short [Rust and WebAssembly book][book], complete the [tutorials][],
and compile some Rust into WebAssembly. If you ran into a paper cut or
roadblock, [let us know by filing an issue!][file-issue]

## 3. Join the Rust and WebAssembly Working Group

We meet on Google Hangouts every two weeks to track progress, give status
updates, and discuss issues. We coordinate meetings with [issues labeled
"meeting" in the `rustwasm/team` repository][meetings].

First get your feet wet by tackling one of these issues:

* [Issues labeled "good first issue" in the `rustwasm/*` repositories][good-first-issue]

* [Issues labeled "help wanted" in the `rustwasm/*` repositories.][help-wanted]

Then help us make progress on the working group goals:

| Goal                           | Owner     | More Information |
|--------------------------------|-----------|------------------|
| `wasm-bindgen` ecosystem       | fitzgen   |                  |
| Publishing and Dependencies    | ag_dubs   |                  |
| Bundler Integration            | xtuc      |                  |
| Book, Documentation, Tutorials | mgattozzi |                  |
| Website                        | fitzgen   |                  |
| Debugging                      | fitzgen   |                  |
| Templates                      | fitzgen   |                  |
| Testing                        | ?         |                  |
| Benchmarking                   | ?         |                  |

See also [`GOVERNANCE.md#membership`][membership].

[help-wanted]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3Arustwasm+archived%3Afalse+label%3A%22help+wanted%22
[good-first-issue]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3Arustwasm+archived%3Afalse+label%3A%22good+first+issue%22
[meetings]: https://github.com/issues?utf8=%E2%9C%93&q=user%3Arustwasm+label%3Ameeting+
[membership]: https://github.com/rustwasm/team/blob/master/GOVERNANCE.md#membership
[book]: https://rustwasm.github.io/book
[tutorials]: https://rustwasm.github.io/book/tutorials.html
[irc]: irc://irc.mozilla.org#rust-wasm
[irc-web-client]: https://client00.chat.mibbit.com/?channel=%23rust-wasm&server=irc.mozilla.org
[file-issue]: https://github.com/rustwasm/team/issues/new

# Status

## The Rust compiler

The Rust compiler currently supports two wasm-related targets:

- `wasm32-unknown-unknown`. This target compiles directly to wasm using the LLVM
  back-end. It's appropriate when you're compiling pure Rust code, i.e. you have
  no C dependencies. Compared to the emscripten target, it produces much leaner
  code by default and is much easier to set
  up. [Here's how to set it up](https://rust-lang-nursery.github.io/rust-wasm/setup.html).

- `wasm32-unknown-emscripten`. This target compiles to wasm via the emscripten
  toolchain. It's what you should use if you have C dependencies, including
  libc. [Here's how to set it up](https://www.hellorust.com/setup/emscripten/).

The `wasm32-unknown-unknown` target is particularly promising for integrating bits of
"greenfield" Rust code into JS projects. However, it is also the less mature
backend.

## The Rust standard library

Each of the wasm targets has a different story with respect to `std`:

- For `wasm32-unknown-unknown`, Rust emits its own, very small allocator that
  sits on top of the wasm page allocator described above. That means that all
  APIs at the `alloc` level (i.e., all container types) are available. APIs that
  exist only within `std` -- threads, networking, files, processes -- are not
  available for this target. Today, the APIs are present but panic or error out
  upon use. In the future, we plan to `cfg` out the APIs for this target.

  Over time, as the wasm spec grows, some of these additional APIs (notably
  threading) may return.

- For `wasm32-unknown-emscripten`, Rust uses the emscripten toolchain to provide
  libc-based functionality. That means that a lot of `std` is available and
  works, but at the cost of significant `.wasm` size bloat.

## JS Interop

### The JS package ecosystem

In the book we focused on the details of [function-level interop][book-interop].
But in practice, it's vital to interoperate at the *package* level as well, which
means producing and consuming npm packages.

As of today the story for this sort of interop is largely still in flux, but
there's lots of progress on lots of fronts to cover as well! The crucial
lynchpin of the assumed integration point is **ES6 Modules**. Although [this
requires a polyfill][es6-wasm] the abstraction of ES6 modules for wasm as well
as JS has shown to be beneficial to consumers and bundlers alike.

[book-interop]: https://rust-lang-nursery.github.io/rust-wasm/js-ffi.html
[es6-wasm]: https://github.com/WebAssembly/design/issues/1087

This part of the story is still in the design phase, but here are
some constraints:

- Consumers of Rust/wasm-based packages should be completely unaware that Rust
  is involved. In particular, using such a package should *not* require a local
  Rust toolchain.
  - This means that publication to npm is done in *binary* form: we upload a
    `.wasm` file containing the fully-compiled Rust code.
  - JS is expected to consume Rust through ES6 `import` statements which end up
    resolving to the compiled module.

- You should be able to *work on* the Rust portion of the library using standard
  Cargo workflows.

- There should be a [straightforward way][metadata] to express npm metadata (i.e.
  the contents of `package.json`) for a Rust/wasm project.

  - That means, in particular, that a Rust project might pull in several crates,
    *each* of which pulls in their own npm package dependencies.

- There should be an [easy way][npm-publish] to publish such a project to npm,
  handling all needed [transitive dependencies][rust-deps].

Ultimately, JS bundlers (like [WebPack] and [Parcel]) will need to understand
wasm-based npm packages and generate the appropriate module instantiation. This
is expected to happen through bundlers interpreting wasm modules as ES6 modules
and generating appropriate instantiation glue. Work in this direction is [under
way][bundlers].

[WebPack]: https://webpack.js.org/
[Parcel]: https://parceljs.org/
[bundlers]: https://github.com/aturon/rust-wasm/issues/8
[metadata]: https://github.com/rustwasm/team/issues/34
[rust-deps]: https://github.com/rustwasm/team/issues/36
[npm-publish]: https://github.com/rustwasm/team/issues/35

### The DOM, GC integration, and more

There is some confusion about whether wasm code can work with the DOM today, or
whether that's effectively blocked on GC integration.

To clear this up: **wasm is quite capable of working with the DOM today**. You
can employ strategies like those in [`wasm-bindgen`][wasm-bindgen] to operate on
the DOM via calls back into JS. However, such calls impose an overhead cost.

Efficiency gains are most easily achieved by batching DOM
interactions. Improvements to the DOM, like the [changelist proposal], and
improvements to WebAssembly, like the
[Host Bindings proposal](https://github.com/WebAssembly/design/issues/1148),
will further smooth the path.

[changelist proposal]: https://github.com/whatwg/dom/issues/270

## The crate ecosystem

There's a nascent ecosystem within crates.io for working with wasm. The most
prominent so far are:

- [stdweb], a "standard library for the client-side web".
- [Yew], a framework for client-side web apps.

[stdweb]: https://github.com/koute/stdweb/
[Yew]: https://github.com/DenisKolodin/yew

# Demos, talks and more

- Numerous Rust-centric resources are available at https://www.hellorust.com/,
including demos, talks, and a news feed tracking significant achievements around
Rust and wasm.
- There are also many general wasm resources:
  - http://webassembly.org/
  - https://github.com/mbasso/awesome-wasm
  - http://wasmweekly.news/
