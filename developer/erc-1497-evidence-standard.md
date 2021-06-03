---
description: An evidence standard for arbitration
---

# ERC 1497: Evidence Standard

📖 [Link to full ERC-1497 documentation](https://developer.kleros.io/en/latest/erc-1497.html#) 📖‌

📜 [EIP-1497](https://github.com/ethereum/EIPs/issues/1497) 📜

### Abstract

The following describes the standards for `MetaEvidence` and `Evidence` for dispute resolution. `Evidence` is provided by a participant in a dispute in order to support their assertion. `MetaEvidence` gives context to the dispute so that arbitrators are able to accurately and fairly evaluate it. This standard follows [ERC 792](https://github.com/ethereum/EIPs/issues/792) and references `Arbitrator` and `Arbitrable` contracts.

### Motivation

Standardizing `MetaEvidence` and `Evidence` allows interoperability between `Arbitrable` DApps \(DApps where disputes can arise\) and `Arbitrator` DApps \(DApps which can be used to resolve disputes\). It allows these applications to easily switch from one arbitration service to another, or to let their users decide which arbitration service to use without having to spend time to integrate with all of them. `MetaEvidence` is required to provide the context of the dispute. `Evidence` allows for dispute participants to submit extra information for the arbitrators.

The ERC792 standardizes the way the smart contracts interact with each other while this standard is made to standardize the way the interfaces interact in the context of disputes.

![](../.gitbook/assets/image%20%287%29%20%282%29%20%282%29%20%282%29%20%281%29.png)

## Introduction to the Evidence Standard

The purpose of this specification is to create a standard way for DApps that are part of the dispute resolution process to share context and information. This standard should allow DApps that have disputes they need arbitrated a way to provide the details of the dispute to the Arbitrator. Conversely, for an Arbitrator interface to be able to display a dispute to be ruled on, there needs to be a standard way for the interface to fetch evidence from the Arbitrable contracts.

  
Let’s consider an example where a developer is asked to develop an e-commerce website. The contracting party locks up the payment for the website in an escrow smart contract. Unfortunately, once the developer submits her work, there is a disagreement on whether the terms have been met and a dispute is raised in the smart contract. Now the case will go to an arbitration service, but in order for the arbitrators to make a fair ruling, they need to understand what the dispute is about and to take into consideration the arguments from both parties.

In essence, there are two kinds of evidence needed for the arbitrators to be able to make a ruling.

The first type of evidence, called MetaEvidence, provides the whole picture behind the dispute. In this case, it could be the original off-chain contract or agreement, as well as important information regarding what consequence\(s\) an arbitrator's ruling will have. MetaEvidence is used to convey this information to the chosen arbitrator.

The second type is the material evidence, such as emails, screenshots and contracts or testimony provided by each party to try to prove that the dispute should be ruled in their favor. In the above case, the programmer might submit the code as evidence, while the contracting party submits screenshots of what is missing.

In the case of our Evidence Standard, MetaEvidence is the context while Evidence is the proof provided by each party.

## How it works

  
In order to provide flexibility for all different types of disputes, and to try to keep minimal information on the chain, we decided to create standardized JSON objects that can be hosted anywhere and fetched by an interface to display a dispute. Below we provide some examples. For more information on what each field does, take a look at the [standard specification](https://github.com/ethereum/EIPs/issues/1497).

####  MetaEvidence: <a id="metaevidence-"></a>

We have already discussed what MetaEvidence is, so let’s take a look at how a piece of MetaEvidence might actually look and how it would be used. Each dispute has one piece of MetaEvidence that is used to give all of the contextual information for a contract that might be disputed. MetaEvidence should be created at the same time as the agreement so that it can be impartial. The only restriction on MetaEvidence is that it must be created before a dispute can be raised in the smart contract.  
Here's an example of MetaEvidence JSON:

```text
{
	"fileURI": "/ipfs/QmUQMJbfiQYX7k6SWt8xMpR7g4vwtAYY1BTeJ8UY8JWRs9", 
	"fileHash": "QmUQMJbfiQYX7k6SWt8xMpR7g4vwtAYY1BTeJ8UY8JWRs9",  		
	"fileTypeExtension": "pdf",
	"category": "Escrow",
	"title": "Alice Builds an e-commerce webpage for Bob",
	"description": "Alice is hired by Bob as a contractor to create an e-commerence website for his company. When completed, the site will be hosted at https://my-site.com.",
	"aliases": {
		"0x56b2b5C88C9AC1D0E5785ED1A7c7B28173F5eE1b": "Alice",
		"0x8961286757C764a4a6Be9689649BA9E08DBaca4a": "Bob"
	},
	"question": "Is the website compliant with the terms of the contract?",
	"rulingOptions": {
		"titles": ["Yes", "No"],
		"descriptions": [
			"The website is compliant. This will release the funds to Alice.",
			"The website is not compliant. This will refund Bob."
	]},
	"evidenceDisplayInterfaceURL": "https://my-site.com/evidence-display/escrow",
	"evidenceDisplayInterfaceURLHash": "QmUQMJbfiQYX7k6SWt8xMpR7g4vwtAYY1BTeJ8UY8JWRs9",
	"selfHash": "QmUQMJbfiQYX7k6SWt8xMpR7g4vwtAYY1BTeJ8UY8JWRs9"
}
```

#### Evidence: <a id="evidence-"></a>

It is also essential in many types of disputes that the participants have a chance to show their viewpoint and give reasons why they believe they are right. Therefore there needs to be a way for an Arbitrator to receive Evidence. The Evidence JSON file includes the following properties:

```text
{
	"fileURI": "/ipfs/QmWQV5ZFFhEJiW8Lm7ay2zLxC2XS4wx1b2W7FfdrLMyQQc",
	"fileHash": "QmWQV5ZFFhEJiW8Lm7ay2zLxC2XS4wx1b2W7FfdrLMyQQc",	
	"fileTypeExtension": "pdf",
	"name": "Email clarifying the terms of the contract.",
	"description": "This is an email sent to Alice from Bob that clarifies that the recommendation page that was expected",
	"selfHash": "QmUQMJbfiQYX7k6SWt8xMpR7g4vwtAYY1BTeJ8UY8JWRs9"
}
```

####  How to use these JSON files: <a id="how-to-use-these-json-files-"></a>

So now we have JSON files with our two types of evidence but we still need a way to link them to our smart contract so that our DApps can interact seamlessly. MetaEvidence and Evidence are submitted and looked up via smart contract event logs. The standard specifies some new events for your smart contracts. When an Evidence is submitted, an event is raised that includes a URI to the JSON file that the submitter can host anywhere they choose. This way we can leverage the immutability and availability of the blockchain to create a permanent log of submission that any interface can look up and use to access the Evidence JSON.  


#### Keeping the data safe with hashes: <a id="keeping-the-data-safe-with-hashes-"></a>

In contentious disputes, it is crucial that Arbitrators can be sure that they receive accurate Evidence and MetaEvidence. For example, if MetaEvidence is tampered with, one of the participants can switch the labels on the ruling options, and an Arbitrator might send funds to the wrong party thinking they are voting the opposite way. To protect against Evidence or MetaEvidence being modified, a series of hashes are used. The JSON for both MetaEvidence and Evidence contains hash fields for things such as linked files. The standard also allows for the hash to be used as the name of the file, like the format IPFS uses, so that files hosted on distributed platforms that guarantee data integrity don’t require any extra work. The arbitrators can use these hashes that are provided when Evidence or MetaEvidence is submitted to verify that nothing has been changed.

