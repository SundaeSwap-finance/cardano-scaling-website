---
title: February 2024
slug: 2024-02
authors: [ch1bo]
tags: [monthly]
---

This is the first joint report of the Hydra and Mithril projects and summarizes on the work done since January 2024.

In the past, each team had published updates as part of their repositories in varying form and cadence:

  - Hydra [monthly reports](https://hydra.family/head-protocol/monthly)
  - Mithril [dev blog](https://mithril.network/doc/dev-blog/)

Keeping such "procedural" documents as part of the code base is not ideal, as it often requires special handling when building versioned, published documentation. For example, [this workflow](https://github.com/input-output-hk/hydra/blob/fad12fd7d967e5e8af4d8b832396e68bd8510e9a/.github/workflows/publish-docs.yaml#L87-L92) in the Hydra project which publishes to https://hydra.family required several attempts to work around how docusaurus websites are built. Consequently, we introduced a [dedicated repository](https://github.com/cardano-scaling/website) that builds into a [website](https://cardano-scaling.github.io/website). This not only helps in keeping the original product repositories clean of inherently dated information, but also serves as a new home for joint reports, announcements or occasional articles.

Finally, this monthly report here serves us as preparation for the monthly review meeting (see [slides][slides] and [recording][recording]), where the team updates project stakeholders on recent developments to gather their feedback on proposed plans.

## Mithril Roadmap & Status

TODO

## Mithril Development Highlights

[Issues and pull requests closed in February](https://github.com/input-output-hk/mithril/issues?q=is%3Aclosed+sort%3Aupdated-desc+closed%3A2024-01-31..2024-02-29).

### Release and publication

- Released the distribution [`2408.0`](https://github.com/input-output-hk/mithril/releases/tag/2408.0).
- Published a development blog post [Mithril SanchoNet network released](https://mithril.network/doc/dev-blog/2024/02/08/testing-sanchonet-network-available).
- Published a development blog post [Mithril client CLI output breaking change](https://mithril.network/doc/dev-blog/).

### Signing Cardano transactions proof-of-concept

The team has kept working on the implementation of a proof-of-concept of a data type for certifying Cardano transactions within Mithril networks. Last month, we have extended the [Mithril client library](https://crates.io/crates/mithril-client) to support the certification of Cardano transactions. This month, we have ugraded the [client CLI](https://mithril.network/doc/manual/developer-docs/nodes/mithril-client/) and implemented a new `cardano-transaction` command that can list snapshots and certify a list of Cardano transactions. Addtionally, we have implemented the same API surface on the [WASM client](https://www.npmjs.com/package/@mithril-dev/mithril-client-wasm) that now supports transaction certification in the browser.

![](img/2024-02-mithril-cardano-tx.png)

### Enhanced support for Conway and Sanchonet

We have extensively tested the upcoming `Conway` era and we are now confident that Mithril networks will smoothly transition to this new era. Moreover, we have released a new [`testing-sanchonet`](https://mithril.network/explorer/?aggregator=https%3A%2F%2Faggregator.testing-sanchonet.api.mithril.network%2Faggregator) network that has been opened to SPOs so that we can jointly test upcoming and experimental features (e.g. the aforementioned signature of the Cardano transactions).

### Community update

The TxPipe team has kept working on the implementation of the `Pallas Chain Observer` for Mithril nodes and has contributed to retrieving the stake distribution and Mithril era markers (stored in the UTxOs of the chain) directly from the Cardano node with mini-protocols.

## Hydra Roadmap

The Hydra project [roadmap](https://github.com/orgs/input-output-hk/projects/21/views/7) only saw few changes this month:

![The roadmap with features and ideas](./img/2024-02-hydra-roadmap.jpg) <small><center>The latest roadmap with features and ideas</center></small>

#### Notable updates

* New: [Drop support for JSON encoded transactions #1213](https://github.com/input-output-hk/hydra/issues/1213) to cover breaking changes we experienced when switching `cardano-node` and `cardano-ledger` versions
* [Smoke tests on Sanchonet #1257](https://github.com/input-output-hk/hydra/issues/1257) took longer than anticipated as it uncovered some issues, but seeing smoke tests run on Sanchonet now makes us confident the `hydra-node` is ready for the Conway hard-fork
* [Build and deploy a Hydra heads explorer #696](https://github.com/input-output-hk/hydra/issues/696) is about half-way done as the data is available for `sanchonet` under http://explorer.hydra.family/heads and we're only missing a user interface
* Also started work on [Incremental commit #199](https://github.com/input-output-hk/hydra/issues/199) as the UX will be very similar to [Incremental decommit #1057](https://github.com/input-output-hk/hydra/issues/1057)
  - Having both features implemented off-chain, would allow early adopters to try this out while we work on the on-chain security.
* Added [Streaming Plugins #1325](https://github.com/input-output-hk/hydra/issues/1325) feature to cover SundaeLab's work on their Catalyst proposal

## Hydra Development Highlights

[Issues and pull requests closed since the last report](https://github.com/input-output-hk/hydra/issues?q=is%3Aclosed+sort%3Aupdated-desc+closed%3A2024-01-31..2024-02-29).

This month, the team worked on the following:

### Contest after fanout bug hunt

TODO

### Hydra explorer supporting multiple versions

The hydra explorer currently supports only one version on one network. This is
because the Hydra scripts are compiled into `hydra-node` and
`hydra-chain-observer` binaries and the observer talks is connected to a single
`cardano-node` running as a client on one network. To support multiple versions,
we need to compile the scripts of each version into individual chain observer
binaries and communicate with them through an API. While Plutus validators
change on any modification (their hashes and addresses), this API between the
`hydra-chain-observer` and `hydra-explorer` components can serve as an
integration point which we can support through multiple versions of the
protocol.

## Community update

TODO: Ikigai on hydra auctions?

TODO: on-going mithril contributions by TxPipe?

## Conclusion

We held the monthly review meeting for February 2024 on 2024-02-26 via Google Meet, presenting these [slides][slides] and this [recording][recording].

TODO

[slides]: https://docs.google.com/presentation/d/18buDs_TcMHgFAYjJt9GftQiEnVB3ubcoD3Djh3ovxSc/edit#slide=id.g1f87a7454a5_0_1392
[recording]: 