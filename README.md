<meta charset="utf-8"/>

# Rust + WebAssembly = 💖

This repository is a simple, organic means of coordinating work on using Rust
and WebAssembly together.

# Get Involved!

Get involved with the Rust and WebAssembly community in just **three easy
steps!**

## 1. Join our Chat

Chat with the Rust and WebAssembly community in [the `#wg-wasm` channel of
the Rust project's Discord server][discord].

Say "hello" and introduce yourself!

## 2. Do some Rust and WebAssembly Yourself

Read our short [Rust and WebAssembly book][book], complete its [tutorial][], and
compile some Rust into WebAssembly. If you run into a paper cut or roadblock,
[let us know by filing an issue!][file-issue-book]

## 3. Join the Rust and WebAssembly Working Group

We are building a Rust and WebAssembly future where:

* The Web is the primary target.
* Rust plays nice with JavaScript, and can surgically replace a
  performance-sensitive JavaScript module or function without throwing away the
  existing code base.

We are not focusing on (but still encourage others to experiment with) scenarios
where:

* The Web is not the primary target (e.g. WebAssembly as a universal binary
  format, or an operating system that runs WebAssembly processes instead of
  native code).
* A Web application is written in pure Rust, without integrating with any
  JavaScript.

We meet on [Zoom](https://zoom.us/) every week to track progress, give status
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
[tutorial]: https://rustwasm.github.io/book/game-of-life/introduction.html
[irc]: irc://irc.mozilla.org#rust-wasm
[discord]: https://discord.gg/hBjKfhP
[irc-web-client]: https://client00.chat.mibbit.com/?channel=%23rust-wasm&server=irc.mozilla.org
[file-issue]: https://github.com/rustwasm/team/issues/new
[file-issue-book]: https://github.com/rustwasm/book/issues/new
