---
description: Frequently Asked Questions about Proof of Humanity
---

# Proof of Humanity FAQ

## What is the purpose of Proof of Humanity?

[Proof of Humanity](https://www.proofofhumanity.id/) is a system combining social verification with video submission in order to create a Sybil-proof list of humans. It is meant to be used by individuals as a point-of-entry to a myriad of new use cases that require Sybil-resistance to be able to be deployed at scale and also to be plugged into a variety of existing and new applications in need for such identity systems.

## Why should I register to PoH? What are its use cases?

Check out the numerous use cases of proof of humanity in this [post](https://blog.kleros.io/proof-of-humanity-a-building-block-for-the-internet-of-the-future/).

## What's the connection between Proof of Humanity and the UBI Token?

Proof of Humanity is a dapp created with the purpose of creating a Sybil-resistant list of humans. The UBI Token is a universal income currency which is accrued by all profiles successfully registered in the Proof of Humanity registry. To learn more about the UBI Token, check the [UBI announcement post](https://blog.kleros.io/introducing-ubi-universal-basic-income-for-humans/).

## How do I use the Proof of Humanity registry?

Check out the [full explainer article](https://blog.kleros.io/proof-of-humanity-an-explainer/) to learn how to interact with Proof of Humanity.

## Can I, as a single individual, have more than one identity submitted to Proof of Humanity?

No, you can’t.

## Which Ethereum address should I use to register in Proof of Humanity?

The Ethereum address you are using to submit your profile will be publicly linked to your identity. If you don't want your wallet holdings and transaction history to be linked to your identity, we recommend using a new Ethereum address seeded with funds from a crypto exchange or coming from Tornado.cash .

## Which phases will my profile go through before being registered?

Once you have submitted your profile, it will be in the “Vouching Phase” until you get vouched for and your deposit gets fully funded. Initially, you will only need 1 person to vouch for you (it enables faster onboarding in the registry at launch) but the number of vouches needed can be increased later on.

Then, your profile will move to the “Pending Registration” phase, during which anyone can challenge it for a period of 3.5 days if they think you are not human or if it violates the [submission guidelines](https://ipfs.kleros.io/ipfs/QmXDiiBAizCPoLqHvcfTzuMT7uvFEe1j3s4TgoWWd4k5np/proof-of-humanity-registry-policy-v1.3.pdf).

If your profile isn’t challenged during this period or the challenges are not successful, you are “Registered”.

If you are challenged, you will either go back to “Pending Registration” phase or be “Removed” depending on the ruling of Kleros Court.

Once you are “Registered”, your profile can either expire after a year (if you don’t reapply) or someone can make a request for removal which will move it to the “Pending removal” phase during which anyone can challenge the removal.

If your profile is “Expired”, “Removed” or about to expire soon, you can reapply for submission which will bring you back to the “Vouching Phase”

![Simplified phase transitions of a profile in PoH (without appeals).](https://lh6.googleusercontent.com/b\_2pVuJKBR1w-SxU95uvjJ27NVynA3jWtO4lF2DGYlLYNT39-xez\_YNySzUMTYkzgvHke4S6M-1IJbWXWNuGm1WAIxlNOuqudpzrBsOngx59AfSot93wAAvddJ8CQtPC0ViSycpg)

You can learn more about how the challenge and the dispute resolution system work in Kleros Court [documentation](https://kleros.gitbook.io/docs/products/court).

## Why should I vouch for someone? What's in it for me?

Vouching for someone is a benevolent act in order to help people you know be accepted into the registry. Be careful with whom you vouch for. If by mistake (or excess of trust) you vouch for a malicious user, you will be penalized.

## What happens if I vouch for a malicious user?

If a submission is rejected for "Duplicate" or "Does not exist" reasons, all people who had vouched for the rejected profile get removed from the registry. This allows to weed out malicious attackers who vouch for bots. It also means you have to be careful when vouching: make sure you know this person in real life and that it is not a duplicate.

## How many people can I vouch for?

You can vouch for as many people as you would like. However your vouch will only count for one person at a time in the order they were given. A user vouching can only be used for one submission at a time on a “first come, first served” basis.

For example, assume user A is registered. A vouches for user B. User B uses the vouch and moves to "Pending registration" phase. Then A vouches for user C. Since the vouching of A is already in use by B, C remains in the "Vouching Phase" for now, but will move to "Pending registration" phase once B is registered.

## Can I remove a vouch?

You can remove your vouch at any time prior to the "Pending Registration" phase by going to the vouched person's profile and clicking on "Remove Vouch".

## When does my deposit get refunded?

Your deposit will be refunded shortly after you move to "Registered" status. You can confirm the status of the refund transaction on [Etherscan](https://etherscan.io) by typing in your address and then clicking the "Internal Txns" tab.

_Note: As this is an internal transaction, unlike the deposit transaction, you will not see the refund transaction in your Metamask "Activity" tab._

## How long does the registration last?

Registrations have a duration of two years. This means that users need to periodically reapply to the registry. The purpose of the limited registration period is to remove people who die and malicious submissions which might have made it into the list. Conditions to reapply are similar to the original application.

You can reapply before the current registration period ends in order to avoid spending some time unregistered. Users reapplying (such that they have the required vouching and deposit) before their registration ends are considered registered for the entire period of their new application.

## What rules should I follow to submit a proper profile or to remove an incorrect one?

Check the [Proof of Humanity policy](https://ipfs.kleros.io/ipfs/QmcT8TUxLEHistCnkmGERcEuVtMfMPhXcMDTxfBTYahqEh/proof-of-humanity-registry-policy-v1.2.pdf) to obtain all the detailed conditions for a profile to be accepted or rejected from the registry.

## Can I request to remove someone else profile from the registry?

A request to remove a registered submission from the list can be made at any time by submitting a deposit. Anyone can put a deposit claiming the registration to be correct. If no one does, the individual is removed from the list. If someone does, a dispute is created. Note that in case of a successful removal request, people vouching for the user are not removed from the list.

## I want to remove my profile and submit it again but because I want to change something about it. How do I proceed?

### **IF YOUR PROFILE IS STILL IN "VOUCHING PHASE"**

There is not yet an option on the app to remove a profile in "Vouching Phase" (It will be added soon).

For now, you will need to interact directly with the smart contract:

![](https://blog.kleros.io/content/images/2021/03/image-6.png)

1. Go to the Etherscan page of the [PoH contract](https://etherscan.io/address/0xC5E9dDebb09Cd64DfaCab4011A0D5cEDaf7c9BDb#writeContract)
2. Connect your wallet (look for the "Connect to Web3" button). IMPORTANT: It has to be the same wallet you use to register.
3. Look for the withdrawSubmission function (it's the last one). Click to expand.
4. Click "Write". Metamask might suggest a crazy gas limit, but the function should cost only around 50k gas.
5. Confirm the Tx and you will get back your deposit and your profile will be transitioned to "Removed".

![](https://blog.kleros.io/content/images/2021/03/image-5.png)

**IF YOUR PROFILE IS ALREADY "REGISTERED"**\
First, you need to remove your own outdated profile and then either reapply or submit with another address for a new registration. In order to remove your old registered profile, you need to go to your registered profile page and click on the "Request Removal" button and then provide evidence that you are indeed the submitter.

![](https://blog.kleros.io/content/images/2021/03/image-7.png)

_**Example 1. Send a removal request from the same address as the submitter.**_

**Evidence Name**: Self-removal of submission.

**Evidence Description**: I am the submitter as proven by my address and I want to remove this submission.

_**Example 2: Send a removal request from a different address than the submitter.**_

**Evidence Name**: Self-removal of submission.

**Evidence Description**: I am the submitter and I want to remove this submission. The video attached is a recording of myself saying the sentence “I want to remove my own submission from the Proof of Humanity registry.”

## Why did the registry start with some users already registered in it?

Since we require user vouching for new members, we had to start with an initial set of trusted and manually curated users. Those registered through the seeding event will still have to periodically confirm their registration like any other user.

## Why can’t I display my ENS in my submission video?

In order to reduce the attack surface at launch, we decided against allowing to display or use ENS. A user could lose control of its ENS, forget to renew it, or be outbid. We opted to link the ownership of the profile to the simple straightforward ownership of the Ethereum address having submitted it. This could change in the future through Kleros Governance.

## Why is the Proof of Humanity app deployed on Ethereum mainnet where gas fees are high?

The Proof of Humanity registry is deployed on Ethereum mainnet because it is where its anti-Sybil attacks properties are the most useful and will allow more dapps to use it. It also relies on several other contracts such as Kleros Court that are not yet deployed on Layer 2 solutions.

The PoH contract has been gas-optimized as much as possible to reduce gas fees when interacting with it. We are aware that gas fees on mainnet are high but we think the steady UBI distribution will compensate those fees paid by the token holders to enter the registry

The contracts are ready for gasless vouching and the UI for it will be implemented soon. In the future, the Kleros DAO will have the power to decide if migrating the PoH registry to a Layer 2 solution is viable.

## As deepfakes get better, will challengers be able to keep up technologically to defend against this?

Improvements in machine learning are likely to affect the effectiveness of both deepfake creation and deepfake detection algorithms. If algorithms manage to produce deepfakes not detectable by other algorithms, other evidence would need to be required. This can be decided through Kleros governance process.

## What if my religion forbids me from showing my face? What if I am physically unable to speak?

Internal features of the face are the most important for face recognition (see [this article](https://twin.sci-hub.tw/6930/15eaafba29e330ca74f92b4ef05e57c9/toseeb2014.pdf)) and removing the requirement to pronounce the sentence would decrease the security of the system (speech analysis can be used to detect multiple registrations). For the moment, these edge cases do not allow the person to be registered. If you have a proposal that would enable the secure registration of this edge case (and others), you can submit it through the governance process.

## What if I have an identical twin that also wants to be registered?

While most people have a hard time distinguishing twins, identical twins aren't actually identical and can be distinguished by skilled individuals. Moreover, facial recognition algorithms tend to do a better job than humans distinguishing between twins. This means a twin submission could be challenged but the twin could probably easily provide evidence that he is a twin to win the dispute.
