---
description: An evidence standard for arbitration
---

# ERC 1497: Evidence Standard

### Abstract

The following describes the standards for `MetaEvidence` and `Evidence` for dispute resolution. `Evidence` is provided by a participant in a dispute in order to support their assertion. `MetaEvidence` gives context to the dispute so that arbitrators are able to accurately and fairly evaluate it. This standard follows [ERC 792](https://github.com/ethereum/EIPs/issues/792) and references `Arbitrator` and `Arbitrable` contracts.

### Motivation

Standardizing `MetaEvidence` and `Evidence` allows interoperability between `Arbitrable` DApps \(DApps where disputes can arise\) and `Arbitrator` DApps \(DApps which can be used to resolve disputes\). It allows these applications to easily switch from one arbitration service to another, or to let their users decide which arbitration service to use without having to spend time to integrate with all of them. `MetaEvidence` is required to provide the context of the dispute. `Evidence` allows for dispute participants to submit extra information for the arbitrators.

The ERC792 standardizes the way the smart contracts interact with each other while this standard is made to standardize the way the interfaces interact in the context of disputes.

![](../.gitbook/assets/image%20%282%29.png)

In the linked documentation, you will be guided through the implementation of an ERC-1487-compatible smart contract.

📖 [Link to full ERC-1497 documentation](https://developer.kleros.io/en/latest/erc-1497.html#) 📖 

📜  [EIP-1497 ](https://github.com/ethereum/EIPs/issues/1497)📜

