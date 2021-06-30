---
description: >-
  People discovering Kleros will often come up with the same doubts and
  questions about the system.
---

# Answers to common Kleros criticism

## Kleros is live and demonstrably working

### FUD \#1 - I only believe in systems that are in production and running, is Kleros even live?

_\(As of June 2021\)_ Kleros Court has been live since 2018 on Ethereum mainnet without any bug or downtime. It has handled and ruled on more than 865 different cases and has a community of more than 760 active jurors staking in 23 different courts \(Source: [KlerosBoard](http://klerosboard.com/)\). Kleros Court has ruled fairly on several controversial cases where millions of dollars were at stake \(cf. [Famous Kleros Cases](https://kleros.gitbook.io/docs/products/court/famous-kleros-cases)\). It is trusted as an unbiased and transparent arbitration layer by multiple Dapps of the ecosystem in different fields \(Prediction Markets, Insurance, DEX, Sybil-Resistance, Marketplaces,... check all those integrations [here](https://kleros.gitbook.io/docs/integrations/live-and-upcoming-integrations)\). 

## Kleros is a fair dispute resolution system

### FUD \#2 - Why should I trust a court with pseudonymous jurors?

Since decisions made in Kleros affect the allocation of resources, there is an incentive for parties to try to bribe or intimidate the tribunal. Pseudonymity is intended to protect jurors from bribing attempts, intimidation, and retaliation. It favors their functional independence \(ability to freely give their judgement\). It also simplifies the process of users becoming jurors and avoids the costs of identity verification. By providing a secure environment and simplifying the selection process, Kleros greatly enlarges the pool of potential jurors. This results in lower arbitration costs and the democratization of access to justice.

### FUD \#3 - If parties can also be jurors, doesn't this pose a conflict of interest? / How can you ensure the jurors are perfectly impartial?

The procedure for random selection of jurors among those who staked tokens in a subcourt makes it extremely hard to be selected on purpose as a juror for a case you are involved in.

It is extremely hard for a juror to be able to be drawn into a court where he has a vested interest. In practice, it would be extremely unlikely for jurors having a vested interest in a case to compose a significant part of the drawn jurors and, even if that were to happen one, the appeal system would allow correcting the ruling;

It is possible that internal biases still exist in jurors. There are some ways within Kleros to present information in such a way that it minimizes this bias. However, it could be also argued that no system can be completely free of biases. For an in depth discussion about this, read [this article](https://medium.com/kleros/kleros-and-mob-justice-can-the-wisdom-of-the-crowd-go-wrong-ef311209ea36).

### FUD \#4  - How can Kleros know jurors have specific expertise if they are pseudonymous?

Kleros jurors self-select into the subcourt where they wish to conduct arbitration. Kleros does not ask for the jurors' real identity or to prove they are qualified to arbitrate disputes in the subcourt where they want to work.

The expertise requirement is conducted via economic incentives. Kleros generates for users the incentive to self-select for the subcourts where they have expertise. Users who self-select into the courts for which they have the right skills will, on average, make money over time. Users who self-select into courts where they don't have the right skills will lose money and tend to abandon the system.

Even though, in theory, jurors may not have subject matter expertise \(anyone can participate in the subcourt\), in practice, users without adequate expertise would suffer an economic loss and exit the subcourt \(unless they wish to lose money while they work, in order to gain those skills\). This works similarly to Wikipedia in the sense that a user who does not have expertise in a field to which an article edited by him relates, may still edit the article but will likely be sanctioned by Wikipedia.

### FUD \#5 - How can I follow the dispute resolution process and be sure it has not been tampered with?

Kleros protocol is committed to full transparency. Its cases are completely open and can be monitored by any person with access to an internet connection. The entire history of cases is also available and published on-chain for reference. Kleros dispute resolution procedure is documented in many places. All cryptoeconomic research is public and the code is open source. A fully working version of Kleros could be replicated in a matter of minutes by anyone with technical skills in blockchain. 

## Kleros can not be gamed and controlled by whales

### FUD \#6 - Is Kleros a court where rich people have more rights than ordinary folks \(because appeals are more affordable for the rich\)?

Anyone can appeal a dispute ruling in Kleros. Most of the time both sides will be asked to contribute fees for the next round of voting to ensure jurors are rewarded and that that the losing side is reimbursed of its paid fees. This appeal system ensures that the final decision of jurors will always converge to the truth and that jurors in initial rounds of voting vote coherently from the start not to be penalized. 

This usually leads to some critics saying that one of the parties with much greater resources than the other can always win a case. We have made a number of design choices regarding the structure of the appeal fee process in order for Kleros to provide just outcomes even in this situation:

1. Appeal fees can be “crowdfunded.” Namely, anyone can contribute a portion of either sides' appeal fees, potentially with many small contributions adding up to cover the whole fee.
2. Crowdfunders who pay part of the fees of the side that ultimately wins are financially rewarded.

People are thus incentivized to look at current appealed cases to spot obvious incorrect rulings and help crowdfund the other side to earn all or part of the rewards. This has been proven effective to deter "rich" parties from trying to win just by appealing several times. Learn more about it [here](https://blog.kleros.io/kleros-decentralized-token-listing-appeal-fees/).

### FUD \#7 - How can you expect fairness from a court that is controlled by a bunch of rich whales?

### FUD \#8 - Can't someone just buy a lot of Kleros tokens and 51% attack the Kleros Court?

In order for a "whale" attacker to flood the juror pool and try to "control the court", they would need to buy enough PNK so that they are selected enough times to be a juror for the same case in order to change the outcome. Generally, this means that the attacks need 51% of the total staked tokens.

An attacker may get lucky in rare circumstances and be selected for two of three juror spots with only a minority of the PNK. However, in order to maintain the attack through the appeal process, it would need to be selected for the majority of the juror spots on larger and larger juries, which will only be possible if the attacker actually has a majority of the PNK. Hence, substantial economic resources in the order of hundreds of millions of dollars would be required to perform a 51% attack.  
  
_**If a "whale" tries to buy 51% of all staked PNK:**_  The PNK market liquidity will dry up. As the attacker buys PNK, it will start to become scarce and each additional PNK will cost more and more. The attacker may not even be able to find 51% of PNK for sale on the open market at any given time and it will progressively cost so much that the attack would not be economically viable.  
  
_**If a malicious attacker did manage somehow to buy a majority of staked PNK:**_  The community would realize that it is under attack, particularly if the attacker uses his new PNK to commit obvious miscarriages of justice. In this case, Kleros would lose credibility as an arbitration platform and the value of PNK would decrease. Then the attacker would take a substantial loss on the PNK she bought, representing a high economic cost to carry out the attack.

_**If a malicious attacker made a successful 51% attack:**_ The community would perform a last-ditch defense by forking the system to remove the attackers’ holdings. Then the market would sort out which version of PNK should be used going forward. This is similar to the [ultimate appeal mechanism of Augur](https://medium.com/kleros/kleros-and-augur-keeping-people-honest-on-ethereum-through-game-theory-56210457649c).

![](../../.gitbook/assets/pnk.png)

On the left, an attacker has managed a 51% attack and starts carrying out obvious miscarriages of justice. The community decides to fork the token removing the attackers’ holdings, and most of the users migrate to the new version of PNK.  
  
More details [here](https://kleros.gitbook.io/docs/pnk-token).

### Questions in progress

"Kleros is broken and unfair because jurors look at policies and do not empathize with people involved in disputes”

"Jurors will give whatever ruling brings them more cases in the future"

“Game theory is just a basic simplification of real life, therefore Kleros is broken"

🚧👷 IN PROGRESS 👷🚧

