---
description: How to integrate with Kleros?
---

# Overview

## Why do you want to integrate with Kleros services?

* If you are looking for pure **Arbitration-as-a-Service**, we can help you integrate with our core service [Kleros Court](https://kleros.gitbook.io/docs/products/court).
* If you want an oracle that can provide rulings about events, connect to [Kleros Oracle](https://kleros.gitbook.io/docs/products/oracle) and get **Truth-as-a-Service** capabilities.
* If you are searching for **Data-Curation-as-a-Service**, use our [Kleros Curate](https://kleros.gitbook.io/docs/products/curate) generalized TCR product to build open community-curated lists and read from them.
* If you want to manage crypto-vs-crypto transactions or service-vs-crypto transactions in your app, have a look at [Kleros Escrow](https://kleros.gitbook.io/docs/products/escrow) contract \(+ Widget & SDK\) for **Escrow-as-a-Service** features.
* If you are a DAO looking to fully decentralize your governance \(even the enforcement of proposal votes\), check out [Kleros Governor](https://kleros.gitbook.io/docs/products/governor) and use it as **Supreme-Court-as-a-Service**.

### What about Kleros products built on top of those services?

* Your DeFi application can source its token data directly from[ Kleros Tokens](https://kleros.gitbook.io/docs/products/tokens) registry and even curate the tokens using badges \(e.g. filtering them using preset criteria\) or indirectly through [TokenLists.org](https://tokenlists.org/token-list?url=t2crtokens.eth)
* Your product can use Sybil-resistance properties of [Proof of Humanity](https://kleros.gitbook.io/docs/products/proof-of-humanity) to protect against Sybil attacks or identify your users.
* You can apply to or benefit from decentralized translation jobs in [Linguo](https://kleros.gitbook.io/docs/products/linguo) to handle the internationalization of your products.

Have a look at the ❓ [Integrations FAQ](https://kleros.gitbook.io/docs/integrations/integrations-faq) ❓ for more answers to common questions.

## Type of Integrations

Kleros Court is the implementation of an arbitrator as per the [arbitration standard we developed](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard). Most integrations consist in buiding or customizing an arbitrable app so it can request arbitration to Kleros Court. Once you integrate with the arbitration standard, you \(or your users\) will be able to choose any arbitrator that follows the standard to solve disputes, including Kleros.  
  
The integration can be done today by:

* **Building an Arbitrable contract**: At [smart-contract-level](https://kleros.gitbook.io/docs/integrations/overview#smart-contract-integration), you will need to create an arbitrable smart contract or ensure your existing smart contracts are compliant to the Arbitrable Interface:

  * From scratch by applying the [arbitration standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) \(and/or using the [Archon library](https://kleros.gitbook.io/docs/developer/archon-ethereum-arbitration-standard-api)\),
  * By customizing one of our [examples](https://github.com/kleros/kleros-interaction) or looking at[ live integrations](https://kleros.gitbook.io/docs/integrations/current-integrations),
  * By working with [Cooperative Kleros](mailto:contact@kleros.io) to adapt yours to the standard or creating a connector,

* **Interacting with an existing Arbitrable contract**: It can be an Kleros arbitrable product \(Escrow, Curate, Tokens, Linguo, PoH, Governor, Dispute Resolver\) or an external one \(Reality.eth\).

Or in the future by:

* **Interacting with a 3rd party intermediary entity:** that will format and forward the dispute to Kleros for you.



