# mrtd

A Rust parser for the machine-readable zone (MRZ) of machine-readable travel documents (MRTD) as defined by ICAO Document 9303.

Supported travel documents:

- Passport

## Example

```rust
use mrtd::{parse, Document};

fn main() {
    let mrz = "P<UTOERIKSSON<<ANNA<MARIA<<<<<<<<<<<<<<<<<<<\
            L898902C36UTO7408122X1204159ZE184226B<<<<<10";
    let Document::Passport(passport) = parse(mrz).unwrap();
    assert_eq!(passport.passport_number, "L898902C3");
    println!("{:?}", passport);
}
```
