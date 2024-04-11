# Coinpopt-sys

[![Package][package-img]][package-url] [![Documentation][documentation-img]][documentation-url] [![License][license-img]][license-url]

`coinbonmin-sys` crate is a *-sys crate. The package provides Low-level bindings to the [Bonmin] library.

By this package, you don't need to worry about installing Bonmin in the system, and it's a package for **all platforms**.

Bonmin  (Basic Open-source Nonlinear Mixed INteger programming) is an open-source code for solving general MINLP (Mixed Integer NonLinear Programming) problems.

## Usage

Just add the following to your `Cargo.toml`:

```toml
[dependencies]
coinbonmin-sys = "\*"
```

## Configuration

You can use `coinbonmin-sys` with `no-default-features`, and add `bonmin-src` to the `Cargo.toml` and enable the related feature defined by `bonmin-src`. Please see [Bonmin-src].

## Library Linking and Cross Compile

if you want to know the detail about how it compile or link the Bonmin, please see [Bonmin-src].

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