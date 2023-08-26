# feat: add flag to CLI to disable colour coding of console output

[https://github.com/paradigmxyz/reth/pull/4033](https://github.com/paradigmxyz/reth/pull/4033)

## Motivation

Add cli flag that is going to disable the colour coding of console output, it is particularly annoying with docker logs that would contain ansci encoding.

## Project description

Add cli flag `--log.color` that is going to disable the colour coding of console output

## Specification

I added a `color` flag to the `Cli` struct that accepts three different `ColorMode`:

- `always`: colors on.
- `auto`: usually does some environment detection, but for now it's ok if it just behaves as `always`.
- `never`: colors off.

Then I changed the signature of the logs tracing function to also accept a `ColorMode` and set colors accordingly.