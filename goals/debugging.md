# Goal: Debugging

Rust compiled to WebAssembly should be easy to debug.

## Owner

**Nick Fitzgerald**

- GitHub: [fitzgen](https://github.com/fitzgen)
- IRC nick: `fitzgen`
- Email: fitzgen@mozilla.com

## Details

Rust compiled to WebAssembly should have an outstanding debugging story.

That is not yet the case, and debugging issues in a `.wasm` compiled from some
Rust is a pain:

* By default, panics and aborts translate into wasm traps, which translate into
  an exception raised in the host JavaScript. If the developer tools were open
  when this happened, we get a backtrace. If the wasm was built with debug info,
  that backtrace will have Rust function names, otherwise each frame will be
  labeled `wasm-function[123]`.

* There are no guard pages, so stack overflows aren't caught. Even worse, our
  current `lld` lays out memory such that the stack overflows into global data,
  which gets corrupted. This is frustrating to debug.

For Rust 2018 edition, we should have:

* [X] [`console_error_panic_hook`][hook]: A method for logging panics and their
      error message to the browser's developer console, along with a stack
      trace.

  * [ ] Install this panic hook by default in the wasm's `$start` function in
        our project templates.

* [ ] Upgrade our LLVM and `lld` to get access to the `--stack-first` linker
      flag, which will change the memory layout so that a stack overflow will
      overflow off the start of memory and out-of-bounds trap. This will sort of
      simulate guard pages, making stack overflows much easier to debug.

Longer term debugging goals:

* [ ] Standardize some kind of debugging capabilities (DWARF, source maps,
      language server, etc...) and emit it when debug info is enabled, so that
      we can use browser's debuggers to step through Rust source code. This
      involves lots of collaboration with many stakeholders across many
      organizations.

* [ ] Valgrind-esque heap corruption, use-after-free, and double-free tooling
      for `unsafe` Rust in wasm.

* [ ] DTrace-style custom logging and instrumentation tooling for Rust and wasm.

## How to Help

Relevant repositories:

* [`rustwasm/console_error_panic_hook`][hook]

* [`rust-lang/rust`](https://github.com/rust-lang/rust)

Things we need particular help with:

* Improving panic debugging ergonomics:

  * [ ] [Make `rustc` generate a wasm `$start` function for a Rust `[[bin]]`'s
        `main` function.](https://github.com/rustwasm/team/issues/108) This is a
        pre-requisite for installing the `console.error` panic hook inside the
        `$start` function in our project template(s).

  * [ ] [Install the `console.error` panic hook inside the `main` function in
        our project
        template(s).](https://github.com/rustwasm/rust_wasm_template/issues/2)

* Improving stack overflow debugging ergonomics:

  * [ ] [Upgrade `rustc`'s LLVM and `lld` so we can get the `--stack-first`
        linker option.](https://github.com/rust-lang/rust/issues/50543)

  * [ ] Make `rustc` use `--stack-first` for wasm projects by default.

* [Issues labeled "debugging" in `rustwasm/*`
  repositories](https://github.com/issues?q=is%3Aissue+user%3Arustwasm+label%3Adebugging+is%3Aopen)

* Promising projects for the future:

  * https://github.com/sarahlim/wasm-trace

  * [ ] Hooking up `wasm-opt --instrument-memory` into `wasm-pack` and creating
        Valgrind clone for Rust and wasm.

[hook]: https://github.com/rustwasm/console_error_panic_hook
