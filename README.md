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

Then help us make progress on the working group goals. To learn more about or
contribute towards a particular goal, read its `goals/*.md` page and its "How to
Help" section. If you have any questions about a goal, contact its owner.

| Goal                           | More Information                                                                                                            |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| `wasm-bindgen` Ecosystem       | [goals/wasm-bindgen-ecosystem.md](https://github.com/rustwasm/team/blob/master/goals/wasm-bindgen-ecosystem.md)             |
| Publishing and Dependencies    | [goals/publishing-and-dependencies.md](https://github.com/rustwasm/team/blob/master/goals/publishing-and-dependencies.md)   |
| Bundler Integration            | [goals/bundler-integration.md](https://github.com/rustwasm/team/blob/master/goals/bundler-integration.md)                   |
| Book, Documentation, Tutorials | [goals/book-documentation-tutorials.md](https://github.com/rustwasm/team/blob/master/goals/book-documentation-tutorials.md) |
| Website                        | [goals/website.md](https://github.com/rustwasm/team/blob/master/goals/website.md)                                           |
| Debugging                      | [goals/debugging.md](https://github.com/rustwasm/team/blob/master/goals/debugging.md)                                       |
| Project Templates              | [goals/project-templates.md](https://github.com/rustwasm/team/blob/master/goals/project-templates.md)                       |
| Testing                        | [goals/testing.md](https://github.com/rustwasm/team/blob/master/goals/testing.md)                                           |
| Benchmarking                   | [goals/benchmarking.md](https://github.com/rustwasm/team/blob/master/goals/benchmarking.md)                                 |

Finally, if you've gotten this far, see [`GOVERNANCE.md#membership`][membership]
for information on becoming an official member of the working group!

[help-wanted]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3Arustwasm+archived%3Afalse+label%3A%22help+wanted%22
[good-first-issue]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3Arustwasm+archived%3Afalse+label%3A%22good+first+issue%22
[meetings]: https://github.com/issues?utf8=%E2%9C%93&q=user%3Arustwasm+label%3Ameeting+
[membership]: https://github.com/rustwasm/team/blob/master/GOVERNANCE.md#membership
[book]: https://rustwasm.github.io/book
[tutorials]: https://rustwasm.github.io/book/tutorials.html
[irc]: irc://irc.mozilla.org#rust-wasm
[irc-web-client]: https://client00.chat.mibbit.com/?channel=%23rust-wasm&server=irc.mozilla.org
[file-issue]: https://github.com/rustwasm/team/issues/new
