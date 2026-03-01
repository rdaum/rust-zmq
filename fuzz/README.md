# Fuzzing

This directory contains `cargo-fuzz` targets for safety and correctness-sensitive APIs.

## Targets

- `fuzz_has`: fuzzes `zmq::has` with arbitrary UTF-8 capability names.
- `fuzz_message_gets`: fuzzes `Message::gets` with arbitrary UTF-8 property names.
- `fuzz_message_alloc`: fuzzes `Message` allocation constructors with varied lengths.

## Running locally

Install cargo-fuzz:

```bash
cargo +nightly install cargo-fuzz
```

Run a target with ASAN:

```bash
cd fuzz
cargo +nightly fuzz run fuzz_has --sanitizer address -- -max_total_time=60
```

Other targets:

```bash
cargo +nightly fuzz run fuzz_message_gets --sanitizer address -- -max_total_time=60
cargo +nightly fuzz run fuzz_message_alloc --sanitizer address -- -max_total_time=60
```
