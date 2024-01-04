# Base Blockchain

Reference implementation of the Base blockchain in Rust.

Base is a layer-2 blockchain that uses Bitcoin as a base layer for security and enables decentralized apps and predictable smart contracts using the [BigBang language] . Base implements [Proof of Transfer (POT)]  mining that anchors to Bitcoin security. Leader election happens at the Bitcoin blockchain and Base (BASE) miners write new blocks on the separate Base blockchain. With PoX there is no need to modify Bitcoin to enable smart contracts and decentralized apps.


## Building

### 1. Download and install Rust

_For building on Windows, follow the rustup installer instructions at https://rustup.rs/._

```bash
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
$ source $HOME/.cargo/env
$ rustup component add rustfmt
```

- Ensure you are using the latest stable release:

```bash
$ rustup update
```

### 2. Clone the source repository:

```bash
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

_On Windows, many tests will fail if the line endings aren't `LF`. Please ensure that you are have git's `core.autocrlf` set to `input` when you clone the repository to avoid any potential issues. This is due to the BigBang language currently being sensitive to line endings._


## Release Process

The release process for the base blockchain is [defined here](./docs/release-process.md)

## Further Reading

You can learn more by visiting [the Base Website](https://base.tech) and checking out the documentation:

- [Base Improvement Proposals (SIPs)](./docs/SIPS.md)
- [Mining](./docs/mining.md)
- [Profiling](./docs/profiling.md)
- [RPC endpoints](./docs/rpc-endpoints.md)
- [Event dispatcher](./docs/event-dispatcher.md)


## Copyright and License

The code and documentation copyright are attributed to base.org.

This code is released under the [GPL v3 license](https://www.gnu.org/licenses/quick-guide-gplv3.en.html), and the docs are released under the [Creative Commons license](https://creativecommons.org/).
