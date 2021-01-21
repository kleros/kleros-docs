---
description: How to use the Kleros Escrow
---

# Kleros Escrow Tutorial

## The Walkthrough

Upon entering [escrow.kleros.io](https://escrow.kleros.io) you will be greeted with the screen below. The home offers you the chance to create new transactions and review those that are open, in progress, pending dispute or closed.

![](https://blog.kleros.io/content/images/2019/04/Escrow_Home.jpg)

This dashboard will populate with escrow contracts over time. At the moment it's empty. Let's go ahead and create a transaction.

Before we get started, remember to sign up for email notifications to not miss any important deadlines.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-29-at-12.40.39.png)

Click 'New Payment' to start building your first escrow.

![](https://blog.kleros.io/content/images/2019/04/NewPaymentUpdated-1.jpg)

Here, we can select the escrow type. For now, let's take 'General.'

Title your escrow accordingly and add the ETH address of the receiver \(the party with whom the contract will be made.\)

Upon clicking the 'Timeout Date and Time' section, a calendar will appear allowing you to select the deadline for the escrow contract. This is an important setting in which the contract execution date will be determined. If no disputes are raised before this deadline, the transaction will be automatically processed.

Before this timeout has passed, the receiver should have sent the product or service to the sender or the contract should be in dispute status.

> **Once the contract timeout has passed, the receiver can manually call the contract which will in turn, release the funds.**

![](https://blog.kleros.io/content/images/2019/04/Screen-Shot-2019-04-19-at-1.10.24-AM.png)

### The Contract

In the Contract Description section, you'll be presented with a template which you can tailor to your escrow needs.

Let's go over the simple 'Cryptocurrency' contract template to better understand what's going on here as the contract is also fundamental to any disputes. The more accurate the data there, the better.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-29-at-20.22.42.png)

**\[Address\]** in **\[Blockchain\]** should receive **\[Cryptoasset Description\]** from the receiver before **\[Due Date\]** \(Note this is before and not the same as the payment's timeout.\).

In the example above using BTC &gt; ETH transfer, this contract could look something like this:

[**1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa**](https://blockchain.info/address/1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa) in **Bitcoin** should receive **0.1 BTC** from the receiver before **Sun Apr 28 2019 23:31 UTC**.

As you can see, we've filled in the info between the square brackets with the necessary wallet addresses, time and crypto asset for transfer.

Double check the contract and that all addresses are correct and click 'Save Transaction' to move to the next screen.

You will then be presented with an overview of the transaction:

![](https://blog.kleros.io/content/images/2019/04/payments.jpg)

Click 'Submit Payment' to confirm. This will bring up a Metamask dialogue in which you will deposit the 0.2 ETH we made in this escrow.

It will remain in the escrow contract until the transfer of cryptoasset is completed or the timeout date of the contract \(as shown in the calendar above\) passes.

Now the 0.2 ETH is held in the escrow contract awaiting payment from the sender. In this example, we assume all has gone well and you've received the cryptoasset within the predefined deadline.

Whilst you wait, all your escrow contracts are held in the My Payments dashboard showing their current status.

![](https://blog.kleros.io/content/images/2019/04/MyPayments.png)

Now, if you click on the escrow contract you just created, you will see a yes/no option. Important to note here is the 'Payment time out' section.

![](https://blog.kleros.io/content/images/2019/04/pay.jpg)![](https://blog.kleros.io/content/images/2019/04/Timeout.png)

If the other party has not complied with the contract \(in this case not sending the BTC\) and you don't select 'No' to the compliance question, **they will be able to execute the payment manually.** 

By clicking 'No' you can then resolve the dispute with a part payment or, take it to Kleros jurors. We'll look at that in the next part of this explainer, but for now, let's click 'Yes' and release the funds to the other party.

![](https://blog.kleros.io/content/images/2019/04/MetaMaskPayment.jpg)

Release the funds by click ' Yes' and paying the gas fee. This will release the ETH from the escrow to the other party.

In the final screen you'll see a confirmation that the payment was made successfully.

![](https://blog.kleros.io/content/images/2019/04/Payment_completed.jpg)![](https://blog.kleros.io/content/images/2019/04/escrowmeme.jpg)

## What Happens if There's a Dispute?

![](https://blog.kleros.io/content/images/2019/04/Kleros_juror.jpg)

In our first example, the transaction went as expected and all ran smoothly. In the case of dispute, there are a number of options to consider.

First up, you can offer to make a settlement before any Kleros jurors are brought in. This can be in the form of a part payment settled 'out of court' as it were.

If that option isn't enough and you want full on justice, you can take it to Kleros' Court where both parties will have to pay an arbitration fee \(winning party is refunded\) in order for the case to go to court. If one side fails to pay the arbitration fee in time, the other party automatically wins.

Let's see these options in action in the escrow case below.

### Cryptoasset Transfer Never Happened

In this case, we have a very similar setup to the former. However, the sender did not send the funds leaving the receiver \(of the XMR\) currently out of pocket. Their ETH is in our escrow contract and in order to get it back, they will raise a dispute by clicking 'No' to the compliance question below.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-28-at-23.25.39.png)

### Part Payment

Upon clicking 'No' there are two paths to take. The first is pretty self explanatory allowing you to make a part payment to the other party. Maybe you contracted for some freelancing work that was _sort_ of completed correctly with the contractor deserving of some recompense.

You can use the slider to select an appropriate amount and click 'Pay'. If the other party agrees, the payment is made and the escrow contract is closed. If not, the case can still go to dispute should either party not agree to the part payment.

**Note:** If you get the other party to digitally sign saying they agree to a settlement, and then they raise a dispute on the remaining amount after a waive, you can use your communications as evidence to win that dispute.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-28-at-23.26.18.png)

### Prepare for Court

The other option here would be to raise a full dispute which is sent to Kleros jurors to arbitrate on.

To do that both parties must pay the arbitration fee. This fee is used to pay coherent jurors in any dispute. If one side pays the arbitration fee and the other does not within the allotted time period, the non-paying side will automatically lose the dispute.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-28-at-23.26.53.png)

By clicking into 'My Payment's dashboard you will see the updated card showing that the other party has to pay. Once they do, the case will be sent to Kleros Court for arbitration.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-28-at-23.28.20.png)

Both parties have agreed to raise a dispute and can now attach evidence detailing their claim.

Below we can see the counter party's notification of payment.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-28-at-23.28.39.png)

The UI will update once you have paid the arbitration fee to show the time left for the other party to pay.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-28-at-23.27.55.png)

### Evidence

By opening the disputed card, you are now able to add evidence to the case. The original agreement document details the initial contract and you can add your own evidence as shown below. Best practice would be a PDF file with [EXIF data](https://www.pdfyeah.com/remove-pdf-metadata/) stripped to preserve anonymity.

![](https://blog.kleros.io/content/images/2019/04/submit_evidence.gif)![](https://blog.kleros.io/content/images/2019/04/EvidenceProof.jpg)

### Kleros Court

We'll take a brief look at this case from a jurors perspective. Below, we can see a juror has been selected to arbitrate this dispute.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-28-at-23.45.11.png)

The case will be presented with attached evidence files, primary document \(original agreement\)

![](https://blog.kleros.io/content/images/2019/04/Court_1_Waiting-For-Evidence.gif)

Once the evidence period is over, jurors can review all attached evidence and cast their vote y selecting 'Refund Sender' or 'Pay Receiver' and paying the gas fee.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-28-at-23.43.46.png)

The case will be updated as shown below with the winning choice and the winning party will receive their funds.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-29-at-02.45.02.png)

The My Payments dashboard will be updated with all the status' of the escrows as shown below.

![](https://blog.kleros.io/content/images/2019/04/Screenshot-2019-04-29-at-12.40.24.png)

### And That's It...

We've gone through a working escrow and a disputed case. Try it out today and become a Kleros Juror using the link bel



