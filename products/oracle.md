---
description: >-
  Crowd-sourced on-chain smart contract oracle system in collaboration with
  Reality.eth
---

# Oracle

Kleros Oracle is a product combining Kleros dispute resolution with Reality.eth cryptoeconomic mechanism for verifying real world events on-chain, to deliver a subjective oracle solution able to answer absolutely any question with a publicly verifiable answer.

## How does it work?

Anyone (individual or dapp) can submit a question to the Reality.eth platform while specifying Kleros as the final arbitrator. For example:

* Who won the gold medal in the individual kata category in the Karate World Championship in 2004?
* In which month and year was the first version of the game ‘_The Curse of Monkey Island_’ released?

In order to create the right incentives, when answering the question, users are required to **post a bond**. If other users believe that the answer is wrong, they can challenge it by doubling the bond and providing a new answer. After each answer, a countdown period begins during which others can submit a different answer. When the countdown period expires, the last person to have posted an answer receives the bond, as well as the reward posted by the asker.

Through this bond escalation mechanism, most questions will rapidly get an answer when no different answer is submitted. However, at any point of the answering process in Reality.eth (or when the maximum bond is reached), anyone can "apply for arbitration" to bring in Kleros as an external arbitrator to resolve what the right answer is.

Kleros will either confirm the current answer (in which case, the party who provided the final answer receives the bond) or it will provide a different answer (in which case, the new answer is considered definitive and the party who paid the arbitration fees receives the bond).

{% content-ref url="../integrations/types-of-integrations/how-to-use-reality.eth-+-kleros-as-an-oracle.md" %}
[how-to-use-reality.eth-+-kleros-as-an-oracle.md](../integrations/types-of-integrations/how-to-use-reality.eth-+-kleros-as-an-oracle.md)
{% endcontent-ref %}
