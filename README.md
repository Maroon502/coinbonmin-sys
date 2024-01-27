# Coinpopt-sys

[![Package][package-img]][package-url] [![Documentation][documentation-img]][documentation-url] [![License][license-img]][license-url]

coinbonmin-sys crate is a *-sys crate. The package provides Low-level bindings to the [Bonmin] library.

By this package, you don't need to worry about installing Bonmin in the system, and it's a package for **all platforms**.

Bonmin  (Basic Open-source Nonlinear Mixed INteger programming) is an open-source code for solving general MINLP (Mixed Integer NonLinear Programming) problems.

## Usage

Just add the following to your `Cargo.toml`:

```toml
[dependencies]
coinbonmin-sys = "0.1"
```

## Configuration

The following Cargo features are supported:

* `default`

The package build from the source and link statically by default. It also provide the following environment variables to allow users to link to system library customly:

* `CARGO_BOMIN_STATIC` to link to Bonmin statically;
* `CARGO_BOMIN_SYSTEM` to link to Bonmin system library;

Set the environment variable to `1` to enable the feature. For example, to link to system library dynamically, set `CARGO_${LIB_NAME}_SYSTEM` to `1`; to link to system library statically, set both `CARGO_${LIB_NAME}_SYSTEM` and `CARGO_${LIB_NAME}_STATIC` to `1`.

You can also use `bonmin-sys` with `no-default-features`, and add `bonmin-src` to the `Cargo.toml` and enable the related feature defined by `bonmin-src`. Please see [Bonmin-src].

## Windows and vcpkg

On Windows, if `${LIB_NAME}_SYSTEM` is set to `1`, `bonmin-src` will use [vcpkg] to find Bonmin. Before building, you must have the correct Bonmin installed for your target triplet and kind of linking. For instance, to link dynamically for the `x86_64-pc-windows-msvc` toolchain, install  `bonmin` for the `x64-windows` triplet:

```sh
vcpkg install bonmin --triplet x64-windows
```

To link Bonmin statically, install `bonmin` for the `x64-windows-static-md` triplet:

```sh
vcpkg install bonmin --triplet x64-windows-static-md
```

To link Bonmin and C Runtime (CRT) statically, install `bonmin` for the `x64-windows-static` triplet:

```sh
vcpkg install bonmin --triplet x64-windows-static
```

and build with `+crt-static` option

```sh
RUSTFLAGS='-C target-feature=+crt-static' cargo build --target x86_64-pc-windows-msvc
```

Please see the ["Static and dynamic C runtimes" in The Rust reference](https://doc.rust-lang.org/reference/linkage.html#static-and-dynamic-c-runtimes) for detail.

## Cross Compilation

Because [openblas-src]'s Issue [#101](https://github.com/blas-lapack-rs/openblas-src/issues/101), we can't cross compile the package with `openblas-static` feature. So, if you want to cross compile the package, you could use [mike-kfed](https://github.com/mike-kfed/openblas-src/tree/arm-cross-compile) instead.

Add this to your `project/.cargo/config.toml`.

```toml
[patch.crates-io]
openblas-src = { git = "https://github.com/mike-kfed/openblas-src.git", branch = "arm-cross-compile" }
```

you can compile it for the other target by providing the `--target` option to `cargo build`.

| Target                               |  supported  |
|--------------------------------------|:-----------:|
| `arm-unknown-linux-gnueabi`          | ✓   |
| `arm-unknown-linux-gnueabihf`        | ✓   |
| `armv7-linux-androideabi`            | ✓   |
| `armv7-unknown-linux-gnueabi`        | ✓   |
| `armv7-unknown-linux-gnueabihf`      | ✓   |
| `armv7-unknown-linux-musleabi`       | ✓   |
| `armv7-unknown-linux-musleabihf`     | ✓   |
| `riscv64gc-unknown-linux-gnu`        | ✓   |
| `x86_64-pc-windows-msvc`              | ✓   |
| `x86_64-unknown-linux-gnu`           | ✓   |

## Contribution

Your contribution is highly appreciated. Do not hesitate to open an issue or a
pull request. Note that any contribution submitted for inclusion in the project
will be licensed according to the terms given in [LICENSE](license-url).

[Bonmin]: https://github.com/coin-or/Bonmin
[Bonmin-src]: https://github.com/Maroon502/bonmin-src

[documentation-img]: https://docs.rs/coinbonmin-sys/badge.svg
[documentation-url]: https://docs.rs/coinbonmin-sys
[package-img]: https://img.shields.io/crates/v/coinbonmin-sys.svg
[package-url]: https://crates.io/crates/coinbonmin-sys
[license-img]: https://img.shields.io/crates/l/coinbonmin-sys.svg
[license-url]: https://github.com/Maroon502/coinbonmin-sys/blob/master/LICENSE.md