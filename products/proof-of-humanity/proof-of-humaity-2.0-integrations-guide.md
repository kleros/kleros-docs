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

### Elementary methods of main PoHv2 contracts (Ethereum and Gnosis)

#### isHuman(address)

Check whether the account corresponds to a claimed humanity

Parameters:

- account(address): the address to verify

Returns:

- a boolean

#### humanityOf(address)

Get the humanity corresponding to an address. Returns zero if it corresponds to no humanity.

Parameters:

- account(address): the address to consult

Returns

- humanityId(bytes20): the humanity id

#### getHumanityInfo(bytes20)

Get additional information about the registered humanity

Parameters:

- humanityId(bytes20): the humanity to consult

Returns

- vouching(bool): whether the human is currently vouching for another humanity claim
- pendingRevocation(bool): the profile has a pending revocation of its humanity
- nbPendingRequests(uint48): requests to be attended
- expirationTime(uint40): time in seconds when this humanity registry expires
- owner(address): the account corresponding to this humanity
- nbRequests(uint256): number of historical requests corresponding to this humanity

### About cross-chain contracts and its elementary methods

Cross-chain contracts handle two main functions:

- Update: relays profile data from the main PoHv2 contract instance deployed on the chain where the humanity identity is currently registered (referred to as the home chain) to the cross-chain contract instance deployed on the foreign chain of that humanity’s home chain.
- Transfer: removes the humanity registry from the main PoHv2 contract deployed on the sender chain, and relays and adds it on the receiver chain.

If a humanity is registered on chain A, that chain is considered the home chain. There is a flag `homeChain` for all humanities in the cross-chain contracts which is set to true when relaying state updates from that instance (or when receiving a humanity transfer). It is set to false when a state update is received from another chain or the cross-chain instance initiates relaying a transfer.

The main PoHv2 and cross-chain contracts implement similar interfaces for checking the humanity state. When checking the state of a humanity, it is possible to choose consulting:

- The state only from its home chain by fetching data from the main PoHv2 contract, or

- The state from both its home chain, and received from the foreign chain, from the cross-chain contracts

Warning: The latter option might not be up-to-date because changes in humanity state on other chains need to be relayed to be reflected. Thus it could be possible for the `homeChain` flag to be outdated.

Therefore, in cases where a humanity has been relayed (or transferred), it is possible to check its state through similar methods as described above.

#### isHuman(address)

Same as for main contracts

#### humanityOf(address)

Same as for main contracts

#### humanityData(bytes20)

Additional information about the registered humanity and its interaction with cross-chain functionalities.

Parameters:

- humanityId(bytes20): the humanity to consult

Returns

- owner(address): the account corresponding to this humanity
- expirationTime(uint40): time in seconds when this humanity registry expires
- lastTransferTime(uint40): time in seconds when this humanity identity has been transferred from the foreign chain
- isHomeChain(bool): whether the humanity identity is registered in the main PoHv2 contract instance deployed on this chain

## Basic interactions

### On-chain verifications:

For verifying if an account is registered in PoHv2, it is necessary to call the `isHuman` function on the main PoHv2 contract deployed in the partner's chain (eg, Gnosis).

In case the `isHuman` call renders true, one may want to address whether the account's **home chain** corresponds to the partner's chain. To that end, it is necessary to call functions from the cross-chain contract deployed on the partner's chain as follows:

- call the `humanityOf` function to obtain the _bytes20 humanity id_
- call the `humanityData` function with the obtained humanity id to observe the `expirationTime` and the `isHomeChain` parameters.

The results can be interpreted as follows:

- If the outcome has no record for this account, it means that the account was originally registered on the same partner's chain and thus, it is the home chain. This is so, since transferred profiles leaves record of this action on the cross-chain contract, and no record means the account has never been transferred.
- If the outcome triggers the `isHomeChain` parameter as true and the `expirationTime` has not been reached, then the account's home chain is the partner's chain.
- If the outcome triggers the `isHomeChain` parameter as false and the `expirationTime` has not been reached, then the account's home chain is not the partner's chain.
- If the outcome triggers an `expirationTime` that has already been reached, then the account's home chain is the partner's chain, no matter which is the `isHomeChain` outcome. This is so, given that the information on the cross-chain contract corresponds to an old transfer, and therefore we know that this latter account's instance has been created on the partner's chain.
