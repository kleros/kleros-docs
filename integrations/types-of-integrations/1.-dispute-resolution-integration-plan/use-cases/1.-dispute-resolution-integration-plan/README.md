---
description: A guide on how to use Kleros as a standalone dispute resolution service.
---

# Recognition of Jurisdiction Integration

## Introduction

If you're interested in using the [**Kleros Court**](../../../../../products/court/) for dispute resolution within your project/company with zero technical work, the Recognition of Jurisdiction Integration (RoJ) is a great alternative. This is especially useful for **Protocols or Companies that are:** &#x20;

* Interested in **testing out the workflow with Kleros**&#x20;
* **Traditional companies** (web 2 or web 2.5) that do not interact with the blockchain

Completing the necessary documentation for a RoJ is a relatively short process, which shouldn't take more than a few weeks (or even a few days). \
To begin with the 3 steps, it's recommended to have had a call with a member of the Business Development team beforehand. If you're interested in scheduling an initial call, please contact Marcos at marcos@kleros.io.

Integrating Kleros into your dispute decision process will always involve 3 main steps and they are outlined below.&#x20;

{% hint style="info" %}
To help you keep track of your integration process, click [**here**](https://docs.google.com/document/d/1dn27idjPIfRInrPUmdvL2nYN0BQ6HRIu7yjVjDlRHFY/edit?usp=sharing) to make a copy of our RoJ integration plan!
{% endhint %}

## Key integration steps for RoJ

Following these 3 steps in sequence will ensure that your integration is secure and runs smoothly for both you and your users.

### 1. Determine the conditions for submission and enforcement

A RoJ integration with Kleros implies that you have chosen to submit all or some of the disputes that may arise on your platform to Kleros Courts.

As with real-world courts, Kleros Court is only a dispute resolution system, and it is important to remember that our decentralized jury only takes care of the ruling on a dispute given certain facts/evidences and policy documents. **Enforcement of the ruling is out of scope for Kleros (in this type of integration), and needs to be carefully taken care of by your service/platform/dApp.**&#x20;

* **Submission criteria**: determining the circumstances under which disputes may be submitted to Kleros court.
  * Example: escalation is only allowed after a first round of dispute resolution has taken place within your platform, and the disputed amount does not exceed a certain value.
* **Enforcement criteria**: what criteria need to be fulfilled for your platform/service to commit to enforcing a ruling from Kleros
  * Example: The partner (exchange, fintech company, etc.) makes a pledge to their customers to abide by the Kleros ruling. \
    And the user retains the right to pursue  traditional legal actions if they are not satisfied with the decision made by Kleros.

### 2. Write a good 'Dispute Policy'

The dispute policy is a document that serves as the primary "law" for jurors, providing them with rules on resolving disputes. It operates similarly to legal statutes or laws in real-world cases, tailored specifically to your integration. Jurors base their decisions on three key sources:

* The dispute policy itself
* The evidence presented by the parties
* The policies of the Kleros courts.

Writing a good dispute policy is essential for ensuring fair and expeditious dispute resolution.&#x20;

{% hint style="info" %}
You can find our Policy Writing Questionnaire in our "[RoJ Integration Plan](https://docs.google.com/document/d/1dn27idjPIfRInrPUmdvL2nYN0BQ6HRIu7yjVjDlRHFY/edit?usp=sharing)" (mentioned above). Based on your feedback, the Kleros team will provide a first draft, subject to an iterative and collaborative process to create the best dispute policy possible.
{% endhint %}

### 3. Communicate all the above to your users

Once all the above are done, it is time to communicate the involvement of Kleros in the dispute resolution processes of your platform. This is essential for the smooth operations of your dispute resolution process and reduces any potential confusion when disputes eventually arise. This includes but is not limited to:

1. Ensuring that the dispute policy is publicly available and pinned using an immutable file storage system (e.g. [IPFS](https://ipfs.io/))
2. Publishing and communicating the **escalation** and **enforcement** criteria.

{% hint style="info" %}
Please reach out to us at marcos@kleros.io once you are done and we will advice you on the right court to use.
{% endhint %}

Once all the above are done, you are ready to go live with Kleros!&#x20;

_For more information about this type of integrations with Kleros, you can visit our_ [_page on Notion: Web 2.0 companies._](https://www.notion.so/kleros/Web-2-0-companies-635bc6949764444dadf6f2ae94d307b9?pvs=4)
