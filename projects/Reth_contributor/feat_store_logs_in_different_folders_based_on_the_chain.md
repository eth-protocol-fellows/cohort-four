# feat: store logs in different folders based on the chain

[https://github.com/paradigmxyz/reth/pull/3948](https://github.com/paradigmxyz/reth/pull/3948)

## Motivation

Currently logs are output to `~/.cache/reth/logs/reth.log`, even if there are multiple nodes running on different chains.

## Project description

Instead, logs should be output to `~/.cache/reth/logs/<chain>/reth.log`, or moved to the already-chain-specific `--datadir`. For example:

`~/.cache/reth/logs/mainnet/reth.log`

`~/.cache/reth/logs/sepolia/reth.log`

## Specification

When `--log.persistent` flag is enabled, logs are now stored in different folders based on the chain or in the already-chain-specific `--datadir`.

Examples (no `--datadir` flag):

`~/.cache/reth/logs/mainnet/reth.log`

`~/.cache/reth/logs/sepolia/reth.log`

Examples (with `--datadir` flag):

`~/custom-data-dir/reth.log`

In order to do that, I added a `chain` field in the `Cli` struct with the `global = true` annotation and made the logs folder be based on that specific flag.

```rust
// add network name to logs dir
self.logs.log_directory = self.logs.log_directory.join(self.chain.chain.to_string());
```