---
description: >-
  How Kleros implements Credibly Neutrality in the context of decentralized
  dispute resolution.
---

# Kleros & Credible Neutrality

'Credible Neutrality' is a concept introduced by Vitalik Buterin in an [inaugural blog post on Nakamoto in 2020](https://nakamoto.com/credible-neutrality/), where it was said that "a mechanism is credibly neutral if just by looking at the mechanism’s design, it is easy to see that the mechanism does not discriminate for or against any specific people". 4 primary rules were mentioned as fundamental to any credibly neutral mechanism:

1. Don’t write specific people or specific outcomes into the mechanism
2. Open source and publicly verifiable execution
3. Keep it simple
4. Don’t change it too often

Kleros has implemented these principles in the design of its Court, and added additional provisions to enhance its credible neutrality in the area of decentralized dispute resolution.

#### **Rule 1: Don’t write specific people or specific outcomes into the mechanism**

* Kleros utilizes **sortition** (selection by the random drawing of lots) in the juror selection process, making it very difficult for disputants and voters to collude.&#x20;
* As an independent arbitration service, Kleros has no direct interest in the outcome of a dispute. This is especially relevant in high-value [insurance](../../integrations/types-of-integrations/1.-dispute-resolution-integration-plan/use-cases/defi-insurance.md) or DAO governance disputes.

**Rule 2: Open source and publicly verifiable execution**

* The Kleros Court's code base is entirely open source and verifiable, and all evidences and voting activity within the Kleros Courts are publicly accessible.
* All the processes in Kleros Court (e.g. dispute initiation, evidence submission, ruling challenge, participation in the jury) are trustless and permissionless, allowing anyone to participate, engage and influence the course of a dispute.

#### **Rule 3: Keep it simple**

* The **purpose-specificity** of Kleros (i.e. the focus on dispute resolution) prevents community voting fatigue within DAOs and prevents the crypto-economic design of the DAO's governance setup to interfere with the dispute resolution process.

#### Rule 4: Don't change it too often

* The settings determining the rules and crypto-economics of Kleros Court are adjustable only by governance votes.
* The policy for each dispute are immutable after a dispute has been initiated, preventing the rules of a dispute to change during the course of a dispute.

#### Additional safeguards

* Kleros Court has an appeal system that allows anyone who disagrees with a ruling to challenge it. This prevents random voting, 51% attacks and [P + epsilon](https://blog.ethereum.org/2015/01/28/p-epsilon-attack/) attacks from involving a larger pool of jurors and allowing more evidence and arguments to be presented.
