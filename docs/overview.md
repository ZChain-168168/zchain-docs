---
id: overview
title: Polygon Edge
sidebar_label: Overview
---

# Zchains

Zchains is a modular and extensible framework for building Ethereum-compatible blockchain networks, sidechains, and general scaling solutions.

Its primary use is to bootstrap a new blockchain network while providing full compatibility with Ethereum smart contracts and transactions. It uses IBFT (Istanbul Byzantine Fault Tolerant) consensus mechanism, supported in  [PoS (proof of stake)](consensus/pos-stake-unstake.md).

Zchains also supports communication with multiple blockchain networks, enabling transfers of both [ERC-20](https://ethereum.org/en/developers/docs/standards/tokens/erc-20) and [ERC-721](https://ethereum.org/en/developers/docs/standards/tokens/erc-721) tokens, by utilising the [centralised bridge solution](https://github.com/ZChain-168168/ZChain-Bridge-Smart-Contract/blob/main/README.md).

Industry standard wallets can be used to interact with Zchains through the [JSON-RPC](working-with-node/) endpoints and node operators can perform various actions on the nodes through the [gRPC](working-with-node/query-operator-info/) protocol.

To find out more about Zchains, visit the [official website](https://zchains.com/).

[**GitHub repository**](https://github.com/0xPolygon/polygon-edge)

:::caution

This is a work in progress so architectural changes may happen in the future. The code has not been audited yet, so please contact the Zchains team if you would like to use it in production.

:::

To get started by running a Zchains network locally, please read: [Installation](get-started/installation/) and [Local Setup](get-started/set-up-ibft-locally/).
