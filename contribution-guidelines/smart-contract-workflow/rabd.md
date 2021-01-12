---
description: Read this before hitting the big red button.
---

# RABd \(+ Deploy\)

Once deployed, smart contract code becomes **immutable**, so you better get it right the first time. This is a very different setting to traditional software development where you can continuously release fixes and enhancements. Although, there are [patterns for upgrading smart contracts](https://blog.trailofbits.com/2018/09/05/contract-upgrade-anti-patterns), they are anything but trivial, and can come with their own flaws.

The following steps should be taken to minimize risk:

1. [x] Make sure [RAB](rab.md) has been completed for the contract you are deploying and all the contracts in its inheritance chain.
2. [x] Create an issue titled "Deploy &lt;SmartContract&gt;".
3. [x] Label it with the appropriate priority, appropriate status, and "maintenance" type.
4. [x] Assign it to the team member tasked with deploying the contract.

Once that's done, the assignee does the following:

1. Creates a pull request titled "chore/deploy-&lt;smart-contract&gt;", that adds the latest commit hash of the `master` branch and the soon to be contract address, separated by a "@" character \(e.g. `90ed3a5e944d7e7c5d413366ad9f0c530cd92880@0xb7faddf3ecd2402a7e48cea6d2637d90eeb5a7e6`\), to the contract's RAB pragma comment's deployments list, and closes the issue.
2. Labels it with the appropriate priority, appropriate status, and "maintenance" type.
3. Assigns himself and adds the whole review team as reviewers.
4. Concatenates all the necessary contract code into a single snippet or gist and posts it in the pull request.
5. Waits for everyone to check off on the code.
6. Gives the code a final read and deploys it using something like Remix or a CLI, before verifying the code on [Etherscan](https://etherscan.io).
7. Adds the contract address to the contract's RAB pragma comment if not already there, changes the status to the "review needed" status and waits for another team member to approve and merge.

{% hint style="success" %}
Verifying code on [Etherscan](https://etherscan.io) is a great way to enhance transparency and let users interact with your contract directly in an easier manner.
{% endhint %}



