# ask for confirmation during reth db drop

[https://github.com/paradigmxyz/reth/pull/4118](https://github.com/paradigmxyz/reth/pull/4118)

## Motivation

It's a shame when a fully synced mainnet database is accidentally deleted.

## Project description

Let's ask for the interactive confirmation by default and add a `-f` / `--force` flag to explicitly bypass this confirmation.

## Specification

Add a `-f`/ `--force` flag to the `reth db drop` command. If not passed by the user, it always asks for confirmation before dropping the db. If the user passes the `-f`/`--force` flag it bypasses the confirmation and immediately drops the db.

I added a bool argument `force` to the `Drop` subcommand and made the logic be dependent on that value: if it is set (to true), then when you call the drop subcommand it immediately drops the database. Otherwise it asks for confirmation before dropping it.