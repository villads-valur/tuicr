# Contributing

## The workflow

1. Use Claude (or your favorite AI coding agent) to make changes
2. Run `cargo run` to review the diff with `tuicr` itself
3. Export your comments and feed them back to Claude
4. Repeat until you're happy
5. Open a PR

Dogfooding is mandatory. If `tuicr` is annoying to use for your own changes, fix that first.

## Building

```bash
cargo build
cargo test
cargo fmt
```

## Guidelines

- Keep it simple—this is a focused tool, not a platform
- If you add a feature, use it yourself first
- Bug reports and feature requests welcome via issues
