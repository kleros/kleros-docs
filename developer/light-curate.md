# Light Curate: Integration for Devs

Since Curate was first conceptualized, demand for ethereum block space has skyrocketed. This put a high price floor on the usecases that Curate can be with. Furthermore, we learned that there are is a lot more demand for user facing data than for contract to contract queries.

Light Curate is a new version of the contract that significantly decreases costs of deployment and operation of Curate lists by leveraging new technologies and changing the strategy for data storage.

1- Light Curate does not use contract storage to store item data. Instead, we only store the item's IPFS multihash in the contract. This means other contracts can't query the TCR with field values, but storage costs are roughly O\(1\) vs Classic Curate's O\(n\). 2- The Graph `ipfs` api means we can also store the item fields in the subgraph. This comes with several benefits, among them: - No need to use `@kleros/gtcr-encoder` to encode and decode items. Just query the subgraph and you have the item. - Faster, scalable search: Classic Curate needs to sync with the client by downloading every single item and decoding it. With subgraphs we do not need to do this and can query the fields directly. - New need for complex solidity code searching fields on-chain. 3- EIP-1167: Light Curate uses the minimal proxy for new deployments. This means the cost of deploying a new TCR dropped from roughly 7 million gas to 700k. Ten times cheaper!

## Development

This section will be devided into 3 sections:

1- Fetching Parameters: Your UI needs to display some important information to the users such as, what is the bounty for successfuly challenges and how long do items stay in the challenge period. 1- Item Submission: Here you will learn how to build a button to submit an item to the UI. 2- Fetching Items: How to view items and item details. 3- Item Interaction: This includes challenging, submitting evidence and crowdfunding appeals.

### Fetching Parameters

We use a view contract to fetch all the relevant information at once. Deployments:

* Kovan: `0x2dba4b729cb5f73bf85e7012ea99aa477a210dd6`

