# strena, the string arena

An [arena]-inspired [interner][interning] for strings.
 
The interner allows you to cache strings and instead deal in a simple
symbol, which is trivial to copy around and compare for equality.

As opposed to most other interners, this interner stores all of the
interned strings in a single concatenated string. This reduces allocation
space required for the interned strings, as well as fragmentation of the
memory held by the interner.

## Cargo Features

- `inline-more`: Aggressively inline functions defined in this crate.
  Note that 99% of this crate is already monomorphized into consumers,
  and thus this just further inlines the functionality into every CGU
  of dependent crates, moving work from thin-crate LTO to codegen.
  This can cause a significant increase in compile time for some slight
  (unmeasured) performance benefits.

- `inline-even-more`: Do aggressive inlining, and aggressively inline
  hashbrown's hashtable implementation as well. Further compile-time
  impact for further slight (unmeasured) performance benefits.

- `rayon`: Support parallel iteration of symbols via [rayon].

  [rayon]: <https://docs.rs/rayon/>
  [arena]: <https://stackoverflow.com/q/12825148/3019990>
  [interning]: <https://en.wikipedia.org/wiki/String_interning>

## Minimum Supported Rust Version

1.36, the first version with stable access to the `alloc` crate.

This minimum version support is informal, and may change with any version.
It will, however, not be regressed without specific reasoning for upgrading.

## License

Licensed under either of

 * Apache License, Version 2.0
   ([LICENSE/APACHE](LICENSE/APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license
   ([LICENSE/MIT](LICENSE/MIT) or http://opensource.org/licenses/MIT)

at your option.

If you are a highly paid worker at any company that prioritises profit over
people, you can still use this crate. I simply wish you will unionise and push
back against the obsession for growth, control, and power that is rampant in
your workplace. Please take a stand against the horrible working conditions
they inflict on your lesser paid colleagues, and more generally their
disrespect for the very human rights they claim to fight for.

## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.

