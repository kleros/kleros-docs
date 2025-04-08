---
description: Decentralise DAO governance control securely
---

# Governor

Kleros Governor is a smart contract that allows for the effecting of DAO governance decisions to be decentralized without compromising security. By designating Kleros Governor as the governor contract for your DAO, batches of transactions representing governance decisions can be submitted as lists to Kleros Governor. In case of disputes about the validity of the submitted transactions, Kleros's jury network will step in to arbitrate the dispute.

## How does it work?

The first step to using Kleros Governor is to point to it as the governor contract for your DAO. Each Governor session enforces governance decisions that were passed prior to the start of the current session, which can be organised on a platform like [Snapshot](https://snapshot.org/).

Once a decision has been reached, a (technically inclined) user then needs to translate the decision into a list of transactions and submit them for execution by the governor contract. If there is only one list submitted in the challenge period, it will be accepted and the deposit is returned to the submitter.

If a competing list is submitted in the same session, a dispute will be automatically created in Kleros Court, and jurors will get to choose which list is correct. After dispute resolution concludes, the deposit from the losing list will be used to pay the jurors and reward the user that submitted the winning list.

Lists that most completely enforce the greatest number of governance decisions will be accepted. The process for choosing between lists can be seen [here](https://cdn.kleros.link/ipfs/QmPt2oTHCYZYUShuLxiK4QWH6sXPHjvgXTqMDpCShKogQY/KlerosGovernorPrimaryDocument.pdf). 

🏛 [Kleros Governor App](https://governor.kleros.io/) 🏛
