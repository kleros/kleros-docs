---
description: A standard for Arbitrable and Arbitrator contracts
---

# ERC-792: Arbitration Standard

### Abstract

The ERC-792 - Arbitration Standard describes a standard of `Arbitrable` and `Arbitrator` contracts. Every Arbitrable contract can be adjudicated by every Arbitrator contract. Arbitrator contracts give rulings and Arbitrable contracts enforce them.

### Motivation

Using two contracts allows separation between the ruling and its enforcement. This abstraction allows `Arbitrable` contract developers not to have to know the internal process of the `Arbitrator` contracts. Neither do `Arbitrator` contract developers with `Arbitrable` ones.  
It allows dapps to easily switch from one arbitration service to another one. Or to allow their users to choose themselves their arbitration services.

![](../.gitbook/assets/image.png)

In the linked documentation, you will be guided through the usage of this standard. We will implement some examples for `Arbitrable` and `Arbitrator` contracts.

📖 [Link to full ERC-792 documentation](https://developer.kleros.io/en/latest/index.html) 📖 

📜 [EIP-792](https://github.com/ethereum/EIPs/issues/792) 📜

