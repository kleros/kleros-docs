---
description: The heart of the Kleros Dispute Resolution Protocol
---

# Court

⚖️ [Kleros Court App](https://court.kleros.io) ⚖️

**Kleros Court** is the core engine of the Kleros portfolio of services and products.\
\
It is a dispute resolution protocol that provides arbitration for the type of subjective conflicts that smart contracts do not address. This is done by having a set of jurors randomly drawn for each dispute and having them vote to ensure a given verdict.

![](<../../.gitbook/assets/image (17).png>)

{% content-ref url="../../integrations/analytics.md" %}
[analytics.md](../../integrations/analytics.md)
{% endcontent-ref %}

### Understanding How Kleros Works

Kleros works in a simple way. Disputes are created by dApps and sent to the [Kleros Court](http://court.kleros.io). All dApps send their disputes to the 'arbitrator side' (meaning the court), thus their side is called the 'arbitrable side'.

![Arbitrable side and Arbitrator side](../../.gitbook/assets/aa1-2-.jpg)

### Kleros Court Process

The Kleros court process works in the following way:

* Once a Dapp sends a dispute, the system randomly picks jurors in a court specified for the case in question.
* The case enters the evidence submission period where all interested parties (disputing parties, jurors, challengers, and any external agent) are able to submit their evidence.
* After the evidence period is finished, jurors are able to vote on the case. For now, Kleros jurors can vote 'Yes', 'No' and 'Refuse to Arbitrate'. The third option is available in cases of an invalid submissions, illegal or morally unacceptable content or evidence.

![](../../.gitbook/assets/kleros-arbitration.png)

{% content-ref url="kleros-juror-tutorial.md" %}
[kleros-juror-tutorial.md](kleros-juror-tutorial.md)
{% endcontent-ref %}

### Courts and sub-courts

When creating an arbitrable contract, parties should choose a type of court specialized in the topic of the contract. A software development contract will choose a software development court, an insurance contract will select an insurance court, etc. The structure of the set of courts forms an arborescence with the General Court as the root.

![Tree of Kleros Courts](../../.gitbook/assets/kleros-courts-tree-1-.jpg)

The description of the courts can be found on the [Kleros Court App](https://court.kleros.io) by clicking on "Join a court" button.

{% content-ref url="../../integrations/types-of-integrations/1.-dispute-resolution-integration-plan/smart-contract-integration.md" %}
[smart-contract-integration.md](../../integrations/types-of-integrations/1.-dispute-resolution-integration-plan/smart-contract-integration.md)
{% endcontent-ref %}
