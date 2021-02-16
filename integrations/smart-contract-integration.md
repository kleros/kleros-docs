# Smart Contract Integration

**Kleros Court \(Arbitrator\) on Ethereum mainnet:** [https://etherscan.io/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069](https://etherscan.io/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069)  
  
**Kleros Court \(Arbitrator\) on Ethereum Ropsten:** [https://etherscan.io/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069](https://etherscan.io/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069)

![Your app will be on the Arbitrable Side and send disputes to Kleros Court, the Arbitrator.](../.gitbook/assets/image%20%281%29.png)

If you want to integrate with Kleros for dispute resolution, you will have to create an `Arbitrable` smart contract as per the[ Arbitration Standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) that will allow executing the following flow:

![Standard simplified flow between an Arbitrable and Arbitrator smart contract](../.gitbook/assets/image%20%286%29.png)

In the `Arbitrable` contract, you will have to define at least:

* the address of the `Arbitrator` contract \(look at the top of this page for the addresses of Kleros Court Arbitrators.
* Some extra data to set up the arbitration \(that will specify the sub-court to be used and the number of voters required\)

  * Script to generate the arbitrator extra data

  `generateArbitratorExtraData = (subcourtID, noOfVotes) => 0x${parseInt(subcourtID, 10).toString(16).padStart(64, "0") + parseInt(noOfVotes, 10).toString(16).padStart(64, "0")};`

* \(If appeals are allowed\) Stake multipliers representing multipliers of the appeal cost that a party must pay for a new round \(in basis points\)

For more details, please consult the [Arbitration Standard](https://kleros.gitbook.io/docs/developer/erc-792-arbitration-standard) documentation, have a look at the examples of implementations shared [here](https://github.com/kleros/kleros-interaction/tree/master/contracts/standard/arbitration) or contact us on Discord, Telegram, Slack, contact@kleros.io \(links on the bottom left\).

