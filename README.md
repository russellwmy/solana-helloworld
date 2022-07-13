# Hello world on Solana

This project demonstrates how to build programs on the Solana blockchain with cargo-make.

The project comprises of:

- An on-chain hello world program
- A client that can send a "hello" to an account and get back the number of
  times "hello" has been sent

## Table of Contents

- [Quick Start](#quick-start)
  - [Configure CLI](#configure-cli)
  - [Start local Solana cluster](#start-local-solana-cluster)
  - [Build the on-chain program](#build-the-on-chain-program)
  - [Deploy the on-chain program](#deploy-the-on-chain-program)
  - [Customizing the Program](#customizing-the-program)
- [Writing the client in Rust](#writing-the-client-in-rust)
- [Pointing to a public Solana cluster](#pointing-to-a-public-solana-cluster)
- [Learn about Solana](#learn-about-solana)
- [Learn about the on-chain program](#learn-about-the-on-chain-program)
  - [Programming on Solana](#programming-on-Solana)

## Quick Start

The following dependencies are required to build and run this example, depending
on your OS, they may already be installed:

- Install cargo-make 0.35.13 or later with `cargo install cargo-make`
- Install Rust v1.62.0 or later from https://rustup.rs/
- Install Solana v1.8.14 or later from
  https://docs.solana.com/cli/install-solana-cli-tools

If this is your first time using Rust, these [Installation
Notes](README-installation-notes.md) might be helpful.

### Configure CLI

> If you're on Windows, it is recommended to use [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10) to run these commands

1. Set CLI config url to localhost cluster

```bash
solana config set --url localhost
```

2. Create CLI Keypair

If this is your first time using the Solana CLI, you will need to generate a new keypair:

```bash
solana-keygen new
```

### Start local Solana cluster

This example connects to a local Solana cluster by default.

Start a local Solana cluster:

```bash
solana-test-validator
```

> **Note**: You may need to do some [system tuning](https://docs.solana.com/running-validator/validator-start#system-tuning) (and restart your computer) to get the validator to run

Listen to transaction logs:

```bash
solana logs
```

### Build the on-chain program

There is both a Rust version of the on-chain program, whichever is built
last will be the one used when running the example.

```bash
cargo make build
```

### Deploy the on-chain program

```bash
cargo make deploy
```

### Customizing the Program

To customize the example, make changes to the files under `/src`. If you change
any files you will need to
[rebuild the on-chain program](#build-the-on-chain-program) and [redeploy the program](#deploy-the-on-chain-program).

## Writing the client in Rust

Solana client program can be written in any language. For an
example client written in Rust and an accompanying write up see [this
repo](https://github.com/ezekiiel/simple-solana-program).

## Pointing to a public Solana cluster

Solana maintains three public clusters:

- `devnet` - Development cluster with airdrops enabled
- `testnet` - Tour De Sol test cluster without airdrops enabled
- `mainnet-beta` - Main cluster

Use the Solana CLI to configure which cluster to connect to.

To point to `devnet`:

```bash
solana config set --url devnet
```

To point back to the local cluster:

```bash
solana config set --url localhost
```

## Learn about Solana

More information about how Solana works is available in the [Solana
documentation](https://docs.solana.com/) and all the source code is available on
[github](https://github.com/solana-labs/solana)

## Learn about the on-chain program

The [on-chain helloworld program](/src/program-rust/Cargo.toml) is a Rust program
compiled to [Berkeley Packet Filter
(BPF)](https://en.wikipedia.org/wiki/Berkeley_Packet_Filter) bytecode and stored as an
[Executable and Linkable Format (ELF) shared
object](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format).

The program is written using:

- [Solana Rust SDK](https://github.com/solana-labs/solana/tree/master/sdk)

### Programming on Solana

To learn more about Solana programming model refer to the [Programming Model
Overview](https://docs.solana.com/developing/programming-model/overview).

To learn more about developing programs on Solana refer to the [On-Chain
Programs Overview](https://docs.solana.com/developing/on-chain-programs/overview)
