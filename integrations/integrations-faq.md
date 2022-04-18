---
description: Frequently Asked Questions by Projects integrating with Kleros
---

# Integrations FAQ

## **If I integrate with Kleros, do I need to ask my users to hold some PNK?**

Your product users do not need to interact with PNK at all. Kleros token is completely absent from your user flows and abstracted from your product interface. PNK is only needed for jurors to be drawn for jury duty and provide the dispute resolution as a service for your application.

_**A useful analogy**:_ If your DeFi project gets its price data from Chainlink oracles, it does not mean that your users need to own LINK. The LINK token powers the service provided by the oracle middleware. Your users never see it. It is the same for PNK.

## **Can I replace Kleros with a community vote or arbitration contract comprised only of my governance token holders?**

It may be tempting to give additional utility to your project's native governance token by having it also handle the dispute resolution through voting, but it presents several weaknesses and risks:

_**Rebuilding a weaker single-use court system :**_ If a Dapp recreates a system where a few randomly selected token holders vote, then they will basically have to recreate a version of a dedicated arbitration system such as Kleros Courts - except that if it is the only utility of their token, then it won't benefit from network effects that Kleros has, where combining a lot of use cases together gives the token enough value to resist 51% attacks. Moreover, If they tack Kleros-like features onto a token that does something else/has value for some other reason, they will not have any guarantee that the culture around their token will develop appropriately so that people reliably stake so that their court can have good resistance to those same 51% attacks.

_**Community-wide Vote Fatigue:**_ If a project uses its native governance token to have every token holder vote on every dispute ever raised, it will require a massive duplication of effort and might be plagued by low response rates progressively creating security issues in the form of claim validation vote that could easily be swayed by a single whale.

_**Biased Jury:**_ If a governance token "whale" gets into a dispute on your product and that arbitration goes through a vote with the same governance token, then this whale will be incentivized to vote with no regard to the truth and to unfairly tip the scale in its favor.

## How much does using Kleros cost?

Kleros Courts are currently only deployed on Ethereum mainnet.

_**Gas fees:**_ As for any smart contract, interacting with Kleros means paying gas fees when sending a transaction. The gas price will vary 24/7 depending on the current utilization of the whole Ethereum blockchain and thus, the gas fee will also vary with it.

_**Arbitration fees:**_ This is a product of the number of jurors you choose to draw into the dispute and the juror fee applicable to the (sub)court of choice (juror fees are fixed per court).

We can't use anonymous jurors in my use case. Can we tweak Kleros to only select jurors from a pre-vetted pool?

At this point, it is not possible to select jurors from a pre-defined pool. Anyone having tokens can self-select to be drawn randomly as a juror.

## Which project is currently using Kleros and how has it worked for them?

We invite you to take a look at our [Live Integrations](https://kleros.gitbook.io/docs/integrations/live-and-upcoming-integrations) page for the answer.
