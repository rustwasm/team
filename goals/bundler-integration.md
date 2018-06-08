# Goal: Bundler Integration

It should be very easy to take Rust code and integrate it into your JavaScript project (using the same build pipeline).

## Owner

**Sven Sauleau**

- GitHub: [xtuc](https://github.com/xtuc)
- IRC nick: `username`
- Email: sven@sauleau.com

## Details

Currently the focus is on the Webpack integration, we should be able to use it with Rust tooling (wasm-bindgen, wasmsnip, wasmopt, etc) for the 2018 edition. 

### Webpack

The integration is usable, a couple of fixes and improvements are in progress.

The next goals are finishing the [rust-plugin](https://github.com/xtuc/rust-plugin) (for optimizations) and creating a loader (for compilation).

### Rollup

PR is progress: https://github.com/rollup/rollup/pull/2113

### Parcel

The current WebAssembly integration is not usable and we raised an issue: https://github.com/parcel-bundler/parcel/issues/1325. 

## How to Help

The project https://github.com/xtuc/webassemblyjs/ provides the tooling needed for the bundler integrations, it would be great if you can help there: [webassemblyjs](https://github.com/xtuc/webassemblyjs).

We also provide a Plugin for Webpack: [rust-plugin](https://github.com/xtuc/rust-plugin).
