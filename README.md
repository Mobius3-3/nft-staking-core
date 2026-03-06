# NFT Staking Core (Anchor + Metaplex Core)

Reference Solana program for non-custodial NFT staking using Metaplex Core plugins. The staking state is written directly to NFT attributes and staking lock behavior is enforced via freeze controls.

## What this repository contains

- Anchor program in `programs/nft-staking-core`
- TypeScript integration tests in `tests/nft-staking-core.ts`
- Migration script in `migrations/deploy.ts`
- Optional Surfpool runbooks in `runbooks/`

## Core behavior

- Users stake NFTs from a managed collection
- Staked NFTs are marked via attributes (`staked`, `staked_at`)
- NFT transferability is controlled through plugin-based freeze/delegate flow
- Rewards are minted based on staking duration and collection config
- Oracle-based transfer validation and update flow is included

## Program instructions

- `create_collection`
- `mint_nft`
- `initialize_config`
- `stake`
- `unstake`
- `claim_rewards`
- `burn`
- `initialize_oracle`
- `update_oracle`
- `transfer_nft`

## Prerequisites

- Rust + Cargo (matching `rust-toolchain.toml`)
- Solana CLI
- Anchor CLI
- Node.js + Yarn

## Quickstart

1. Install dependencies

```bash
yarn install
```

2. Build the program

```bash
anchor build
```

3. Run tests (localnet)

```bash
anchor test
```

## Useful commands

```bash
# format/lint TypeScript files
yarn lint
yarn lint:fix

# run only ts-mocha tests configured in Anchor.toml script
yarn run ts-mocha -p ./tsconfig.json -t 1000000 "tests/**/*.ts"
```

## Program ID

Current localnet program ID is configured in:

- `Anchor.toml` under `[programs.localnet].nft_staking_core`
- `programs/nft-staking-core/src/lib.rs` via `declare_id!`

Keep these two values synchronized whenever rotating program keys.

## Project layout

```text
programs/nft-staking-core/src/
    constants.rs
    errors.rs
    helper.rs
    lib.rs
    instructions/
    state/

tests/
    nft-staking-core.ts

migrations/
    deploy.ts
```

## Runbooks (optional)

If using Surfpool for local workflows and scripted deployments, see `runbooks/README.md`.

## Challenge notes

Additional extension tasks are documented in `challenge.md`.
