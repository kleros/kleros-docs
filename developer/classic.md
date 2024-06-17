# Curate Classic: Integration for Devs

The Kleros-powered [TCR factory and browser](https://curate.kleros.io).

## Introduction

Curate is a web app built to ease interaction with Generalized TCR contracts. With it, users can create new TCRs \(a.k.a. lists\), browse deployed lists and interact with them \(submit, remove or challenge items\).

Decentralized curated lists are most useful as a replacement for apps that do curation without tripartition of powers. Some examples of apps that do this \(and often generate frustation for users\) are:

* Social Media;
* App Stores;
* News Platforms;
* Video Platforms;
* Content Storage;

The status quo is that central parties get to write the law \(listing criteria\), be the judge and enforce rulings on videos, posts etc. Using a Generalized TCR instead, allows these powers to be moved to the edges, such that the users of the app get to write the listing criteria and pick an arbitrator they consider to be neutral. Enforcing is done by the blockchain.

## Quick Start

Kleros provides an SDK to ease integration:

```shell
npm add @kleros/gtcr-sdk
```

> Note: The terms TCR, GTCR and list are used interchangeably here and refer to the same thing: a Generalized TCR contract.

Example: [https://codesandbox.io/s/elastic-frog-d5w32](https://codesandbox.io/s/elastic-frog-d5w32)

### Fetching deployed lists.

Curate uses a factory contract to deploy and keep track of TCRs. To fetch a list of addresses of GTCRs you just have to provide the factory address:

```typescript
// The GTCR factory contract on mainnet is located at: 0xe9dd523600b74b8ef0af164687079a6c437f9cd5
import { GTCRFactory } from "@kleros/gtcr-sdk";

(async () => {
  const gtcrFactory = new GTCRFactory(
    window.ethereum,
    "0xe9dd523600b74b8ef0af164687079a6c437f9cd5"
  );
  await gtcrFactory.getTCRAddresses();
})();
```

You can find a react example at [https://codesandbox.io/s/inspiring-jackson-0nx0q](https://codesandbox.io/s/inspiring-jackson-0nx0q)

> Note: Curate factory deploys 2 contracts per list created: One is the list itself and another is the badges TCR. This second list is a list of lists used to connect TCRs together.

### Fetching an Item

To get information on a single item, use the `getItem` function of the `GeneralizedTCR` class:

```typescript
import { GTCRFactory } from "@kleros/gtcr-sdk";

// This example assumes you have an injected provider
// (e.g. Metamask) set to mainnet.
const GTCR_VIEW_ADDRESS = "0x98f1309f96044000174a89c2a0e2001ea5d7a524";
const IPFS_GATEWAY = "https://cdn.kleros.link";

const LIST_ADDRESS = "0x99A0f0e0d9Ee776D791D2E55c215d05ccF7286fC"; // List of stories for the kleros storytelling program.
const DEPLOYMENT_BLOCK = 10247266; // Optional, but recommended. Setting the deployment block speeds up requests.

const ITEM_ID =
  "0x22a0a12e2c9ac41b15b5c3bc4aab748550663f164f64316e0ff9447b336e3565";

(async () => {
  const gtcr = new GeneralizedTCR(
    window.ethereum,
    LIST_ADDRESS,
    GTCR_VIEW_ADDRESS,
    IPFS_GATEWAY,
    DEPLOYMENT_BLOCK
  );

  const item = await gtcr.getItem(ITEM_ID)
  console.info(item.decodedData) // Outputs the item column values.
})();
```

You can find a react example at [https://codesandbox.io/s/great-frog-rti1f](https://codesandbox.io/s/great-frog-rti1f)

### Fetching Items

You can fetch items from a list using the `getItems` method of the `GeneralizedTCR` class. This will return an array of items with the latest request information:

```typescript
import { GTCRFactory } from "@kleros/gtcr-sdk";

// This example assumes you have an injected provider
// (e.g. Metamask) set to mainnet.
const GTCR_VIEW_ADDRESS = "0x98f1309f96044000174a89c2a0e2001ea5d7a524";
const IPFS_GATEWAY = "https://cdn.kleros.link";

const LIST_ADDRESS = "0x99A0f0e0d9Ee776D791D2E55c215d05ccF7286fC"; // List of stories for the kleros storytelling program.
const DEPLOYMENT_BLOCK = 10247266; // Optional, but recommended. Setting the deployment block speeds up requests.

(async () => {
  const gtcr = new GeneralizedTCR(
    window.ethereum,
    LIST_ADDRESS,
    GTCR_VIEW_ADDRESS,
    IPFS_GATEWAY,
    DEPLOYMENT_BLOCK
  );

  const items = (await gtcr.getItems())
  console.info(items.map(item => item.decodedData)) // Outputs the item column values.
})();
```

You can find a React example at: [https://codesandbox.io/s/elastic-frog-d5w32](https://codesandbox.io/s/elastic-frog-d5w32)

### Fetching Meta Evidence and Metadata

The address of a GTCR by itself is not very useful for building, UIs. Usually we need other information such as the list name, description, logo etc. This data is stored inside the `metadata` field inside the meta evidence file. You can use the `getLatestMetaEvidence` to get the file like so:

```typescript
const gtcr = new GeneralizedTCR(
    window.ethereum,
    LIST_ADDRESS,
    GTCR_VIEW_ADDRESS,
    IPFS_GATEWAY,
    DEPLOYMENT_BLOCK
  );

  const [registrationMetaEvidence, removalMetaEvidence] = (await gtcr.getLatestMetaEvidence())

  // Both removal and registration meta evidence contain the same `metadata`.
  console.info(registrationMetaEvidence.metadata)

  // Outputs
  {
    tcrTitle: string        // The list title.
    tcrDescription: string  // The list description.
    columns: Column[]       // Used by @kleros/gtcr-encoder
    itemName: string        // The noun used when building UIs. E.g. "Token" for a list of tokens -> generates "Submit *token*", "Challenge token", etc.
    itemNamePlural: string  // Plural version of `itemName`.
    logoURI: string         // Link to the list logo. Usually an IPFS URI.
    requireRemovalEvidence: boolean // Whether to require evidence when removing an item.
    isTCRofTCRs: boolean      // Whether this is a list of GTCR addresses.
    relTcrDisabled: boolean    // Whether the badges TCR is enabled.
  }
```

> For more information on meta evidence files, see [EIP-792](https://github.com/ethereum/EIPs/issues/792) and [erc-792 docs](https://developer.kleros.io/en/latest/)introduction.html.

