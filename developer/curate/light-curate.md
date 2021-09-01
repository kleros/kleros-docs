# Light Curate

Since Curate was first conceptualized, demand for ethereum block space has skyrocketed. This put a high price floor on the usecases that Curate can be with. Furthermore, we learned that there are is a lot more demand for user facing data than for contract to contract queries.

Light Curate is a new version of the contract that significantly decreases costs of deployment and operation of Curate lists by leveraging new technologies and changing the strategy for data storage.

1- Light Curate does not use contract storage to store item data. Instead, we only store the item's IPFS multihash in the contract. This means other contracts can't query the TCR with field values, but storage costs are roughly O(1) vs Classic Curate's O(n).
2- The Graph `ipfs` api means we can also store the item fields in the subgraph. This comes with several benefits, among them: - No need to use `@kleros/gtcr-encoder` to encode and decode items. Just query the subgraph and you have the item. - Faster, scalable search: Classic Curate needs to sync with the client by downloading every single item and decoding it. With subgraphs we do not need to do this and can query the fields directly. - New need for complex solidity code searching fields on-chain.
3- EIP-1167: Light Curate uses the minimal proxy for new deployments. This means the cost of deploying a new TCR dropped from roughly 7 million gas to 700k. Ten times cheaper!

## Development

This section will be devided into 3 sections:

1- Fetching Parameters: Your UI needs to display some important information to the users such as, what is the bounty for successfuly challenges and how long do items stay in the challenge period.
1- Item Submission: Here you will learn how to build a button to submit an item to the UI.
2- Fetching Items: How to view items and item details.
3- Item Interaction: This includes challenging, submitting evidence and crowdfunding appeals.

### Fetching Parameters

We use a view contract to fetch all the relevant information at once.
Deployments:

- Kovan: `0x2dba4b729cb5f73bf85e7012ea99aa477a210dd6`

> Note: If you are using react, you can take the hook we built [here](https://github.com/kleros/light-gtcr-example/blob/master/src/hooks/tcr-view.js) or use it as an example.

Copy the contract's ABI from [here](../../.gitbook/assets/light-gtcr-view-abi.json).

Using `ethers`, instantiate the contract.

### Item Submission.

With light Curate, item submission consists of first uploading the item to IPFS and then submitting a transaction with the required deposit.
