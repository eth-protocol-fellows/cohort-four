# feat: add rpc server metrics into dashboard

[https://github.com/paradigmxyz/reth/pull/4078](https://github.com/paradigmxyz/reth/pull/4078)

## Motivation

New set of metrics for rpc server added in [#3913](https://github.com/paradigmxyz/reth/pull/3913) but are currently not tracked in the grafana dashboard.

## Project description

Integrate in dashboard:

- active requests
- histogram
- active websocket connections

## Specification

I added all those metrics in three different charts using standard Grafana JSON format. Actually I had never worked on grafana metrics so it was very interesting to understand how that works in details and be able to create dashbaords based on metrics exposed by Reth.