---
description: Solution plan for integrating Kleros as an arbitrator to decide on disputes
---

# 1. Dispute resolution integration plan

## Introduction

Using [**Kleros Court**](../../../products/court/) to decide on disputes is the most direct way to use Kleros. The ways to use this are numerous, but here are a few of them:

* **Escrow** (see [Kleros Escrow](../../../products/escrow/))
* **(DeFi) insurance claim disputes** (see our partnership with [Unslashed Finance](https://blog.kleros.io/welcome-to-decentralized-insurance-kleros-x-unslashed-finance/))
* **Bounty and job payment disputes** (see the integration with [Feature.sh](https://docs.feature.sh/guides/challenge-a-claim))
* **Securing oracle result resolutions** (see the [documentation](https://kleros.gitbook.io/docs/integrations/types-of-integrations/how-to-use-reality.eth-+-kleros-as-an-oracle) and the [Kleros+Gnosis’s partnership](https://blog.kleros.io/kleros-x-safesnap/))
* **Real-world arbitration** (see this example [from Mexico](https://blog.kleros.io/how-to-enforce-blockchain-dispute-resolution-in-court-the-kleros-case-in-mexico/))

A full list of Kleros's existing integrations and partnerships can be found [here](../../live-and-upcoming-integrations.md).

Integrating Kleros into your dispute decision process will always involve 5 main steps and they are outlined below.&#x20;

{% hint style="info" %}
To help you keep track of your integration process, click [**here**](https://docs.google.com/document/d/11HUXGV25cy\_DMKXJvIn7LeAGBjY7ohXtO5uNN\_C9wI0/copy?copyComments=true) to make a copy of our  Dispute Resolution model integration plan!
{% endhint %}

To help you keep track of the process, click here to make a copy of our model integration plan!

## Key integration steps

Following these 5 steps in sequence will ensure that your integration is secure and runs smoothly for both you and your users.

### 1. Determine the conditions for escalation and enforcement

An integration with Kleros implies that you have chosen for the jurisdiction of Kleros Court for the resolution of a dispute.&#x20;

As with real-world courts, Kleros Court is only an arbitration service, and it is important to remember that our decentralized jury only takes care of the ruling on a dispute given certain facts/evidences and policy documents. Enforcement of the ruling is out of scope for Kleros, and needs to be carefully taken care of by your service/platform/dApp.&#x20;

What this means in concrete terms is that you need to decide on and document the following before escalating a dispute to Kleros:

* **Escalation criteria**: when your platform will allow an escalation of a dispute to Kleros&#x20;
  * Example: _escalation is only allowed after a first round of dispute resolution has taken place within your platform, and the disputed transaction above a certain transaction value._
* **Enforcement criteria**: what criteria need to be fulfilled for your platform/service to commit to enforcing a ruling from Kleros
  * Example: _enforcement is dependent on the agreement of DAO governance or approval committees, if the enforcement is governed by a 'multisig', of which Kleros Court represents only 1-of-n signers._

{% hint style="info" %}
If a smart contract integration with Kleros Court is used (see [**Step 4** ](./#4.-integrate-with-the-court)below), the escalation and enforcement criteria could be built into the logic of your 'Arbitrable' contract.
{% endhint %}

### 2. Write a good 'Dispute Policy'

The dispute policy is the primary document presented to the jurors to inform them on how to resolve a dispute. It is similar to a piece of real-world law referenced during cases to decide a dispute, but in this case only pertaining to your specific integration.&#x20;

Jurors will use three main categories of information to decide on their vote:

1. The dispute policy
2. The evidence provided (which can potentially be submitted by anyone on the internet)
3. If the above two are insufficient for deciding on the case, then the policies of the Court in question are considered.

Writing a good dispute policy is therefore crucial to the fair and speedy resolution of a case, as it sets the backdrop against which the pieces of evidence are considered.

{% hint style="info" %}
Save time and avoid omissions by using our[ model policy here!](https://docs.google.com/document/u/1/d/1UYJ2mKSPhAn0-erAGa9MLiKQr25lpi-YPcMQrJyMOz4/copy?copyComments=true)&#x20;

Refer to the policy writing guide [here](../../policy-writing-guide.md) if you need help adjusting it to your use case.
{% endhint %}

### 3. Determine the Court parameters

Once the above has been done, the next step is to decide on

1. The **Court** where you would want your cases to be arbitrated in
2. The **number of jurors** you want to draw into the first round of arbitration.

Choosing the right court for your case ensures that it will be resolved in the quickest and most efficient manner. Do keep in mind the choices in this section directly affect the cost of arbitration; it is a function of the number of jurors drawn into the case, and the cost of involving an additional juror differs with each court.

For an overview of the courts available on Ethereum Mainnet and their parameters, please refer to the community-managed [Klerosboard](https://klerosboard.com/court/?network=mainnet).

{% hint style="info" %}
A guide on the recommendation parameters for different use cases will be made available soon. For now, please reach out to us at [integrations@kleros.io](mailto:integrations@kleros.io) for guidance.
{% endhint %}

### 4. Integrate with the Court

There are two ways to use Kleros Court for your dispute resolution:

#### A. Smart contract integration

The best way to integrate with Kleros is to invest in a smart contract integration with Kleros Court. While it takes work to write and audit an 'Arbitrable' smart contract (complying with the [**ERC-792**](../../../developer/arbitration-development/erc-792-arbitration-standard.md) standard), it does allow for a **trustless** integration and can fully address user concerns of centralized control or censorship.&#x20;

There are two ways to go about it:

1.  **A fully ERC-792 compliant integration**, in which the full integration guide for this technical integration can be found here:

    [smart-contract-integration.md](smart-contract-integration.md "mention")
2. **A** **greatly simplified variant of the ERC-792 integration** using an ['arbitrable-proxy' contract](../../../developer/arbitration-development/arbitrable-proxy.md), in which the evidence and appeal logic management and UI components are outsourced to Kleros-written smart contracts and frontends. All you need to do is for your pseudo-Arbitrable contact to call the `createDispute` function and poll for the ruling from the arbitrable-proxy afterwards.



#### B. A standalone 'Recognition-of-Jurisdiction' (RoJ) integrations

Sometimes there might be reasons why a full smart contract integration is not feasible for you (yet):

* The case involves an off-chain dispute that cannot be trustlessly integrated with Kleros (e.g. off-chain video game disputes, real-world arbitration cases).
* Kleros Court is not (yet) available on the chain/L2 you are on.
* There are no resources to perform the full smart contract integration in the near term.
* You prefer to test out the process with Kleros before investing development resources.

In such cases, you can start with a simple Recognition-of-Jurisdiction (aka **RoJ**) setup in which disputes are created 'standalone' on [resolve.kleros.io](https://resolve.kleros.io/), and your service/platform simply pledges (to your users) to enforce the ruling of Kleros.&#x20;

While this is not a trustless integration method, it does allow you to introduce Kleros's rulings into your dispute resolution process very quickly, and allows you to test usage before investing in a full smart contract integration.

### 5. Communicate all the above to your users

Once all the above are done, it is time to communicate the involvement of Kleros in the dispute resolution processes of your platform. This is essential for the smooth operations of your dispute resolution process and reduces any potential confusion when disputes eventually arise. This includes but is not limited to:

1. Ensuring that the dispute policy is publicly available and pinned using an immutable file storage system (e.g. [IPFS](https://ipfs.io/))
2. Publishing and communicating the **escalation** and **enforcement** criteria.
3. Inform users on how to submit additional evidence and raise appeals (if applicable for your integration).

Once all the above are done, you are ready to go live with Kleros!&#x20;

{% hint style="info" %}
Reminder: To help you keep track of your integration process, click [**here**](https://docs.google.com/document/d/11HUXGV25cy\_DMKXJvIn7LeAGBjY7ohXtO5uNN\_C9wI0/copy?copyComments=true) to make a copy of our model integration plan!
{% endhint %}

## Ready-made integrations

Kleros Court has integrations with various ready-made integrations, built either by ourselves or one of our channel partners.

### Escrow

For the usage of Kleros Court to decide if assets in escrow should be released, check out [Kleros Escrow](../../../products/escrow/), which can be used [standalone](http://escrow.kleros.io) or integrated by calling its [smart contracts](https://github.com/kleros/kleros-interaction/tree/master/contracts/standard/arbitration).

### (Optimistic) Oracle solutions

Kleros has a close integration with [Reality.eth](https://reality.eth.link/) (formerly Realitio), acting as an arbitrator to rectify oracle results in case the results are contested. Check out the full details in the page here: [how-to-use-reality.eth-+-kleros-as-an-oracle.md](channel-partners/how-to-use-reality.eth-+-kleros-as-an-oracle.md "mention")

### Securing Snapshot votes

Gnosis's [Zodiac Reality Module](https://gnosis.github.io/zodiac/docs/tutorial-module-reality/get-started/) makes use of the Reality+Kleros integration mentioned above to securely translate [Snapshot](https://snapshot.org/) voting results into on-chain transactions.&#x20;

## Integration tools

If you are performing a smart contract integration, you can use the centralized arbitrator below to test your integration:

[centralized-arbitrator.md](integration-tools/centralized-arbitrator.md "mention")

If you would like to use the existing escrow smart contracts of Kleros behind [escrow.kleros.io](https://escrow.kleros.io), you can also make use of the following tools.

[escrow-sdk.md](integration-tools/escrow-sdk.md "mention")

[escrow-react-widget.md](integration-tools/escrow-react-widget.md "mention")

