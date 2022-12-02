---
description: Truly trustless and decentralized claim arbitration for Insurance protocols
---

# DeFi Insurance

## Key challenges

DeFi Insurance has been one of the fastest-growing sectors of DeFi in the last two years, and will likely accelerate in importance as the number of cataclysmic events in Web3 increase in frequency.&#x20;

Setting up a fully decentralized claims management process is no easy feat. While the process for setting up staking and protection pools is relatively well understood, many protocols still struggle with deciding on the right setup for claim approvals for indemnity insurance. Besides that, parametric insurance providers also struggle with finding the right oracle solutions that can provide the data they need to detect the wide range of possible payout conditions.

Kleros solves these problems for you.

## **How Kleros can be used**

### Kleros as arbitrator for indemnity insurance claims

An insurance claim can be simply seen as a conditional payment that is dependent on the answer to a question. In the context of DeFi indemnity insurance, the question can be something like this:

{% code overflow="wrap" %}
```
The claimant ([ETH_address]) has requested a compensation for damages covered by [Name_of_your_protocol] for the amount of [amount] USDC. 
The evidence of the damages to the claimant can be found here [link to evidence document on IPFS], and the applicable cover policy can be found here (link to policy document on IPFS). 

Should the claim be paid out?
```
{% endcode %}

### Kleros as subjective oracle for triggering parametric insurance payouts

Similar to indemnity insurance, parametric insurance are also conditional payouts, but the questions to be answered are much simpler. Here is an example of a question that can be used in drought insurance:

{% code overflow="wrap" %}
```
Has there been less than 10mm of recorded rainfall in total over the city of Dar es Salaam over the past 90 days prior to the opening date of this question?
```
{% endcode %}

## Integration options

### Through the Kleros+Reality.eth oracle

This is by far the easiest solution, and supports both no-code and smart contract integrations.

The questions above can be posed as a question to the [**Kleros+Reality.eth oracle**](https://kleros.gitbook.io/docs/products/oracle) through either the user interface on [Reality.eth](https://reality.eth.limo) or by interfacing directly with the [Reality.eth smart contract](https://kleros.gitbook.io/docs/integrations/types-of-integrations/1.-dispute-resolution-integration-plan/channel-partners/how-to-use-reality.eth-+-kleros-as-an-oracle)[s](https://kleros.gitbook.io/docs/integrations/types-of-integrations/1.-dispute-resolution-integration-plan/channel-partners/how-to-use-reality.eth-+-kleros-as-an-oracle). Should the escalation game within Reality.eth prove insufficient for resolving the claim correctly, the case can be escalated to Kleros for arbitration.

### Building a custom dApp

If you would like to build a custom integration that's tightly integrated with the rest of your platform, you can follow in the footsteps of [Unslashed Finance](https://blog.kleros.io/welcome-to-decentralized-insurance-kleros-x-unslashed-finance/), who built a custom 'optimistic' claim approval flow that uses Kleros as arbitrator.&#x20;

## Key insurance partners and users&#x20;

Kleros is the leading claim arbitration solution in DeFi insurance, and is trusted by the leaders of the DeFi insurance space:

* Unslashed Finance
* Etherisc
* Athena
* Ensuro
* Union Finance
* Atomica
* API3
* Solace

## Get in touch!

Reach out to our integrations team on [Telegram](https://t.me/daisugist) or [email](mailto:integration@kleros.io) to start the conversation!
