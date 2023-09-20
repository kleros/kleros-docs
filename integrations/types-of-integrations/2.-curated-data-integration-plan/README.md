---
description: >-
  Solution plan for using the data from curated data registries created using
  Kleros
---

# 2. Curated-data integration plan

## Introduction

While resolving disputes is the most direct way to integrate with Kleros, the Court can also be used to power the decentralized curation of information.&#x20;

Here are a few examples:

* Contract metadata registries built with [**Kleros Curate**](../../../products/curate/)
  * [Tokens registry](https://curate.kleros.io/tcr/100/0x70533554fe5c17CAf77fE530f77eAB933B92af60?ref=blog.kleros.io)
  * [Address tags registry](https://curate.kleros.io/tcr/100/0x66260C69d03837016d88c9877e61e08Ef74C59F2?ref=blog.kleros.io)
  * [Contract-Domain Name (CDN) registry](https://curate.kleros.io/tcr/100/0x957A53A994860BE4750810131d9c876b2f52d6E1?ref=blog.kleros.io)
* [NFT registries](https://www.reddit.com/r/loopringorg/comments/srji2h/introducing\_kleros\_curated\_nft\_registry\_a\_work\_in/)
* Identity registries
  * [**Proof-of-Humanity**](https://www.proofofhumanity.id/)

A full list of Kleros's existing integrations and partnerships can be found [here](../../live-and-upcoming-integrations.md).

Using Kleros's curated data registries always consists of the following steps, which are outlined below.

{% hint style="info" %}
To help you keep track of your integration process, click [**here**](https://docs.google.com/document/d/1al1JwX8LPQzNDKSmG\_IIiLwqwtEVhnlGX9K\_PI-o08M/copy?copyComments=true) to make a copy of our  Curated Data model integration plan!
{% endhint %}

## Key integration steps

Following these steps in sequence will ensure that your integration is secure and runs smoothly for both you and your users.

### 1. Determine your data requirements

Each curated registry of Kleros has a unique acceptance policy and field set for each entry onto the list. You can use one of the ready-made registries if it fits your needs. Otherwise, feel free to create your own list from scratch.&#x20;

#### 1.1 Using one of the existing registries

The [main page](https://curate.kleros.io/) of Kleros Curate features a number of existing curated registries that have met certain quality standards in their policy and format. Note that the registries are specific to a chain, and you will see different lists on xDai/Gnosis chain than on Ethereum Mainnet.&#x20;

A few of the most important lists that are related to contract security metadata are:

1. [Tokens registry](https://curate.kleros.io/tcr/100/0x70533554fe5c17CAf77fE530f77eAB933B92af60?ref=blog.kleros.io)&#x20;
2. [Address tag registry](https://curate.kleros.io/tcr/100/0x66260C69d03837016d88c9877e61e08Ef74C59F2?ref=blog.kleros.io)&#x20;
3. [Contract-Domain Name mappings](https://curate.kleros.io/tcr/100/0x957A53A994860BE4750810131d9c876b2f52d6E1?ref=blog.kleros.io)

There is also the [Proof-of-Humanity project](https://www.proofofhumanity.id/), which is a Sybil resistant curated registry of real humans (linked to their ETH addresses) on the Ethereum blockchain.

#### 1.2 Creating your own TCR

If none of the lists mentioned in the links above suit your needs, feel free to create your own registry by following the instructions here:

[kleros-curate-tutorial.md](../../../products/curate/kleros-curate-tutorial.md "mention")

{% hint style="info" %}
Save time and avoid omissions by using our[ model TCR acceptance policy here!](https://docs.google.com/document/d/1R-CyzbJYVkIlRM6JSUX-Gm1QAHsHe6PDdJ1uxeoNfjs/copy?copyComments=true)&#x20;

Refer to the policy writing guide [here](../../policy-writing-guide.md) if you need help adjusting it to your use case.
{% endhint %}

### 2. Determine the method for data retrieval

We recommend using one of the subgraphs built using [The Graph's](https://thegraph.com/en/) technology to query for the information one of the existing curated lists.&#x20;

[interacting-with-arbitrable-app.md](interacting-with-arbitrable-app.md "mention")

### 3. Build your frontend (if applicable)

Once the curated registry has been decided/created, and the query for retrieving the data is settled, you can proceed to creating the frontend to display the information (if applicable for your use case).

### 4. Communicate all the above to your users

Once all the above are done, it is time to communicate the involvement of Kleros in the dispute resolution processes of your platform to reduce any potential confusion around the processes. This includes but is not limited to:

1. Educating them on the decentralized nature of the curated registries, that the data is not under the control of Kleros (the organisation).
2. Educating them on how to [submit and challenge entries](../../../products/curate/kleros-curate-tutorial.md) to the curated registries in question.
3. Communicating the process for them to submit additional evidence and raise appeals (if supported).

Once all the above are done, you are ready to go live with Kleros!&#x20;
