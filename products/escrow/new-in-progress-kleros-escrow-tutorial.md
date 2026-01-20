# Kleros Escrow Tutorial

**Kleros Escrow** is a secure and decentralized escrow Dapp that can be used for any exchange of goods, assets, or services involving an Ethereum-based asset.

Using Kleros Escrow, you can transact in the blockchain ecosystem for services, products, and assets with a simple solution that provides a level of trust not yet known outside the traditional commerce space. If a dispute happens, it will be adjudicated by crowdsourced jurors selected and incentivized by the Kleros protocol.

<figure><img src="../../.gitbook/assets/Escrow v1 flow.png" alt=""><figcaption></figcaption></figure>

## TUTORIAL

(One tab for each step)

{% tabs %}
{% tab title="1/ Initiating a Payment" %}
To start an Escrow transaction, you will need to connect your wallet and initiate a new payment.

### 1/ Initiating a Payment

#### 1.a. Go to the Kleros Escrow Website

Visit [Kleros Escrow V1](https://escrow-v1.kleros.builders/)

You will need to connect your Rabby, Metamask wallet or WalletConnect to use the Escrow service.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-17 at 2.55.30 PM.png" alt="" width="375"><figcaption></figcaption></figure>

Once you have connected your wallet to the app (the wallet will ask you to confirm the connection), you will need to ensure you have some Ether (ETH) loaded in the wallet to:

* Interact with the Ethereum blockchain (pays transaction fees)
* Pay for the Escrow transaction you'll be setting up

You should now be able to see the homepage.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.20.07 PM.png" alt=""><figcaption></figcaption></figure>

The homepage allows you to:

* Create new escrowed transactions
* Search existing transactions by title or address
* Review existing transactions&#x20;

{% hint style="info" %}
**INFO**\
**If you already had some escrowed transactions in progress, they will be displayed on the homepage.**
{% endhint %}

#### 1.b. Create a new Payment



* To start configuring an escrowed payment, click on the **"Create Transcation"** button on the top right.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-17 at 3.01.51 PM.png" alt="" width="287"><figcaption></figcaption></figure>

**IMPORTANT:** When you create a transaction, you will be the person who deposits funds into the escrow smart contract. The funds will be held securely until:

* You manually release them to the receiver
* The receiver manually refunds them to you
* A dispute is raised and resolved by Kleros Court
* The expiry date passes and either party can execute the transaction&#x20;

The receiver will be able to view and interact with the transaction using their wallet address once you've created it.

#### 1.c. Select an Escrow Type

* On creating a new transcation you'll get an option to select the type of Escrow transaction you want to create. Select one and click on "Next".

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-17 at 3.02.57 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**TYPES OF ESCROW TRANSACTIONS**

**Cryptocurrency Transaction**

* Select this option if you want to trade or exchange a crypto asset for another crypto asset
* Especially useful where one of the assets is on a blockchain other than Ethereum
* Example: Trading ETH on Ethereum for SOL tokens on Solana

**General Service Transaction**

* Select this when paying for any other type of general service
* Allows you to specify your own terms for the agreement
* Allows you to upload a document when creating the payment&#x20;
{% endhint %}
{% endtab %}

{% tab title="2/ Submitting Payment" %}
In this step, you will specify the details of the Escrow transaction to be made between parties and lock the funds in the Escrow.

### 2/ Submitting a Payment

#### 2.a. **Transaction Details**

When creating a payment, you'll be asked to fill out a form providing basic information about the payment:

**Required Information:**

* **Title for the transaction**
  * Examples: "Marketing Mission with John D.", "ETH to SOL trade", "Physical NFT delivery"
* **Ethereum address for the funds receiver**
  * The wallet address that will receive the funds when the transaction completes
* **Amount and unit** of ETH or ERC-20 tokens to be paid

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-17 at 3.25.03 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Note:** The transaction details form is the same for both General Service and Cryptocurrecny Transaction types. The only difference between the two transaction types is which Kleros Court will handle disputes if they raise. Cryptocurrency Transaction cases will be handled by Kleros Blockchain Non Technical Court whereas those under General Service will be handled by Kleros General Court.&#x20;
{% endhint %}

**Selecting ERC-20 Tokens:**

If you wish to pay with an ERC-20 token, click on the asset dropdown to select another asset. The tokens displayed are those who received the "ERC-20 badge" in the Kleros Token List.

If you don't find the token you want to use in this list, click on **"Add Custom Token"** and add the information of the ERC-20 token (available from the Etherscan token contract page).

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-17 at 3.26.18 PM.png" alt="" width="375"><figcaption></figcaption></figure>

#### 2.b. Setting the Delivery Deadline (Terms Step)

In the Terms step, you will set the timeline for your escrow:

**Description:** Enter a detailed description of the service or product to be delivered. This description is important as it will be used by jurors if a dispute arises.

**Delivery Deadline (Local time):** Select the date and time by which the receiver should deliver the service or product. This is the only timeline you need to set.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.24.29 PM.png" alt=""><figcaption></figcaption></figure>

**Understanding How the Timeline Works:**

All Kleros Escrow V1 transactions follow an automatic timeline:

1. **Service Period**: From creation until the delivery deadline
   * The receiver should complete and deliver the service/product during this time
   * Either party can manually release/refund or raise a dispute at any time
2. **Buffer Period**: Automatically set to 7 days after the delivery deadline
   * Additional time window where either party can review and raise a dispute
   * Provides a grace period before automatic execution
3. **Escrow Expiry**: Automatically occurs 7 days after the delivery deadline
   * After this date, either party can execute the transaction (releasing funds to receiver)

**IMPORTANT:**

* The buffer period is **fixed at 7 days** and cannot be changed
* The escrow expiry date is automatically calculated as: Delivery Deadline + 7 days
* You will see both dates displayed after creating the transaction

**Example Timeline:**

* Transaction created: December 17, 2025
* Delivery deadline set to: January 16, 2026
* Escrow expiry (automatic): January 23, 2026

This means:

* Receiver should deliver by January 16
* You have until January 23 to review and raise any disputes
* After January, either party can execute the transaction to release funds to receiver

#### 2.c. Agreement Document

**Upload an Agreement PDF (optional):**

You can upload a PDF document detailing the specifics of the agreement between the parties. Alternatively, you can include all terms in the Description field.

**IMPORTANT:** The Description and/or Agreement PDF is crucial and will be relied upon by jurors in the event of a dispute.

Try to clearly specify:

* The parties involved
* The nature of the service/good expected
* Specific deliverables or milestones
* Acceptance criteria
* Any conditions of the engagement

#### 2.d. Submit Transaction

Once all the details are filled in:

1. Review all information in the Preview step
2. Verify all information is correct, especially:
   * Receiver address (double-check this!)
   * Amount
   * Delivery deadline
3. Click on the **"Create Escrow"** button

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.39.21 PM.png" alt=""><figcaption></figcaption></figure>



You will need to confirm a blockchain transaction to:

* Deposit the payment amount into escrow
* Pay gas fees for the blockchain transaction

The payment will remain in the escrow contract until:

* The sender manually releases payment by clicking "Make a payment"
* The receiver manually refunds by clicking their refund option
* A dispute is raised and resolved
* The escrow expiry date passes and either party executes the transaction

Once the payment is submitted and the transaction is mined, you will be redirected to the payment page.
{% endtab %}

{% tab title="3/ Executing Payment" %}
After the service has been provided or trade has been made successfully, this is how you can finalize the transaction.&#x20;

Now, if you click on the escrow contract you just created, you will see a summary of the payment details.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-17 at 3.54.58 PM (1).png" alt=""><figcaption></figcaption></figure>

### 3/ Executing Payment

#### 3.a. Payment Sender

If you are the sender of the payment you'll see the following options when viewing the transaction

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.46.37 PM.png" alt=""><figcaption></figcaption></figure>

**Make Payment**:&#x20;

* Click this button to release funds to the receiver
* You can choose to pay the **full amount** or a **partial amount**
* Paying a partial amount is useful for settlement scenarios (see Step 4 for more details)
* Interface shows:
  * "Current amount in escrow: \[amount] ETH"
  * "If you are happy with the service or good provided, you can pay the total amount and complete the escrow. Otherwise, you can make a partial payment. The amount that remains can still be disputed."
  * Input field: "Amount to pay" (you can enter any amount up to the full escrow balance)
  * Button: "Send"

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.46.46 PM.png" alt=""><figcaption></figcaption></figure>

**When to pay full amount:**

* Service/product was delivered exactly as agreed
* You're completely satisfied with the outcome
* Click "Send" with the full amount → Transaction closes, receiver gets all funds

**When to pay partial amount (Settlement):**

* Work was partially completed
* Quality issues but some payment is deserved
* You want to settle the disagreement without going to dispute
* Enter the agreed partial amount → That amount goes to receiver, remainder stays in escrow (can still be disputed if receiver disagrees)



**Raise Dispute**:&#x20;

* Click this button if you're not satisfied with the service/product delivery
* You'll be shown the arbitration cost (e.g., 0.03 ETH)
* You must deposit the arbitration fee to initiate the dispute
* Interface shows:
  * "Arbitration cost: \[amount] ETH"
  * "By raising a dispute you are petitioning for the full remaining balance."
  * "You will need to deposit the arbitration cost. This is refunded if you win the dispute."
  * "The dispute will be evaluated by the Kleros jurors."

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.46.55 PM.png" alt=""><figcaption></figcaption></figure>

#### 3.b. Payment Receiver

If you are the receiver of the payment you'll also have two options when viewing the same transaction:

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.49.14 PM.png" alt=""><figcaption></figcaption></figure>

**Reimburse**:&#x20;

* Click this button to return funds to the sender
* You can choose to reimburse the **full amount** or a **partial amount**
* Partial reimbursement is useful for settlement scenarios (see Step 4 for more details)
* Interface shows:
  * "Current amount in escrow: \[amount] ETH"
  * "You can fully or partially reimburse the other party. The amount that remains can still be disputed."
  * Input field: "Amount to reimburse" (you can enter any amount up to the full escrow balance)
  * Button: "Send"

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.49.23 PM.png" alt=""><figcaption></figcaption></figure>

**When to reimburse full amount:**

* You're unable to complete the service/product delivery
* You want to cancel the agreement entirely
* Click "Send" with the full amount → Transaction closes, sender gets all funds back

**When to reimburse partial amount (Settlement):**

* You completed some but not all of the work
* You want to keep partial payment for work done
* You want to settle the disagreement without going to dispute
* Enter the amount to refund → That amount goes back to sender, remainder goes to you, transaction closes

**Raise Dispute:**&#x20;

* Click this button if the sender refuses to release payment despite you fulfilling the agreed terms
* You'll be shown the same arbitration cost (e.g., 0.03 ETH)
* You must deposit the arbitration fee to initiate the dispute
* The dispute process is identical for both sender and receiver (same interface, same cost, same process)

#### 3.c. Understanding Settlements Through Partial Payments

Settlement in Kleros Escrow is achieved through the partial payment mechanism described above. There is no separate "settlement mode" - you simply use the partial payment option when both parties agree to a compromise.

**How Settlement Works:**

**Scenario 1: Sender Initiates Settlement**

1. Sender decides to pay partial amount (e.g., 0.7 ETH out of 1 ETH escrow)
2. Sender clicks "Make a payment", enters 0.7 ETH, clicks "Send"
3. **Result:** 0.7 ETH immediately goes to receiver, 0.3 ETH remains in escrow
4. **Receiver's options:**
   * Accept the settlement (do nothing, keep the 0.7 ETH)
   * Reject and dispute the remaining 0.3 ETH
   * Reimburse some or all of the remaining 0.3 ETH

**Scenario 2: Receiver Initiates Settlement**

1. Receiver decides to refund partial amount (e.g., 0.4 ETH out of 1 ETH escrow)
2. Receiver clicks "Reimburse", enters 0.4 ETH, clicks "Send"
3. **Result:** 0.4 ETH immediately goes back to sender, 0.6 ETH remains in escrow&#x20;

**CRITICAL WARNING:** When you make a partial payment or partial reimbursement, **that amount transfers immediately and permanently**. The transferred amount cannot be recovered even if a dispute is later raised over the remaining balance. The dispute will only concern the funds that remain in escrow.

**Best Practice for Settlements:**

* Document any settlement agreement in writing (email, chat, signed PDF)
* Get the other party to confirm they agree to the settlement terms
* Save this communication as evidence in case they dispute the remaining amount
* If you have written proof they agreed to the settlement, you can use it to win any subsequent dispute

{% hint style="info" %}
**Note:** Both sender and receiver use the same interface at [https://escrow-v1.kleros.builders/](https://escrow-v1.kleros.builders/) - the available buttons change based on which wallet address you're using to view the transaction.
{% endhint %}
{% endtab %}

{% tab title="4/ Raise a dispute" %}
Whether a partial settlement has been made or not, any of the 2 parties can raise a dispute for the full or remaining payment amount by paying the arbitration fee (that is reimbursed if you win the case). Both parties must pay the arbitration fee. This fee is used to pay coherent jurors in any dispute.

### 4/ Raise a dispute

#### 4.a. Raise the Dispute

To raise a dispute either party can select the **Raise Dispute** button to pay for the arbitration fees and start the process for arbitration by the Kleros court.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-21 at 11.46.55 PM.png" alt=""><figcaption></figcaption></figure>

Once a dispute is raised by any party the other party has a limited period of time to pay their side of the arbitration fees after which the Kleros arbitration process starts and can take at least 5-7 days depending on the Kleros court parameters.

The UI will update once you have paid the arbitration fee to show the time left for the other party to pay.

Below we can see the notifications of payment each party will see.



<figure><img src="../../.gitbook/assets/Screenshot 2025-12-22 at 12.12.50 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-22 at 12.14.00 AM.png" alt=""><figcaption></figcaption></figure>

Once both the parties submit the arbitration fees, they can view the details of the case <br>

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-22 at 12.38.19 AM (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**INFO**

If the other party fails to pay for their side of the fees then the first paying party automatically wins the dispute and can withdraw their funds.
{% endhint %}

#### 4.b. Share Evidence

Once a dispute has been created and both parties have paid their arbitration fees, both parties can submit evidence to support their case.

**IMPORTANT:** In Escrow V1, evidence must be submitted through the [Kleros Dispute Resolver](https://resolve.kleros.io/) interface, not through the Escrow frontend.

**How to Submit Evidence:**

1. Go to [https://resolve.kleros.io/](https://resolve.kleros.io/)
2. Connect your wallet
3. Find your dispute in the interface
4. Click on your dispute to open the evidence submission page
5. Add your evidence and supporting arguments

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-22 at 12.44.01 AM.png" alt=""><figcaption></figcaption></figure>

**Evidence Best Practices:**

* The original Agreement Document details the initial contract
* You can add additional evidence such as:
  * Communication logs with the other party
  * Proof of delivery or work completed
  * Photos or screenshots
  * Any other relevant documentation
* **Best practice**: Use PDF files with EXIF data stripped to preserve anonymity
* Be clear and concise in explaining why you should win the dispute
* Reference specific terms from the original agreement

#### 4.c. Monitor the dispute

You can monitor the progress of the dispute in two places:

1. **On the escrow payment page** - Shows the current status
2. **On** [**https://resolve.kleros.io/**](https://resolve.kleros.io/) - Shows detailed case information and voting status

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-22 at 12.41.09 AM.png" alt=""><figcaption></figcaption></figure>

**First Ruling:**

Once a first ruling has been made by the Kleros Court, anyone who is not satisfied by the ruling can choose to appeal the court ruling:

* Appeals request another round of ruling with more jurors than before
* Additional evidence can be provided for the jurors to consider
* Appeal fees must be paid within the appeal period

**Final Ruling:**

When the final ruling is made (either after no appeals or after all appeal rounds are complete):

* The winning party can withdraw their funds from the escrow
* The winning party also receives their arbitration fees back

[Learn more about the dispute process.](https://kleros.gitbook.io/docs/products/court)
{% endtab %}
{% endtabs %}
