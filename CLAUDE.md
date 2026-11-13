# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What

Web server (actix-web + sea-orm) and React/PatternFly UI for managing Peru SUNAT UBL documents.
Uses the `xhandler` crate from https://github.com/project-openubl/xhandler-rust (git dependency).

## Commands

```bash
# System deps (Ubuntu): sudo apt-get install pkg-config libssl-dev libxml2-dev libclang-dev
# Fedora: sudo dnf install pkg-config libxml2-devel xmlsec1-devel xmlsec1-openssl clang-devel
# Node.js + npm are required: ui/crate/build.rs runs the UI build during `cargo build`.
cargo build
cargo test
cargo fmt --check
cargo clippy --all-targets --all-features -- -D warnings
cargo run --bin server -- server --db-fs-path openubl.sqlite local --storage-local-dir .openubl
                                  # http://localhost:8080, Swagger at /swagger-ui
npm run dev --prefix ui           # UI dev server at http://localhost:3000
npm run check --prefix ui         # biome lint
```

Rust 1.100.0 pinned in `rust-toolchain.toml`. Clippy allows unwrap/expect in tests.

## Crates

- **server** (`openubl-server`) — actix-web HTTP API + embedded UI
- **cli** (`server` binary) — entrypoint
- **api** — business logic over the DB
- **entity** / **migration** — sea-orm entities and migrations
- **storage** — local / MinIO / S3 file storage
- **common**, **signature**, **xtask** (OpenAPI generation → `openapi.yaml`)
- **ui/crate** (`openubl-ui`) — embeds the built UI as static files
