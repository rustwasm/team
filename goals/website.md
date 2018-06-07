# Goal: Website

We should have compelling informational material and demos of Rust and
WebAssembly for the 2018 Rust website revamp.

## Owner

**Nick Fitzgerald**

- GitHub: [fitzgen](https://github.com/fitzgen)
- IRC nick: `fitzgen`
- Email: fitzgen@mozilla.com

## Details

For the 2018 edition, the Rust website is getting overhauled, and each of the
domain working groups will have some real estate to show off Rust in their
domain.

We should have:

* A live-editable, interactive playground (perhaps use
  https://webassembly.studio ?)  for Rust and Wasm that can be included.

  * With cool, pre-loaded demo programs

* Introductory material for our tooling and ecosystem, including:

  * `wasm-bindgen`

  * `wasm-pack`

  * Integrating nicely with JS

* Some information about why Rust is particularly well-suited for the Web. We
  can probably reuse a lot of the ["Vision" section from the `rustwasm/team`'s
  `README.md`][vision].

More details about this goal. What is in scope for the 2018 edition. What comes
after that.

## How to Help

The new Rust website's repository is [`rust-lang/wubwub`][wubwub]. This is a
private repository, ping `@fitzgen` if you would like to contribute directly to
it, and would like access.

We need help with coming up with and writing small and digestible but still cool
and compelling demo programs for the interactive playground. [Open issues on the
`rustwasm/team` repository for brainstorming and proposing such programs.][open]

[vision]: https://github.com/rustwasm/team/blob/master/README.md#vision
[wubwubwub]: https://github.com/rust-lang/wubwub
[open]: https://github.com/rustwasm/team/issues/new
