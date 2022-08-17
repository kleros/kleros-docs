---
description: >-
  When you want to integrate your smart contract with Kleros Court for a fully
  trustless integration.
---

# Smart contract integration with Kleros Court (Arbitrator)

Kleros Court is the implementation of an arbitrator as per the [Arbitration standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) we developed. Most integrations consist in building or customizing an Arbitrable app so it can request arbitration to Kleros Court. Once you integrate with the Arbitration standard, you (or your users) will be able to choose any arbitrator that follows the standard to solve disputes, including Kleros.

![](<../../../.gitbook/assets/image (48) (3) (3) (3) (2) (1) (1) (1) (1).png>)

You can build an arbitrable smart contract or ensure your existing smart contracts are compliant with the Arbitrable interface:

* From scratch by applying the [Arbitration standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) (and/or using the [Archon library](https://kleros.gitbook.io/docs/developer/archon-ethereum-arbitration-standard-api)),
* By customizing one of our [examples](https://github.com/kleros/erc-792/tree/master/contracts/examples) or looking at[ live integrations](https://kleros.gitbook.io/docs/integrations/live-and-upcoming-integrations),
* By working with [Cooperative Kleros](mailto:contact@kleros.io) to adapt yours to the standard or creating a connector,

## Create/Modify the Arbitrable app to be integrated with Kleros Court

If you want to integrate with Kleros for dispute resolution, you will have to create an `Arbitrable` smart contract as per the[ Arbitration Standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) that will allow executing the following flow:

![](../../../.gitbook/assets/flow\_arbitrable-arbitrator-smart-contract.png)

In the `Arbitrable` contract, you will have to define at least:

* the address of the `Arbitrator` contract (look at the top of this page for the addresses of Kleros Court Arbitrators.
*   Some extra data to set up the arbitration (that will specify the sub-court to be used and the number of vote required)

    * List of subcourt IDs below,
    * We recommend starting with 3 votes.
    * Script to generate the arbitrator extra data

    `generateArbitratorExtraData = (subcourtID, noOfVotes) => 0x${parseInt(subcourtID, 10).toString(16).padStart(64, "0") + parseInt(noOfVotes, 10).toString(16).padStart(64, "0")};`
* (If appeals are allowed) Stake multipliers representing multipliers of the appeal cost that a party must pay for a new round (in basis points)

{% hint style="info" %}
**Kleros Court Deployments (Arbitrator)**

* [Kleros Court (Arbitrator) on Ethereum Mainnet](https://etherscan.io/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069)
* [Kleros Court (Arbitrator) on xDai](https://blockscout.com/xdai/mainnet/address/0x9C1dA9A04925bDfDedf0f6421bC7EEa8305F9002)
* [Kleros Court (Arbitrator) on Sokol](https://blockscout.com/poa/sokol/address/0xb701ff19fBD9702DD7Ca099Ee7D0D42a2612baB5/)
* [Kleros Court (Arbitrator) on Ethereum Ropsten](https://ropsten.etherscan.io/address/0x9643e91d3734b795e914a64169147b70876272ba)
* [Kleros Court (Arbitrator) on Ethereum Kovan](https://kovan.etherscan.io/address/0x60b2abfdfad9c0873242f59f2a8c32a3cc682f80)
{% endhint %}

{% hint style="info" %}
**List of Subcourt IDs (Ethereum Mainnet)**\
\
The General Court ID is 0.

1. Blockchain
2. Non-Technical
3. Token Listing
4. Technical
5. Marketing Services
6. English Language
7. Video Production
8. Onboarding
9. Curation
10. Data Analysis
11. Statistical Modeling
12. Curation (Medium)
13. Spanish-English Translation
14. French-English Translation
15. Portuguese-English Translation
16. German-English Translation
17. Russian-English Translation
18. Korean-English Translation
19. Japanese-English Translation
20. Turkish-English Translation
21. Chinese-English Translation
22. Corte General en Espanol
23. Humanity Court
{% endhint %}

You can also check the subcourt IDs on community-owned [http://klerosboard.com/](http://klerosboard.com).

Learn more about how to build an Arbitrable app integrated with the Kleros Court arbitrator by reading the ERC-792 Arbitration Standard linked below.

{% content-ref url="../../../developer/erc-792-arbitration-standard.md" %}
[erc-792-arbitration-standard.md](../../../developer/erc-792-arbitration-standard.md)
{% endcontent-ref %}

## Test it with the Centralized Arbitrator

You can test your arbitrable app on mainnet and most testnets by deploying a centralized arbitrator that you control (= you can easily give rulings/decisions and set the arbitration fee) and testing the integration this way. More details about the arbitrator on the page linked below.

{% content-ref url="integration-tools/centralized-arbitrator.md" %}
[centralized-arbitrator.md](integration-tools/centralized-arbitrator.md)
{% endcontent-ref %}

For more details, please consult the [Arbitration Standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) documentation, have a look at the examples of implementations shared [here](https://github.com/kleros/erc-792/tree/master/contracts/examples), or contact us on Discord, Telegram, Slack, or send a mail to contact@kleros.io (links on the bottom left).
