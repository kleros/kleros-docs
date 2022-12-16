---
description: >-
  When you want to interact with an Arbitrable app that is using Kleros Court as
  an Arbitrator
---

# Interact with Arbitrable apps built on top of Kleros Court

There are as many ways to interact with an `Arbitrable` app as there are Arbitrable apps. We will not be able to list them all exhaustively here but we will try to give you some pointers.

## Query the app subgraph API

If a [Graph Protocol](https://thegraph.com/) subgraph already exists for the application you want to read from, you can directly [query its subgraph](https://thegraph.com/docs/query-the-graph).

{% hint style="info" %}
**Kleros Arbitrable apps subgraphs**

* [Kleros Tokens (Mainnet) subgraph](https://thegraph.com/explorer/subgraph/kleros/t2cr)
* [Kleros Curate (Mainnet) subgraph](https://thegraph.com/explorer/subgraph/kleros/curate)
* [Kleros Curate (Goerli) subgraph](https://thegraph.com/hosted-service/subgraph/greenlucid/curate-goerli)
* [Proof of Humanity (Mainnet) subgraph](https://thegraph.com/explorer/subgraph/kleros/proof-of-humanity-mainnet)
* [Proof of Humanity (Kovan) subgraph](https://thegraph.com/explorer/subgraph/epiqueras/proof-of-humanity-kovan)
{% endhint %}

If no subgraph exists for the application you want to read from, you can request one to the Kleros team, or [define ](https://thegraph.com/docs/define-a-subgraph)and [deploy](https://thegraph.com/docs/deploy-a-subgraph) one.

## Interact directly with the app smart contracts

Check out the Kleros repository, Proof of Humanity repository, or Kleros-Integrated products repositories to consult the arbitrable apps smart contracts and understand how to interact directly with their setter and getter functions.

{% hint style="info" %}
**How to integrate with Kleros Arbitrable apps**

* Kleros Tokens [Technical Documentation](https://t2cr-docs.readthedocs.io/en/latest/deep-dive/#introduction) or list in [Token Lists](https://tokenlists.org/token-list?url=t2crtokens.eth)
{% endhint %}

## Use the Archon library

Use the [Archon Library Arbitrable package](https://archon.readthedocs.io/en/latest/archon-arbitrable.html) to read disputes, evidence, metaevidence, and ruling from arbitrable smart contracts.
