# add defaults to some rpc server cli args

[https://github.com/paradigmxyz/reth/pull/3969](https://github.com/paradigmxyz/reth/pull/3969)

## Motivation

The following fields of `RpcServerArgs` do not have to be an `Option`.

- `auth_addr`
- `ws_addr`
- `ws_port`
- `http_addr`
- `http_port`

## Project description

Add a default value so it can be displayed in help and remove the `Option`.

## Specification

First I studied the `clap` crate in order to be able to understand the issue and solve it easily. You can find my documentation about it here: [Clap crate](https://alessandromazza.notion.site/Clap-crate-393be7f219514973a333f8608116dcbd?pvs=4).

Then I just added the `default_value_t` annotation in all of the above mentioned fields with its correspondent value:

- `IpAddr::V4(Ipv4Addr::LOCALHOST)` for ip addresses
- `constants::DEFAULT_HTTP_RPC_PORT`
- `constants::DEFAULT_WS_RPC_PORT`