> Note: If you are using react, you can take the hook we built [here](https://github.com/kleros/gtcr/blob/5e313ced24f5e3fc3a54f812e07fb1f86a6b2621/src/hooks/tcr-view.js) or use it as an example.

### Item Submission.

With light Curate, item submission consists of first uploading the item to IPFS and then submitting a transaction with the required deposit.

Since we use `@graphprotocol/graph-ts` we must submit items to its ipfs endpoint until they allow custom endpoints. In addition, we also upload to kleros ipfs node.

> In addition to Kleros' and The Graph's, we strongly advise pin the data to ipfs nodes you control as well. Update the provided below for this.

Full example [here](https://github.com/kleros/gtcr/blob/5e313ced24f5e3fc3a54f812e07fb1f86a6b2621/src/utils/ipfs-publish.js)

```text
REACT_APP_IPFS_GATEWAY=https://ipfs.kleros.io
REACT_APP_HOSTED_GRAPH_IPFS_ENDPOINT=https://api.thegraph.com/ipfs
```

#### Upload and Transaction

```text
// ipfs-publish.js

import deepEqual from 'fast-deep-equal/es6'

const mirroredExtensions = ['.json']

/**
 * Send file to IPFS network.
 * @param {string} fileName - The name that will be used to store the file. This is useful to preserve extension type.
 * @param {ArrayBuffer} data - The raw data from the file to upload.
 * @returns {object} ipfs response. Should include the hash and path of the stored item.
 */
export default async function ipfsPublish(fileName, data) {
  if (!mirroredExtensions.some(ext => fileName.endsWith(ext)))
    return publishToKlerosNode(fileName, data)

  const [klerosResult, theGraphResult] = await Promise.all([
    publishToKlerosNode(fileName, data),
    publishToTheGraphNode(fileName, data),
    // Pin to your own ipfs node here as well.
  ])

  if (!deepEqual(klerosResult, theGraphResult)) {
    console.warn('IPFS upload result is different:', {
      kleros: klerosResult,
      theGraph: theGraphResult
    })
    throw new Error('IPFS upload result is different.')
  }

  return klerosResult
}

/**
 * Send file to IPFS network via the Kleros IPFS node
 * @param {string} fileName - The name that will be used to store the file. This is useful to preserve extension type.
 * @param {ArrayBuffer} data - The raw data from the file to upload.
 * @returns {object} ipfs response. Should include the hash and path of the stored item.
 */
async function publishToKlerosNode(fileName, data) {
  const buffer = await Buffer.from(data)
  const url = `${process.env.REACT_APP_IPFS_GATEWAY}/add`

  const response = await fetch(url, {
    method: 'POST',
    body: JSON.stringify({
      fileName,
      buffer
    }),
    headers: {
      'content-type': 'application/json'
    }
  })

  const body = await response.json()

  return body.data
}

/**
 * Send file to IPFS network via The Graph hosted IPFS node
 * @param {string} fileName - The name that will be used to store the file. This is useful to preserve extension type.
 * @param {ArrayBuffer} data - The raw data from the file to upload.
 * @returns {object} ipfs response. Should include the hash and path of the stored item.
 */
async function publishToTheGraphNode(fileName, data) {
  const url = `${process.env.REACT_APP_HOSTED_GRAPH_IPFS_ENDPOINT}/api/v0/add?wrap-with-directory=true`

  const payload = new FormData()
  payload.append('file', new Blob([data]), fileName)

  const response = await fetch(url, {
    method: 'POST',
    body: payload
  })

  const result = await jsonStreamToPromise(response.body)

  return result.map(({ Name, Hash }) => ({
    hash: Hash,
    path: `/${Name}`
  }))
}

/**
 * Accumulates a JSON stream body into an array of JSON objects.
 * @param {ReadableStream} stream The stream to read from.
 * @returns {Promise<any>} An array of all JSON objects emitted by the stream.
 */
async function jsonStreamToPromise(stream) {
  const reader = stream.getReader()
  const decoder = new TextDecoder('utf-8')

  const deferred = {
    resolve: undefined,
    reject: undefined
  }

  const result = new Promise((resolve, reject) => {
    deferred.resolve = resolve
    deferred.reject = reject
  })

  const acc = []
  const start = async () => {
    reader
      .read()
      .then(({ done, value }) => {
        if (done) return deferred.resolve(acc)

        // Each `read` can produce one or more lines...
        const lines = decoder.decode(value).split(/\n/)
        const objects = lines
          .filter(line => line.trim() !== '')
          .map(line => JSON.parse(line))
        acc.push(...objects)

        return start()
      })
      .catch(err => deferred.reject(err))
  }

  start()

  return result
}
```

The JSON file for the object is composed of the its metadata and fields.

* Metadata \(columns\): An array describing each of the items columns \(what's its type, name, description, etc.\)
* Values \(values\): An object mapping the column name to the value.

The metadata is available inside the meta evidence file, which is returned by the useTCRView hook. The Values are input by the user.

Example of columns used by the TCR at

```text
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

```text
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

```text
const gtcr = new ethers.Contract(tcrAddress, _gtcr, signer)
const enc = new TextEncoder()
const fileData = enc.encode(JSON.stringify({ columns, values }))
const ipfsEvidenceObject = await ipfsPublish('item.json', fileData)
const ipfsEvidencePath = `/ipfs/${ipfsEvidenceObject[1].hash +
    ipfsEvidenceObject[0].path}`

// Request signature and submit.
const tx = await gtcr.addItem(ipfsEvidencePath, {
    value: submissionDeposit
})
```

### Fetching Items

> We break down this section into two as list views and details view have different requirements.

Fetchin items is best done via the subgraph we provide. If you deployed an list using the factory, it already has a subgraph deployed and available \(here\)\[[https://thegraph.com/explorer/subgraph/kleros/light-curate-kovan](https://thegraph.com/explorer/subgraph/kleros/light-curate-kovan)\].

#### List

Whenever we want to fetch items, or a specific item, we must pass the TCR address to the subgraph.

See \(this react example\)\[[https://github.com/kleros/gtcr/blob/5e313ced24f5e3fc3a54f812e07fb1f86a6b2621/src/pages/items/index.js](https://github.com/kleros/gtcr/blob/5e313ced24f5e3fc3a54f812e07fb1f86a6b2621/src/pages/items/index.js)\] for more details.

A standard query for the first page of a given list, ordered by the most recent requests, looks like this.

```text
const ITEMS_PER_PAGE = 40
const orderDirection = 'asc'
const page = 1
const itemsWhere = `{ registry: "${tcrAddress.toLowerCase()}" }`
const GTCR_SUBGRAPH_URL='https://api.thegraph.com/subgraphs/name/kleros/light-curate-kovan'
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
          props {
              value
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
        body: JSON.stringify(query)
    })
  ).json()
```

#### Details

If you want, you can also use apollo to cache queries and make the app load faster.

```text
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

