---
description: >-
  How to challenge a profile, remove your own or someone else's profile and
  resubmit.
---

# Proof Humanity Tutorial \(Remove & Challenge\)

❓ Check out the [FAQ ](https://kleros.gitbook.io/docs/products/proof-of-humanity/poh-faq)or [Part 1 of the PoH Tutorial](https://kleros.gitbook.io/docs/products/proof-of-humanity/proof-of-humanity-tutorial) if you don't find your answer here.

{% tabs %}
{% tab title="5/ Challenge a profile" %}
## 5/ Challenge a profile in "Pending registration" status.

If you want to help to maintain the PoH registry and earn money by spotting fake, bot, and incorrect profiles, you will need to learn how to challenge these types of profiles when they are in "Pending Registration" status.

#### 5.a/ Browse through the "Pending registration" profiles and check them

* Go to the [PoH app](https://app.proofofhumanity.id/) and filter the profiles for "Pending Registration" profiles. The filter is on the right just above the profiles and below the total number of profiles.

![](../../.gitbook/assets/image%20%2834%29.png)

* Once you have applied the filter, click on each profile one by one to check if their information, photo, and video follow the [PoH guidelines](https://ipfs.kleros.io/ipfs/Qmc7ag5XohnSAozvsKsLCUbvaFyasyLtyi3H7g3mmxznPU/proof-of-humanity-registry-policy.pdf) or if you can spot impersonators or deepfake videos.

{% hint style="info" %}
You can use deepfake detection tools such as [https://deepware.ai/](https://deepware.ai/), [https://sensity.ai/](https://sensity.ai/) or other more powerful deepfake detection algorithms to help you in this enterprise. You can also use Voice Recognition Software to spot computer-generated voices or compare old and new submissions.
{% endhint %}

* If you find a malicious/incorrect profile, ensure you have enough funds is your wallet and challenge the profile by clicking on the "Challenge request" button at the bottom left.

![](../../.gitbook/assets/image%20%2844%29.png)

* This will open a modal asking you for a reason to the challenge. Select the relevant reason and click on "Challenge Request".

![](../../.gitbook/assets/image%20%2826%29.png)

* Send the Transaction with the challenger deposit. Once the transaction is validated, the profile will soon go to "Challenged Registration" status.

{% hint style="info" %}
**What is the Challenger Deposit?** The deposit is an amount of ETH you lock with the challenge of the profile that will act as a deterrent to prevent people from challenging profiles for no valid reason. If your challenge of the profile is successful, you get your challenger deposit back and earn the submitter deposit \(minus arbitration fees\). If you have challenged a valid profile, you will lose this deposit.
{% endhint %}

* A dispute will then be raised in [Kleros Court](https://kleros.gitbook.io/docs/products/court) where jurors will vote on a ruling. Anyone can submit evidence from  the profile interface \(at the bottom of the page\)

![](../../.gitbook/assets/image%20%2818%29.png)

![](../../.gitbook/assets/image%20%2838%29.png)

* Now, you just have to monitor the progress of the dispute through the profile interface over the following 5 to 7 days. If you don't agree with the final ruling, you will have the possibility to appeal.
{% endtab %}

{% tab title="6/ Remove a profile" %}
## 6/ Remove a profile from the registry

#### 6.a/ Remove a profile still in "Vouching Phase"

* There is not yet an option on the app to remove a profile in "Vouching Phase" \(It will be added soon\).  For now, you will need to interact directly with the smart contract:

![](https://blog.kleros.io/content/images/2021/03/image-6.png)

* Go to the Etherscan page of the [PoH contract](https://etherscan.io/address/0xC5E9dDebb09Cd64DfaCab4011A0D5cEDaf7c9BDb#writeContract)
* Connect your wallet \(look for the "Connect to Web3" button\). IMPORTANT: It has to be the same wallet you use to register.
* Look for the withdrawSubmission function \(it's the last one\). Click to expand.
* Click "Write". Metamask might suggest a crazy gas limit, but the function should cost only around 50k gas.
* Confirm the Tx and you will get back your deposit and your profile will be transitioned to "Removed".

![](https://blog.kleros.io/content/images/2021/03/image-5.png)

#### 6.b/ Remove a profile in "Registered" status

* In order to remove a registered profile, you need to go to the registered profile page and click on the "Request Removal" button.

![](https://blog.kleros.io/content/images/2021/03/image-7.png)

* You will then be asked to select a reason for removal.
* In your removal request or after you sent it, you can submit evidence to back up your request

{% hint style="success" %}
_**Example 1. Send a removal request from the same address as the submitter.**_

**Evidence Name**: Self-removal of submission.

**Evidence Description**: I am the submitter as proven by my address and I want to remove this submission_**.**_
{% endhint %}

{% hint style="success" %}
_**Example 2: Send a removal request to remove a malicious deepfake submission**_

**Evidence Name**: Removal of deepfake submission.

**Evidence Description**: I have analyzed the video of the submitter and the reproducible report attached in this evidence proves that it is a deepfake.
{% endhint %}

{% hint style="success" %}
_**Example 3: Send a removal request from a different address than the submitter.**_

**Evidence Name**: Self-removal of submission.

**Evidence Description**: I am the submitter and I want to remove this submission. The video attached is a recording of myself saying the sentence “I want to remove my own submission from the Proof of Humanity registry.”
{% endhint %}

#### 6.c/ Remove a profile in "Pending Registration" status

* You will need to challenge the profile as explained in the [previous tab](https://kleros.gitbook.io/docs/products/proof-of-humanity/proof-humanity-tutorial-remove-and-challenge#5-challenge-a-profile-in-pending-registration-status).
{% endtab %}

{% tab title="7/ Resubmit/Reapply a profile" %}
## 7/ Resubmit a profile

#### 7.a/ Resubmit a profile from a new address

* The first step is to ensure that your profile linked to your old address is in "Removed" status \(because we want to avoid submitting duplicates of the same person in the registry which could be challenged\).
* For this go directly to your profile page using _`https://app.proofofhumanity.id/profile/youraddress?network=mainnet` ****_ or click on "My Profile", and check that it is in "Removed" status. If it's not, remove it using these instructions in the previous tab.

 

#### 7.b/ Resubmit a profile from the same address

* The first step is to ensure that your profile linked to your address is in in "Removed" status \(because we want to avoid submittin

#### 7.c/ Reapply a profile expired or soon-to-be expired

🚧👷 IN PROGRESS 👷🚧
{% endtab %}
{% endtabs %}

