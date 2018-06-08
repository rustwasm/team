# Goal: Book, Documentation, Tutorials

Providing high quality documentation so that users can effortlessly get spun up on Rust and wasm 
and start hacking without fear. We want to reduce the friction, bounce rate, and frustration from
trying something new and struggling to find good answers to common problems.

## Owner

**Michael Gattozzi**

- GitHub: [mgattozzi](https://github.com/mgattozzi)
- IRC nick: `mgattozzi`
- Email: mgattozzi@gmail.com

## Details

Documentation is an absolutely critical part of the developer experience. Especially when coming into contact
with a new concept or technology like WebAssembly. We want to make this experience something people feel happy,
excited, and willing to continue using Rust with WebAssembly as their go to toolchain. In conjunction with the
Working Group's Rust 2018 Goals this means we'll want to do the following:

1. Make the Game of Life tutorial the primary way to learn about Rust and Web Assembly
2. Make the tutorial a high quality piece of documentation that makes learning effortless rather than frustrated
3. Provide appendixes and tutorials for tools the team recommends to use such as, but not limited to, `wasm-bindgen`
   and `wasm-pack`
4. Provide troubleshooting instructions for common issues when using Rust with WebAssembly
5. Document current blockers and known issues that might hinder development (i.e. we once had a bug where debug
   builds would not work which was surprising)

By focusing on the end user experience we can create a multiplicative benefit when combined with tooling and other
features the team as a whole is currently working on. Beyond the 2018 edition more work can be done to focus on non
web areas such as wasm on the desktop, but for now the primary goals are the ones listed above and greatly overlap
with future plans.

## How to Help

- [rustwasm/book][book] is where the documentation lives
- [rustwasm/wasm_game_of_life][gol] is where the code for the Game of Life tutorial lives

Want to get started helping out? The [book has some good first issues][book issues] and the
[Game of Life tutorial][gol issues] also has some things that can be worked on. If you can't find
something you feel like you can work on or don't know where to begin, ping either me or someone
on the [@rustwasm/book team][team]!

[book]: https://github.com/rustwasm/book
[book issues]: https://github.com/rustwasm/book/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22
[gol]: https://github.com/rustwasm/wasm_game_of_life
[gol issues]: https://github.com/rustwasm/wasm_game_of_life/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22
[team]: https://github.com/orgs/rustwasm/teams/book
