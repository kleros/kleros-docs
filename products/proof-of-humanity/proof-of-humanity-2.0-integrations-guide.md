# **Proof of Humanity (PoHv2): Integration Guide**

## Introduction

Welcome to the Proof of Humanity v2 (PoHv2) integration documentation. This guide will walk you through the process of integrating the PoHv2 smart contracts into your DApp project. We've designed our platform to make interacting with the multichain curated list of humans seamless and secure.

## Key Features

- A Sybil-resistant protocol (non-duplicate and bot-proof) registry of humans.
- Prevents duplicate accounts, ensuring each entry represents a distinct individual.
- Trusted list of humans curated by a decentralized community.
- Consultable human identities registered through a unique wallet account, enhancing transparency and trustworthiness.
- Airdrop feasibility, enabling seamless token distribution to verified human identities.
- Ensures that accounts reached through the airdrop correspond to different humans, preventing token accumulation in a single identity.
- Operates across multiple blockchain networks, allowing for widespread adoption and flexibility.
- PoHv2 is currently deployed in Ethereum and Gnosis.
- PoHv2 is an open-source project developed and maintained by Kleros.
- The Kleros Justice Protocol is a (multichain) on-chain dispute resolution platform. It is integrated into PoHv2 and constitutes the ultimate resource utilized to verify and maintain the curated list of human identities registered in PoHv2.

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

- For verifying if an account **is registered** in PoHv2, it is necessary to call the `isHuman(address)` function on the crossChain contract deployed on the target chain.
- For verifying if the target chain is the **home chain** of a registered account, it is necessary to call the `isHuman(address)` function on the main PoHv2 contract deployed on the target chain.

In general, you just want to verify that an account is verified (so call the crossChain contract).

However, if your application is deployed on multiple chains and you don't want to allow a user to be registered with the same humanity on both chains (for example, if you are streaming a UBI to the user, you may want to be sure they can only claim it on one chain), you should call the PoHv2 contract to verify it is their home chain. You must also have a way to notify your app that the user does not have a home chain application anymore (as users can move their home chain to another chain; for example, in the case of streaming a UBI, you can allow anyone to call a function to terminate the user's stream if they are not registered on PoHv2 of this specific chain anymore).
