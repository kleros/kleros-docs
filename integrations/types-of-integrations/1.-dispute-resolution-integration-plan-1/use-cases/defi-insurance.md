---
description: Solutions for decentralized Insurance protocols
---

# DeFi Insurance

### Decentralizing claim management in DeFi Insurance

An insurance claim is a formal request by a user to an insurance product for coverage or compensation for a covered loss or policy event. In the case of a decentralized finance insurance organization, a designated authority (DAO, Multi-sig, centralized resolver,...) should validate this claim (or deny it). If it is approved, the insurance contract will issue payment to the insured or an approved interested party on behalf of the insured.

![Insurance governance token holder that will see the value of its holdings decrease in case of a hack payout: “I don’t see any damage/hack here, sir.”](../../../../.gitbook/assets/0.png)

Legacy insurance companies often handle claims in a non-transparent and indisputable manner. The challenge for new DeFi Insurance products (apart from offering coverage for investments that could not be covered anywhere else) is therefore to offer a trust-minimized and fair mechanism to manage and arbitrate claims.

### The pitfalls of managing claim management through DAO governance

The solution most often used by DeFi insurance projects is to delegate the challenges above to their DAO governance. While it might seem intuitively like a great solution, it is often fraught with dangers and pitfalls. Here are a few of them:&#x20;

* **Conflict of interest for the DAO token holders**\
  There is a fundamental conflict of interest whenever a DAO governing an insurance protocol is tasked with its own claim approval process. On one hand, they have the duty to ensure rightful claims are paid out, thus allowing the protocol to serve its intended purpose. On the other hand, every successful claim chips away at their own capital staked in the protocol. Unless the voters/deciders in the claim approval process has no direct interest in the approval or rejection of a claim, the process cannot be said to be credibly neutral.
* **Risk of creating a weaker single-use court system**\
  If a DeFi protection app recreates a system where a few randomly selected governance token holders vote, then they will basically have to recreate a version of a dedicated arbitration system such as Kleros Courts. They will also not have any guarantee that the culture around their token will develop appropriately, as it takes time and effort to cultivate a community that is educated on jury duty in the decentralized world.&#x20;
* **DAO governance is weakened**\
  The lock-up/staking of tokens is a cornerstone of any tokenomic design of an effective and honest decentralised court. What this means is that tokens locked up for court participation cannot be used for governance, and vice versa. Because of this, attempting to combine two use cases into a single token dramatically increases the vulnerability of both to 51% attacks. Furthermore, a court operating on the won't benefit from the network effects that Kleros has through working with a huge network of token-holding juries, arbitrating for multiple DAOs.
* **Community-wide vote fatigue**\
  If an insurance project asks every token holder to vote on every claim ever raised, it will require a massive duplication of effort and might be plagued by low response rates progressively creating security issues in the form of claim validation vote that could easily be swayed by a single whale. If voting is made optional, the results could skew towards the goals of those with specific agendas that may not be in the interest of the community, opening the door for collusion or vote buying.

Most DeFi insurance projects operate with a (semi-)centralized process that employs a multi-step voting process to manage their claims. The claims will first often go through a community-wide approval or rejection process before being reviewed by a final committee that acts as the final decision-maker.&#x20;

![Common Claim Process Template for DeFi Insurance projects](../../../../.gitbook/assets/1.png)

However, the fact that the first round of vote by the governance token holders can be overridden every time by a committee of a handful of experts without a possibility to challenge them can make the whole process look like decentralization theater.

Some other DeFi protection initiatives will let the users directly choose which arbitrator they want for the protection contracts they just created. And finally, the rest will be based on an automated incident monitoring system keeping an eye on events that can be detected and published on-chain (like a DAO emergency shutdown or a stablecoin on-chain price feed going below a specific value). While these setups automate and decentralize the fact-finding aspects of an insurance claim, the decision of how much the claimable damages are remain something a problem that requires a dispute resolution process.

## Why Kleros is a better solution

Kleros offers better decentralized solutions to the challenges mentioned above, which are explained in this section.

### Kleros as a fair and trustless Claim Arbitration System

Kleros recommends a Claimant-Challenger model for decentralizing your claim management process: a solution that can be achieved using Kleros's [Dispute Resolver](https://resolve.kleros.io/), which allows claims and disputes from an insurance protocol to be passed on to the Kleros Courts for arbitration.

An arbitrable Claim Management contract can be written to interface between the Kleros Courts and the insurance protocol's payout contracts, allowing the decisions of the jurors in the Kleros Courts to translate to decision on claims within a DeFi insurance protocol.

The Claimant-Challenger model follows the standard request-challenge protocol with a crowdfunded appeal system, where the claim submitter registers the claim and anyone can challenge said claim, thus creating a dispute in Kleros Court. An insuree would then be able to submit a claim using that contract and to provide the information related to his claim. If their claim is challenged, a dispute will be opened in the relevant Kleros Court. If not challenged, the claim will be considered valid and a payout will be triggered. An illustration of this process can be seen below:

![The most commonly prescribed claims process for insurance protocols using Kleros.](../../../../.gitbook/assets/defi-insurance-project\_1.png)

The Claim Management contract also can be designed to go beyond just simple Approve/Reject decisions, incorporating functionalities such as the ability for counter-offers to claims to be raised by parties such as the DAO governance or designated claim oversight teams.

By doing this, an insurance project will simplify its development efforts by focusing on just the insurance mechanisms, while outsourcing the arbitration process to a decentralized and uncorrelated system.

In summary, in the case of claim systems using Kleros as Claims arbitrator, the final ruling will be made if:

* no claim challenge has been raised
* no appeal has been made after a previous decision by jurors
* a decision has been made in the highest General Court with no more appeal possible.

#### Incremental adoption of Kleros

There are many ways to incorporate Kleros into your DeFi insurance protocol, and it is possible to only adopt the elements that add the most benefit now, and incrementally move towards a more comprehensive integration when the need arises.

There are at least 4 ways at which Kleros can be integrated into a decentralized claims process:

1. As one of the arbitration systems that can be selected when deploying a coverage contract,
2. As one of the signatories in a multi-sig committee taking the final decision about a claim.
3. As a ruler of last resort for claimants to dispute the rulings of a DAO's governance/central committee.
4. As the single default source for ruling when a claim is challenged

An additional complementary integration would be for insurance projects to share a single common registry of “official DeFi hacks/exploits” that could be built as a [Kleros Curate](https://kleros.io/curate/) list, and have automatic payouts tied to the acceptance of a new entry into the list.

In conclusion, if you don’t want to reinvent the wheel and expose your project to badly designed dispute resolution incentives, you should [reach out to us](mailto:contact@kleros.io) to seamlessly integrate the Kleros dispute resolution protocol within your Insurance project.
