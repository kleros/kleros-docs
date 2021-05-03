---
description: >-
  When you want to integrate your smart contract with Kleros Court to get
  dispute resolution services
---

# Integration with Arbitrator

{% hint style="info" %}
**Kleros Court Deployments \(Arbitrator\)**

* [Kleros Court \(Arbitrator\) on Ethereum Mainnet](https://etherscan.io/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069)
* [Kleros Court \(Arbitrator\) on Ethereum Ropsten](https://ropsten.etherscan.io/address/0x9643e91d3734b795e914a64169147b70876272ba)
* [Kleros Court \(Arbitrator\) on Ethereum Kovan](https://kovan.etherscan.io/address/0x60b2abfdfad9c0873242f59f2a8c32a3cc682f80)
{% endhint %}

## Create/Modify the Arbitrable app to be integrated with Kleros Court

If you want to integrate with Kleros for dispute resolution, you will have to create an `Arbitrable` smart contract as per the[ Arbitration Standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) that will allow executing the following flow:

![Standard simplified flow between an Arbitrable and Arbitrator smart contract](../../.gitbook/assets/image%20%286%29.png)

In the `Arbitrable` contract, you will have to define at least:

* the address of the `Arbitrator` contract \(look at the top of this page for the addresses of Kleros Court Arbitrators.
* Some extra data to set up the arbitration \(that will specify the sub-court to be used and the number of vote required\)

  * List of subcourt IDs below,
  * We recommend starting with 3 votes.
  * Script to generate the arbitrator extra data

  `generateArbitratorExtraData = (subcourtID, noOfVotes) => 0x${parseInt(subcourtID, 10).toString(16).padStart(64, "0") + parseInt(noOfVotes, 10).toString(16).padStart(64, "0")};`

* \(If appeals are allowed\) Stake multipliers representing multipliers of the appeal cost that a party must pay for a new round \(in basis points\)

{% hint style="info" %}
**List of Subcourt IDs**  
  
The General Court ID is 0.

1. Blockchain
2. Non-Technical
3. Token Listing
4. Marketing Services
5. English Language
6. Video Production
7. Onboarding
8. Curation
9. Data Analysis
10. Statistical Modeling
11. Curation \(Medium\)
12. Spanish-English Translation
13. French-English Translation
14. Portuguese-English Translation
15. German-English Translation
16. Korean-English Translation
17. Japanese-English Translation
18. Turkish-English Translation
19. Chinese-English Translation
20. Corte General en Espanol
21. Humanity Court
{% endhint %}

{% page-ref page="../../developer/erc-792-arbitration-standard.md" %}

## Test it with the Centralized Arbitrator

You can test your arbitrable app on mainnet and most testnets by deploying a centralized arbitrator that you control \(= you can easily give rulings/decisions and set the arbitration fee\) and testing the integration this way. More details about the arbitrator on the page linked below.

{% page-ref page="../integration-tools/centralized-arbitrator.md" %}

For more details, please consult the [Arbitration Standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) documentation, have a look at the examples of implementations shared [here](https://github.com/kleros/erc-792/tree/master/contracts/examples), or contact us on Discord, Telegram, Slack, or send a mail to contact@kleros.io \(links on the bottom left\).

