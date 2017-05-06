# Legacy Serde shims

These shim crates allow a single crate to support impls for multiple versions of
Serde at the same time.

- [`serde06`](https://crates.io/crates/serde06)
- [`serde07`](https://crates.io/crates/serde07)
- [`serde08`](https://crates.io/crates/serde08)
- [`serde09`](https://crates.io/crates/serde09)
- [`serde1`](https://crates.io/crates/serde1)

```rust
extern crate serde08;
extern crate serde09;
extern crate serde1;

struct S;

impl serde08::Deserialize for S {
    fn deserialize<D>(deserializer: &mut D) -> Result<Self, D::Error>
        where D: serde08::Deserializer
    {
        unimplemented!()
    }
}

impl serde09::Deserialize for S {
    fn deserialize<D>(deserializer: D) -> Result<Self, D::Error>
        where D: serde09::Deserializer
    {
        unimplemented!()
    }
}

impl<'de> serde1::Deserialize<'de> for S {
    fn deserialize<D>(deserializer: D) -> Result<Self, D::Error>
        where D: serde1::Deserializer<'de>
    {
        unimplemented!()
    }
}
```

## License

Serde is licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or
   http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or
   http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in Serde by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
