# Light Curate: Integration for Devs

Since Curate was first conceptualized, demand for ethereum block space has skyrocketed. This put a high price floor on the usecases that Curate can be with. Furthermore, we learned that there are is a lot more demand for user facing data than for contract to contract queries.

Light Curate is a new version of the contract that significantly decreases costs of deployment and operation of Curate lists by leveraging new technologies and changing the strategy for data storage.

1- Light Curate does not use contract storage to store item data. Instead, we only store the item's IPFS multihash in the contract. This means other contracts can't query the TCR with field values, but storage costs are roughly O\(1\) vs Classic Curate's O\(n\). 2- The Graph `ipfs` api means we can also store the item fields in the subgraph. This comes with several benefits, among them: - No need to use `@kleros/gtcr-encoder` to encode and decode items. Just query the subgraph and you have the item. - Faster, scalable search: Classic Curate needs to sync with the client by downloading every single item and decoding it. With subgraphs we do not need to do this and can query the fields directly. - New need for complex solidity code searching fields on-chain. 3- EIP-1167: Light Curate uses the minimal proxy for new deployments. This means the cost of deploying a new TCR dropped from roughly 7 million gas to 700k. Ten times cheaper!

## Development

This section will be devided into 3 sections:

1- Fetching Parameters: Your UI needs to display some important information to the users such as, what is the bounty for successfuly challenges and how long do items stay in the challenge period. 1- Item Submission: Here you will learn how to build a button to submit an item to the UI. 2- Fetching Items: How to view items and item details. 3- Item Interaction: This includes challenging, submitting evidence and crowdfunding appeals.

### Fetching Parameters

We use a view contract to fetch all the relevant information at once. Deployments:


