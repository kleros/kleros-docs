---
description: >-
  When you want to interact with an Arbitrable app that is using Kleros Court as
  an Arbitrator
---

# Interacting with Arbitrable app

There are as many ways to interact with an `Arbitrable` app as there are Arbitrable apps. We will not be able to list them all exhaustively here but we will try to give you some pointers.

## Query the app subgraph API

If a [Graph Protocol](https://thegraph.com/) subgraph already exists for the application you want to read from, you can directly [query its subgraph](https://thegraph.com/docs/query-the-graph).

* [Kleros Tokens \(Mainnet\) subgraph](https://thegraph.com/explorer/subgraph/kleros/t2cr)
* [Kleros Curate \(Mainnet\) subgraph](https://thegraph.com/explorer/subgraph/kleros/curate)
* [Kleros Curate \(Rinkeby\) subgraph](https://thegraph.com/explorer/subgraph/kleros/curate-rinkeby)
* [Proof of Humanity \(Mainnet\) subgraph](https://thegraph.com/explorer/subgraph/kleros/proof-of-humanity-mainnet)
* [Proof of Humanity \(Kovan\) subgraph](https://thegraph.com/explorer/subgraph/epiqueras/proof-of-humanity-kovan)

If no subgraph exists for the application you want to read from, you can request one to the Kleros team, or [define ](https://thegraph.com/docs/define-a-subgraph)and [deploy](https://thegraph.com/docs/deploy-a-subgraph) one.

## Interact directly with the app smart contracts

Check out Kleros repository, Proof of Humanity repository, or Kleros-Integrated products repositories to consult the arbitrable apps smart contracts and understand how to interact directly with their setter and getter functions.

## Use the Archon library

Use the [Archon Library Arbitrable package](https://archon.readthedocs.io/en/latest/archon-arbitrable.html) to read disputes, evidence, metaevidence, and ruling from arbitrable smart contracts.

