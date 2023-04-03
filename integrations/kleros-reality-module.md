# Kleros Reality Module

From the Zodiac app within the Safe app, you can deploy a Kleros Reality Module. This is a wrapper of the already existing Reality Module, and will automatically deploy it using Kleros as arbitrator. This module is available in Mainnet, Gnosis Chain, and Polygon.

## Setup

Open your Safe dashboard, and click on _Apps_, search _Zodiac_, and open it.

Click on _Kleros Reality Module_. If you can't see it, it might mean your safe is in a different chain. Kleros is only available on Mainnet, Gnosis and Polygon.

![image](https://user-images.githubusercontent.com/40367733/229220090-2267df33-31f3-499f-a328-f1c61dd082c5.png)

Fill in the information. Some guidelines:

- _Timeout_ is a setting that affects the questions that will be created in Reality. An answer will be considered true if it remains unchanged during this period, unless called to arbitration.
- _Cooldown_ is the period from the point the answer is final, to the point the transaction batch can be executed. This is used to prevent malicious answers that might have slipped through from causing immediate damage, by allowing potential victims to react. In order to prevent damage, parties using the Safe are expected to stay vigilant and regularly pay attention to questions created by this module, as anyone is able to create them, without going through a Snapshot proposal.
- _Expiration_ is how long until an accepted transaction batch becomes too outdated to be executed.
- _Bond_ is the minimum amount required to post an answer to a question. Keeping it large makes it more punishing to attackers. Remember this amount is denominated in the chain's native token.

## SafeSnap

If you encountered this warning:

> _Install SafeSnap after creating the module_

it means one of the following:

- The controller of the ENS is not the Safe.
- You are not in Mainnet.

From here, you have two options. Most of the time, you will want to install SafeSnap manually.

### Have the Safe in control of the Snapshot Space

This is only supported if you are in Mainnet.
 
- Don't do this if you're just testing.
- Don't do this if you're planning on decentralizing later. You can do it later when you're ready.
- Do this if you know what you're doing, and you want to decentralize immediately by removing all the signers of the Safe later.
- This will cost more gas.

To do this, go to [the ENS frontend](https://app.ens.domains/) and type the ENS in. The deployment will work if you just _Set_ the Controller of the ENS with the address of the Safe, but, if you want the Space to be fully in control of the Safe, and not in the control of anything else, you will need to _Transfer_ the ENS itself.

### Configuring SafeSnap manually

Just fill in the parameters normally, click on _Add Module_, and sign the resulting transactions. This will create a _Reality Module_ with everything set up.

After doing this, use a wallet you can use to change the Snapshot Space settings. Open Snapshot, and go to settings.

Go to the Settings -> Advanced, _Add Plugin_.

In `network`, type in the network id of the chain the Safe is in, quotes included.

> Mainnet: `"1"`, Gnosis Chain: `"100"`, Polygon: `"137"`

In `realityAddress`, paste in the address of the Reality Module. You can find this address in your Zodiac App. Check the screenshot below, the left side of the screen.

![image](https://user-images.githubusercontent.com/40367733/229247862-3b946415-f38b-434c-bb7f-cb517807e2c7.png)

For the field `umaAddress`, you can either ignore it or remove the line. Check the sample config below for a deployment on Mainnet.

```
{
  "safes": [
    {
      "network": "1",
      "realityAddress": "0x0811dE7b6CA6fF61C24eB8C6C885F44d1Bca4c28"
    }
  ]
}
```

## Missing `daorequirements`

When you deploy the Reality Module, you will also setup a default template for the Reality questions that will be created. Within this template, there is a section that mentions the following:

> and does it meet the requirements of the document referenced in the dao requirements record at ${dao}.eth?

For reference, [here is a sample question created by the Reality Module](https://reality.eth.limo/app/#!/question/0x5b7dd1e86623548af054a4985f7fc8ccbb554e2c-0xeb3c667f6bb40ece6a17ba99e100e16fd2ba9f0723ad5a5289085b83b707d1f5).

If this _dao requirements record_ document does not exist, then it can be possible to resolve the question as _No_, since it is not possible to match the requirements of a document that does not exist. Alternatively, it could be resolve as _Yes_, since, if there are no requirements, that means there are also no restrictions.

Questions can ultimately be applied for arbitration, by clicking _Apply for arbitration_ in Reality. This has a fixed cost, but parties that have already posted an answer might be incentivized to pay this cost, instead of posting a new answer and doubling the bond. This fixed arbitration cost can change depending on the chain. The [Terms of Service of the Kleros Arbitrator for Reality](https://ipfs.kleros.io/ipfs/QmXyo9M4Z2XY6Nw9UfuuUNzKXXNhvt24q6pejuN9RYWPMr/Reality_Module_Governance_Oracle-Question_Resolution_Policy.pdf) include some guidelines to limit the potential damage of not having set the `daorequirements` record, instructing the jurors to investigate the project, forum, etc, to find a reasonable frame of reference to find out these requirements, and assume some defaults if these requirements cannot be found. Still, this is a failsafe mechanism that should not be relied upon, at it can lead to different assumptions.

In order to avoid this uncertainty, we advice adding a `daorequirements` record in the Snapshot Space ENS. To do so:

- Create an acceptance document (plain text, pdf, anything is fine)
- Proofread it to ensure it will not have unintended consequences. Kleros has experience writing policies and acceptance documents for subjective oracles, feel free to contact us if you want us to take a look.
- Upload the document to IPFS.
- Go to the [ENS frontend](https://app.ens.domains), access the ENS of the Snapshot Space, click on _Add/Edit Record_, and add a new record by selecting _text_ on the left selector, typing in _daorequirements_ in the right selector, and pasting the IPFS identifier.

![image](https://user-images.githubusercontent.com/128833886/229306507-035eb088-1806-40a6-a65b-957340fd0a04.png)

For reference, [here is the ENS record of gnosis.eth](https://app.ens.domains/name/gnosis.eth/details), you can find a `daorequirements` record that points to a plaintext file with [a well defined acceptance criteria](https://ipfs.io/ipfs/QmZXAbYyDt7WUq2HqcvQrnxw7zXGPCGJvQXSrNsjik49Uy).

## How to Use the Reality Module

After the SafeSnap plugin is installed in your space, there will be an extra step when creating proposals, that will allow the creator of the proposal to propose a batch of transaction batches. After you do, a proposal like this will be created.

![image](https://user-images.githubusercontent.com/128833886/229285087-af6c947d-ce56-4163-9656-2b2d918807e8.png)

If the proposal passes, you will be allowed to begin execution. This will create a question in Reality.

![image](https://user-images.githubusercontent.com/128833886/229285220-73d17203-df57-438d-9286-a937cfb33c47.png)

From here, you can answer the question directly, using _Set outcome_.

![image](https://user-images.githubusercontent.com/128833886/229285344-c5dbc5a9-ef39-4ceb-b944-fff0e63f8e19.png)

You can handle it directly from Snapshot, or go to Reality by clicking _Question_. It is adviced to do it in Reality, as you will be able to read extra details, such the contents of the question, the terms of service of the arbitrator, and how long does it take for the current answer to be valid.

When the question is finally resolved, execution will not be able to start until the _Cooldown period_ passes. When it passes, you can use Snapshot to execute. Open the proposal that was accepted, and on the SafeSnap plugin on the bottom, you can execute the transaction.

## Further Information

You can check [Zodiac Intergration](./zodiac-integration.md) and [How to use Reality and Kleros as an Oracle](./types-of-integrations/1.-dispute-resolution-integration-plan/channel-partners/how-to-use-reality.eth-+-kleros-as-an-oracle.md).