* Gnosis: `0x08e58Bc26CFB0d346bABD253A1799866F269805a` ([source](https://github.com/kleros/gtcr-subgraph/blob/master/networks.json))

> Note: If you are using react, you can take the hook we built [here](https://github.com/kleros/gtcr/blob/5e313ced24f5e3fc3a54f812e07fb1f86a6b2621/src/hooks/tcr-view.js) or use it as an example.

### Item Submission.

With light Curate, item submission consists of first uploading the item to IPFS and then submitting a transaction with the required deposit.

Since we use `@graphprotocol/graph-ts` we must submit items to its ipfs endpoint until they allow custom endpoints. In addition, we also upload to kleros ipfs node.

> In addition to Kleros' and The Graph's, we strongly advise pin the data to ipfs nodes you control as well. Update the provided below for this.

Full example [here](https://github.com/kleros/gtcr/blob/5e313ced24f5e3fc3a54f812e07fb1f86a6b2621/src/utils/ipfs-publish.js)

```bash
REACT_APP_IPFS_GATEWAY=https://cdn.kleros.link
REACT_APP_HOSTED_GRAPH_IPFS_ENDPOINT=https://api.thegraph.com/ipfs
```

#### Upload and Transaction

```typescript
const pinFiles = async (
  data: FormData,
  pinToGraph: boolean
): Promise<
  [Array<string>, Array<{ filebaseCid: string; graphCid: string }>]
> => {
  const cids = new Array<string>();
  // keep track in case some cids are inconsistent
  const inconsistentCids = new Array<{
    filebaseCid: string;
    graphCid: string;
  }>();

  for (const [_, dataElement] of Object.entries(data)) {
    if (dataElement.isFile) {
      const { filename, mimeType, content } = dataElement;
      const path = `${filename}`;
      const cid = await filebase.storeDirectory([
        new File([content], path, { type: mimeType }),
      ]);

      if (pinToGraph) {
        const graphResult = await publishToGraph(filename, content);
        if (!areCidsConsistent(cid, graphResult)) {
          console.warn("Inconsistent cids from Filebase and Graph Node :", {
            filebaseCid: cid,
            graphCid: graphResult[1].hash,
          });
          inconsistentCids.push({
            filebaseCid: cid,
            graphCid: graphResult[1].hash,
          });
        }
      }

      cids.push(`/ipfs/${cid}/${path}`);
    }
  }
  return [cids, inconsistentCids];
};


/**
 * Send file to IPFS network via The Graph hosted IPFS node
 * @param data - The raw data from the file to upload.
 * @returns  ipfs response. Should include the hash and path of the stored item.
 */
export const publishToGraph = async (fileName, data) => {
  const url = `${process.env.GRAPH_IPFS_ENDPOINT}/api/v0/add?wrap-with-directory=true`;

  const payload = new FormData();
  payload.append("file", new Blob([data]), fileName);

  const response = await fetch(url, {
    method: "POST",
    body: payload,
  });

  if (!response.ok) {
    throw new Error(
      `HTTP error! status: ${response.status}, Failed to pin to graph`
    );
  }

  const result = parseNewlineSeparatedJSON(await response.text());

  return result.map(({ Name, Hash }) => ({
    hash: Hash,
    path: `/${Name}`,
  }));
};

/**
 * @description parses json from stringified json's seperated by new line
 */
const parseNewlineSeparatedJSON = (text) => {
  const lines = text.trim().split("\n");
  return lines.map((line) => JSON.parse(line));
};

export const areCidsConsistent = (filebaseCid, graphResult) => {
  const graphCid = graphResult[1].hash;
  return graphCid === filebaseCid;
};

```

The JSON file for the object is composed of the its metadata and fields.

* Metadata \(columns\): An array describing each of the items columns \(what's its type, name, description, etc.\)
* Values \(values\): An object mapping the column name to the value.

The metadata is available inside the meta evidence file, which is returned by the useTCRView hook. The Values are input by the user.

Example of columns used by the TCR at

```json
[
  {
    "label": "Logo",
    "description": "The token's logo.",
    "type": "image",
    "isIdentifier": false
  },
  {
    "label": "Name",
    "description": "The token name.",
    "type": "text",
    "isIdentifier": true
  },
  {
    "label": "Ticker",
    "description": "The token ticker.",
    "type": "text",
    "isIdentifier": true
  },
  {
    "label": "Address",
    "description": "The token address.",
    "type": "address",
    "isIdentifier": true
  },
  {
    "label": "Chain ID",
    "description": "The ID of the chain the token contract was deployed",
    "type": "number"
  },
  {
    "label": "Decimals",
    "description": "The number of decimal places.",
    "type": "number"
  }
]
```

And an example of values. Note that it is required for the keys to match the column names in the columns object.

```json
{
  "Logo": "/ipfs/QmT4vij3PrGZEQ1zarTrPmkqQWggRQN6VEpewSHJXbkeXh/pnk-logo.png",
  "Name": "Pinakion",
  "Ticker": "PNK",
  "Address": "0x93ED3FBe21207Ec2E8f2d3c3de6e058Cb73Bc04d",
  "Chain ID": "1",
  "Decimals": "18"
}
```

With this in hand we can submit the item.

```typescript
const gtcr = new ethers.Contract(tcrAddress, _gtcr, signer)
const enc = new TextEncoder()
const fileData = enc.encode(JSON.stringify({ columns, values }))
const ipfsEvidencePath = await ipfsPublish('item.json', fileData)

// Request signature and submit.
const tx = await gtcr.addItem(ipfsEvidencePath, {
    value: submissionDeposit
})
```

### Fetching Items

> We break down this section into two as list views and details view have different requirements.

Fetching items is best done via the subgraph we provide. If you deployed a list using the factory, it already has a subgraph deployed and available [here](https://thegraph.com/explorer/subgraphs/9hHo5MpjpC1JqfD3BsgFnojGurXRHTrHWcUcZPPCo6m8?view=Query&chain=arbitrum-one).

#### List

Whenever we want to fetch items, or a specific item, we must pass the TCR address to the subgraph.

See [this react example](https://github.com/kleros/gtcr/blob/7995e3de0a740dc1056a03a68a34185ac71d8909/src/utils/graphql/light-items.js#L29-L37) for more details.

A standard query for the first page of a given list, ordered by the most recent requests, looks like this.

```typescript
const ITEMS_PER_PAGE = 40
const orderDirection = 'asc'
const page = 1
const itemsWhere = `{ registry: "${tcrAddress.toLowerCase()}" }`
const GTCR_SUBGRAPH_URL=`https://gateway-arbitrum.network.thegraph.com/api/${YOUR_API_KEY}/subgraphs/id/9hHo5MpjpC1JqfD3BsgFnojGurXRHTrHWcUcZPPCo6m8` // You need to replace with your API key
const query = {
  query: `
      {
        items(
          skip: ${(Number(page) - 1) * ITEMS_PER_PAGE}
          first: ${ITEMS_PER_PAGE}
          orderDirection: ${orderDirection}
          orderBy: latestRequestSubmissionTime
          where: ${itemsWhere}
        ) {
          itemID
          status
          data
          metadata{
              props {
               value
             }
          }
          requests(first: 1, orderBy: submissionTime, orderDirection: desc) {
            disputed
            disputeID
            submissionTime
            resolved
            requester
            challenger
            resolutionTime
            rounds(first: 1, orderBy: creationTime, orderDirection: desc) {
              appealPeriodStart
              appealPeriodEnd
              ruling
              hasPaidRequester
              hasPaidChallenger
              amountPaidRequester
              amountPaidChallenger
            }
          }
        }
      }
    `
  }
  const { data, errors } = await (
    await fetch(GTCR_SUBGRAPH_URL, {
        method: 'POST',
        headers: {
          'Content-Type': "application/json",
        },
        body: JSON.stringify(query)
    })
  ).json()
```

#### Details

If you want, you can also use apollo to cache queries and make the app load faster.

```typescript
const ITEM_DETAILS_QUERY = gql`
  query itemDetailsQuery($id: String!) {
    item(id: $id) {
      data
      requests(orderBy: submissionTime, orderDirection: desc) {
        requestType
        disputed
        disputeID
        submissionTime
        resolved
        requester
        arbitrator
        challenger
        evidenceGroupID
        creationTx
        resolutionTx
        rounds(orderBy: creationTime, orderDirection: desc) {
          appealPeriodStart
          appealPeriodEnd
          ruling
          hasPaidRequester
          hasPaidChallenger
          amountPaidRequester
          amountPaidChallenger
        }
      }
    }
  }
`

  // subgraph item entities have id "<itemID>@<listaddress>"
  const compoundId = `${itemID}@${tcrAddress.toLowerCase()}`
  const detailsViewQuery = useQuery(ITEM_DETAILS_QUERY, {
    variables: { id: compoundId }
  })
```

### Item Interaction

This is the easiest part of the application. All items are referenced by their ID which is the keccak256 hash of the IPFS URI.

With it you can:

* Execute requests: This is for when a request passed the challenge period without any challenges.
* Challenge requests \(registration or removal\) via the contract's `challengeRequest` function
* Submit evidence: `submitEvidence` by passing the evidence json file following \(ERC-1497\)\[[https://kleros.gitbook.io/docs/developer/erc-1497-evidence-standard](https://kleros.gitbook.io/docs/developer/erc-1497-evidence-standard)\] standard.
* Fund appeals: `fundAppeal`

