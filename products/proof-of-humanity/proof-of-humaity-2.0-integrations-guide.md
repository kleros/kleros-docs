# **Proof of Humanity (PoHv2): Integration Guide**

## Introduction

Welcome to the Proof of Humanity v2 (PoHv2) integration documentation. This guide will walk you through the process of integrating the PoHv2 smart contracts into your DApp project. We've designed our platform to make interacting with the multichain curated list of humans seamless and secure.

## Key Features

- A sybil resistant protocol (non-duplicate and bot-proof) registry of humans.
- Prevents duplicate accounts, ensuring each entry represents a distinct individual.
- Trusted list of humans curated by a decentralized community.
- Consultable human identities registered through a unique wallet account, enhancing transparency and trustworthiness.
- Airdrop feasibility, enabling seamless token distribution to verified human identities.
- Ensures that accounts reached through the airdrop correspond to different humans, preventing token accumulation in a single identity.
- Operates across multiple blockchain networks, allowing for widespread adoption and flexibility.
- PoHv2 is currently deployed in Ethereum and Gnosis.
- PoHv2 is an open-source project developed and maintained by Kleros.
- The Kleros Justice Protocol is a (multichain) on-chain dispute resolution platform. It is integrated to PoHv2 and constitutes the ultimate resource utilized to verify and maintain the curated list of human identities registered in PoHv2.

## Smart Contract Interactions

### Main contracts

#### Ethereum

Main PoHv2 proxy contract: [0xbE9834097A4E97689d9B667441acafb456D0480A](https://etherscan.io/address/0xbE9834097A4E97689d9B667441acafb456D0480A)

CrossChain proxy contract: [0xa478095886659168E8812154fB0DE39F103E74b2](https://etherscan.io/address/0xa478095886659168E8812154fB0DE39F103E74b2)

#### Gnosis

Gnosis main PoHv2 proxy contract: [0xa4AC94C4fa65Bb352eFa30e3408e64F72aC857bc](https://gnosisscan.io/address/0xa4AC94C4fa65Bb352eFa30e3408e64F72aC857bc)

Gnosis CrossChain proxy contract: [0x16044E1063C08670f8653055A786b7CC2034d2b0](https://gnosisscan.io/address/0x16044E1063C08670f8653055A786b7CC2034d2b0)

## Basic interactions

### On-chain verification:

For verifying if an account is registered in PoHv2, it is necessary to call the `isHuman(address)` function on the cross-chain contract deployed on the target chain. The result is a boolean.

In addition, for verifying if the target chain is the **home chain** it is necessary to call the following functions on the same cross-chain contract's instance:

- call the `humanityOf` function to obtain the _bytes20 humanity id_
- call the `humanityData` function with the obtained humanity id to observe the resulting parameters:

#### humanityData(bytes20)

Additional information about the registered humanity and its interaction with cross-chain functionalities.

Parameters:

- humanityId(bytes20): the humanity to consult

Returns

- owner(address): the account corresponding to this humanity
- expirationTime(uint40): time in seconds when this humanity registry expires
- lastTransferTime(uint40): time in seconds when this humanity identity has been transferred from the foreign chain
- isHomeChain(bool): whether the humanity identity is registered in the main PoHv2 contract instance deployed on this chain

The results can be interpreted as follows:

- If the outcome has no record for this account, it means that the account was originally registered on the target chain and thus, it is the **home chain**.
- If the outcome triggers the `isHomeChain` parameter as true, the `expirationTime` has not been reached, and `owner` corresponds to this PoHv2 account, then the account's **home chain** is the target chain.
