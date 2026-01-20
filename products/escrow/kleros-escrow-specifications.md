# Kleros Escrow Specifications

This page describes the technical flow of the Kleros Escrow smart contracts. It explains how Escrow works behind the scenes for developers and technical users who want to understand the underlying mechanisms.

The Escrow V1 system uses two main contracts:

* **MultipleArbitrableTransaction** (for ETH transactions)
* **MultipleArbitrableTokenTransaction** (for ERC20 token transactions)

Both contracts support the appeal functionality through the Kleros Court system.

![](../../.gitbook/assets/standard-escrow-flow.png)

### **Constructor (deployed by the cooperative)**

The constructor of the contract includes:

* Address of the arbitrator contract
* Extra data for the arbitrator to define court parameters
* Time each party has to pay the dispute fee
* Multiplier for calculating the appeal fee in the situation when there is no winner and loser in the previous round (e.g. when arbitrator gave "0" ruling)
* Multiplier for calculating the appeal fee that must be paid by the winner of the previous round
* Multiplier for calculating the appeal fee that must be paid by the party that lost the previous round

### **Create transaction**

The flow starts when the transaction is created. The creator of the transaction (sender) deposits the amount that will be held in Escrow and specifies:

* **The address that will receive the funds** if the service is successfully provided (receiver)
* **Token** - ETH or ERC-20 token to be used for payment
* **Amount** - The quantity of tokens to be held in escrow
* **Delivery deadline** - The date and time by which the service/product should be delivered
* **Description** - Details of the service to be provided (text field)
* **Agreement PDF** - Optional document detailing the agreement terms

#### Timeline Structure

1. **Service Period**: From creation until the delivery deadline
2. **Buffer Period**: Fixed 7-day period after the delivery deadline
3. **Escrow Expiry:** Occurs exactly 7 days after the delivery deadline

### **Pay / Reimburse**

The sender can use the `pay()` function to transfer the funds locked in Escrow to the receiver as payment for the provided services. Conversely, the receiver can use the `reimburse()` function to unlock some of the Escrow funds and transfer them back to the sender if the services can't be provided fully.

When the escrow expiry date is reached (delivery deadline + 7 days buffer period), the transaction can be executed by anyone calling the contract, which transfers all locked funds to the receiver. This automatic execution only occurs if:

* No dispute has been raised by either party
* Neither party has manually executed the payment or refund

**Note:** All these options are only available if there is no active dispute.

### **Dispute**

If the parties can't reach an agreement, they can create a dispute in Kleros Court. To do so, both parties must pay arbitration fees using the functions:

* `payArbitrationFeeBySender()` (for the sender)
* `payArbitrationFeeByReceiver()` (for the receiver)

When one party fully pays its fees, it waits for the other side to do the same. If both parties pay their fees in time, the dispute is created.

#### Arbitration Cost

The required arbitration cost value can be obtained with:

```
arbitrationCost(_extraData)
```

where `arbitrationCost()` is a function of the arbitrator contract. This function returns the amount in wei and requires the extra data (the same that was used in the constructor) to be passed as an argument.

#### Fee Timeout

If a party doesn't pay arbitration fees in time, it can be timed out using either `timeOutBySender()` or `timeOutByReceiver()`, depending on which party didn't pay. In this case, the party that fully paid the fees wins and gets all the locked funds. Both parties have their arbitration fees fully reimbursed in this scenario.

#### Dispute Outcomes

When the dispute is created, it can be resolved with three possible outcomes:

1. **Sender wins**: Gets all the locked funds and arbitration fees reimbursed
2. **Receiver wins**: Gets all the locked funds and arbitration fees reimbursed
3. **Tie/No clear winner**: The court didn't favor either party. Reimbursed fees and locked funds are split equally between the parties

#### Evidence Submission

Until the dispute is resolved, parties can submit evidence to support their claims. **Note:** In Escrow V1, evidence must be submitted through the [Kleros Dispute Resolver](https://resolve.kleros.io/) interface, not through the Escrow frontend. Parties should navigate to their dispute in the Dispute Resolver to add supporting documentation and arguments.

### **Appeal**

The dispute ruling can be appealed by depositing the appeal fee within the dispute's appeal period. If appeal funding is successful the dispute will be arbitrated again with more jurors.

#### Appeal Fee Calculation

The required appeal fee value is computed by the formula:

```
appealCost(_disputeID, _extraData) × (10000 + multiplier) / 10000
```

Where:

* `appealCost()` is a function of the arbitrator contract that returns the appeal cost
* `_disputeID` is the ID of the dispute given by the arbitrator when the dispute is created
* `_extraData` is the same extra data value used in the Constructor
* `multiplier` is the stake multiplier defined by the outcome of the previous round:
  * **sharedStakeMultiplier**: if the dispute didn't have a winner and loser in the previous round (e.g., when arbitrator gave "0" ruling)
  * **winnerStakeMultiplier**: if the appealing party won the previous round
  * **loserStakeMultiplier**: if the appealing party lost the previous round

These multipliers are set when the contract is deployed.

#### Appeal Process

**Important:** In Escrow V1, only one party needs to pay the full appeal cost to trigger a new arbitration round. For example, if the sender loses the initial ruling, the sender can click the appeal button in the UI during the appeal period, pay the appeal fee, and the dispute will enter a new round of arbitration. The other party does not need to pay for the appeal to proceed.

Each party pays their own appeal fees directly. The appeal process is managed through the Kleros Court system.

If the dispute is not appealed within the appeal period, it receives the final ruling from the arbitrator and the transaction is marked as resolved. The ruling can then be executed and funds are distributed accordingly.
