# Base Blockchain

Reference implementation of the [Base blockchain](https://github.com/base-network/base) in Rust.

Base is a layer-2 blockchain that uses Bitcoin as a base layer for security and enables decentralized apps and predictable smart contracts using the [Clarity language](https://clarity-lang.org/). Base implements [Proof of Transfer (PoX)](https://community.base.org/pox) mining that anchors to Bitcoin security. Leader election happens at the Bitcoin blockchain and Base (STX) miners write new blocks on the separate Base blockchain. With PoX there is no need to modify Bitcoin to enable smart contracts and decentralized apps.

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg?style=flat)](https://www.gnu.org/licenses/gpl-3.0)
[![Release](https://img.shields.io/github/v/release/base-network/base-blockchain?style=flat)](https://github.com/base-network/base-blockchain/releases/latest)
[![Build Status](https://github.com/base-network/base-blockchain/actions/workflows/ci.yml/badge.svg?branch=master&event=workflow_dispatch&style=flat)](https://github.com/base-network/base-blockchain/actions/workflows/ci.yml?query=event%3Aworkflow_dispatch+branch%3Amaster)
[![Discord Chat](https://img.shields.io/discord/621759717756370964.svg)](https://base.chat)

## Building

### 1. Download and install Rust

_For building on Windows, follow the rustup installer instructions at https://rustup.rs/._

```bash
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
$ source $HOME/.cargo/env
$ rustup component add rustfmt
```

- When building the [`master`](https://github.com/base-network/base-blockchain/tree/master) branch, ensure you are using the latest stable release:

```bash
$ rustup update
```

### 2. Clone the source repository:

```bash
$ git clone --depth=1 https://github.com/base-network/base-blockchain.git
$ cd base-blockchain
```

### 3. Build the project

```bash
$ cargo build
```

## Testing

**Run the tests:**

```bash
$ cargo test testnet  -- --test-threads=1
```

**Run all unit tests in parallel using [nextest](https://nexte.st/):**

_Warning, this typically takes a few minutes_
```bash
$ cargo nextest run
```

## Run the testnet

You can observe the state machine in action locally by running:

```bash
$ cd testnet/base-node
$ cargo run --bin base-node -- start --config=./conf/testnet-follower-conf.toml
```

_On Windows, many tests will fail if the line endings aren't `LF`. Please ensure that you are have git's `core.autocrlf` set to `input` when you clone the repository to avoid any potential issues. This is due to the Clarity language currently being sensitive to line endings._

Additional testnet documentation is available [here](./docs/testnet.md) and [here](https://docs.base.co/docs/nodes-and-miners/miner-testnet)

## Release Process

The release process for the base blockchain is [defined here](./docs/release-process.md)

## Further Reading

You can learn more by visiting [the Base Website](https://base.co) and checking out the documentation:

- [Base docs](https://docs.base.co/)
- [Base Improvement Proposals (SIPs)](./docs/SIPS.md)
- [Mining](./docs/mining.md)
- [Profiling](./docs/profiling.md)
- [RPC endpoints](./docs/rpc-endpoints.md)
- [Event dispatcher](./docs/event-dispatcher.md)

You can also read the technical papers:

- ["PoX: Proof of Transfer Mining with Bitcoin"](https://community.base.org/pox), May 2020
- ["Base 2.0: Apps and Smart Contracts for Bitcoin"](https://base.org/base), Dec 2020

## Copyright and License

The code and documentation copyright are attributed to base.org.

This code is released under the [GPL v3 license](https://www.gnu.org/licenses/quick-guide-gplv3.en.html), and the docs are released under the [Creative Commons license](https://creativecommons.org/).
