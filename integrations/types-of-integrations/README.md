---
description: Have a look at the paths to integration
---

# Types of Integrations

Kleros Court is the implementation of an arbitrator as per the [Arbitration standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) we developed. Most integrations consist in building or customizing an Arbitrable app so it can request arbitration to Kleros Court. Once you integrate with the Arbitration standard, you \(or your users\) will be able to choose any arbitrator that follows the standard to solve disputes, including Kleros.

![](../../.gitbook/assets/image%20%2848%29.png)

Integrating with Kleros Court can be done today by:

1. \*\*\*\*[**Building an Arbitrable smart contract**](https://kleros.gitbook.io/docs/integrations/types-of-integrations/smart-contract-integration) ****_\(and plugging it to Kleros Court as Arbitrator\)_

   * You will need to create an arbitrable smart contract or ensure your existing smart contracts are compliant with the Arbitrable interface:
     * From scratch by applying the [Arbitration standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) \(and/or using the [Archon library](https://kleros.gitbook.io/docs/developer/archon-ethereum-arbitration-standard-api)\),
     * By customizing one of our [examples](https://github.com/kleros/kleros-interaction) or looking at[ live integrations](https://kleros.gitbook.io/docs/integrations/current-integrations),
     * By working with [Cooperative Kleros](mailto:contact@kleros.io) to adapt yours to the standard or creating a connector,

2. \*\*\*\*[**Interacting with an existing Arbitrable application**](https://kleros.gitbook.io/docs/integrations/types-of-integrations/interacting-with-arbitrable-app)\*\*\*\*
   * It can be a Kleros Arbitrable product \(Escrow, Curate, Tokens, Linguo, PoH, Governor, Dispute Resolver\) or an external one \(Reality.eth\).

{% hint style="info" %}
In the future, it will also be possible to use Kleros dispute resolution through:

* **Subcontracting disputes to intermediary mediation entities integrated w/ Kleros**

  * A mediation organization could format and forward the dispute to Kleros for you.
  * Learn more about it [here](https://blog.kleros.io/kleros-layer-2/)

* **Kleros API**
  * A fully managed solution \(over REST API\) for actors not willing to interact with on-chain contracts themselves.
{% endhint %}

