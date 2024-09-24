# Retrieving information from Kleros Dapps

Here you will find information on how to retrieve the information from Kleros Dapps like Curate, Proof of Humanity and the Court to power your own applications.

## Existing Kleros-managed registries

### 1. Contract security metadata registries

Kleros uses three 3 registries on Gnosis Chain to curate information contracts across a number of EVM chains, including Ethereum, Gnosis, Polygon and Binance Smart Chain.&#x20;

The registry URLs and their registry contract addresses on Gnosis chain are as below:

1. [Tokens](https://curate.kleros.io/tcr/100/0x70533554fe5c17CAf77fE530f77eAB933B92af60?ref=blog.kleros.io) (0x70533554fe5c17CAf77fE530f77eAB933B92af60)
2. [Address Tags](https://curate.kleros.io/tcr/100/0x66260C69d03837016d88c9877e61e08Ef74C59F2?ref=blog.kleros.io) (0x66260C69d03837016d88c9877e61e08Ef74C59F2)
3. [Contract Domain Name](https://curate.kleros.io/tcr/100/0x957A53A994860BE4750810131d9c876b2f52d6E1?ref=blog.kleros.io) (0x957A53A994860BE4750810131d9c876b2f52d6E1)

The data from all three registries can be pulled from the Subgraph endpoint of Kleros Curate on Gnosis chain: [https://thegraph.com/hosted-service/subgraph/kleros/legacy-curate-xdai](https://thegraph.com/hosted-service/subgraph/kleros/legacy-curate-xdai)&#x20;

Here is a sample batched GraphQL query to retrieve the most important fields from each of these three registries for a single address:&#x20;

```graphql
{
    addressTags: litems(where:{
      registry:"0x66260c69d03837016d88c9877e61e08ef74c59f2",
      key0_starts_with_nocase: $targetAddress,
      key0_ends_with_nocase: $targetAddress,
      status_in:[Registered, ClearingRequested]
    }, first: 1) {
      key0 #caipAddress
      key1 #publicName
      key2 #projectName
      key3 #infoLink
    }
    contractDomains: litems(where:{
      registry:"0x957a53a994860be4750810131d9c876b2f52d6e1",
      key0_starts_with_nocase: $targetAddress,
      key0_ends_with_nocase: $targetAddress,
      key1: $domain,
      status_in:[Registered, ClearingRequested]
    }, first: 1) {
      key0 #caipAddress
      key1 #domain
    }
    tokens: litems(where:{
      registry:"0x70533554fe5c17caf77fe530f77eab933b92af60",
      key0_starts_with_nocase: $targetAddress,
      key0_ends_with_nocase: $targetAddress,
      status_in:[Registered, ClearingRequested]
    }, first: 1) {
      key0 #caipAddress
      key1 #name
      key2 #symbol
    }
  }
```

#### A few things to note:

* If the intention is to retrieve entries that have passed curation, only filter on statuses **`Registered`** and **`ClearingRequested`.**
* The full data object for each of the entries in Curate are stored as a JSON file on IPFS. If you want to retrieve the entire file to get all the data available, you can use the `data` field to retrieve the IPFS URL, or use the `props` array to retrieve all the available key-value pairs.

### 2. Proof of Humanity

The [Proof of Humanity registry](../../../products/proof-of-humanity/) is a list of verified real humans on the blockchain.&#x20;

The subgraph endpoint for Proof of Humanity on Ethereum Mainnet is as follows:\
[https://thegraph.com/hosted-service/subgraph/kleros/proof-of-humanity-mainnet](https://thegraph.com/hosted-service/subgraph/kleros/proof-of-humanity-mainnet)&#x20;

You can also query the contract directly deployed at [0xC5E9dDebb09Cd64DfaCab4011A0D5cEDaf7c9BDb](https://etherscan.io/address/0xc5e9ddebb09cd64dfacab4011a0d5cedaf7c9bdb). In this case, to check if an address is currently accepted in the registry, you can simply query the `isRegistered` function ([#L1029](https://github.com/Proof-Of-Humanity/Proof-Of-Humanity/blob/master/contracts/ProofOfHumanity.sol#L1029)).

## Arbitrary subgraph queries

If you wish to pull data from custom registries or any other Dapps of Kleros, simply [query one of the subgraphs below](https://thegraph.com/docs/query-the-graph):

{% hint style="info" %}
**Kleros Arbitrable apps subgraphs**

* [Kleros Curate (Mainnet) subgraph](https://thegraph.com/explorer/subgraphs/A5oqWboEuDezwqpkaJjih4ckGhoHRoXZExqUbja2k1NQ?view=Query\&chain=arbitrum-one) (Updated Sep 2024)
* [Kleros Curate (Gnosis) subgraph](https://thegraph.com/explorer/subgraphs/9hHo5MpjpC1JqfD3BsgFnojGurXRHTrHWcUcZPPCo6m8?view=Query\&chain=arbitrum-one) (Updated Sep 2024)
* [Proof of Humanity (Mainnet) subgraph](https://thegraph.com/explorer/subgraph/kleros/proof-of-humanity-mainnet)
* [Proof of Humanity (Kovan) subgraph](https://thegraph.com/explorer/subgraph/epiqueras/proof-of-humanity-kovan)
* [Kleros Court (Mainnet) subgraph](https://thegraph.com/hosted-service/subgraph/salgozino/klerosboard)
* [Kleros Court (Gnosis) subgraph](https://thegraph.com/hosted-service/subgraph/salgozino/klerosboard-xdai)
{% endhint %}

If no subgraph exists for the application you want to read from, you can request one to the Kleros team, or [define ](https://thegraph.com/docs/define-a-subgraph)and [deploy](https://thegraph.com/docs/deploy-a-subgraph) one.
