---
description: >-
  Smart contract development poses unique challenges and experience has taught
  us that not all the rules of traditional software apply.
---

# Task Tracking & Lifecycle

## \`contract\` Smart Contract Workflow \`is\` General Workflow {...}

Most of the guidelines of [Task Tracking & Lifecycle](../general-dev.-workflow/task-tracking-and-lifecycle.md) in the general workflow apply, with one key difference.

There is no automatic branch deployment, because we do not think you should rely on package managers for production smart contract development and deployment, more on that later. Because of this, it doesn't make sense to have staging or production environments, so all pull requests are made to `master`.

{% hint style="danger" %}
Do not rely on package managers for production smart contract development and deployment.
{% endhint %}

## Lite Pull Requests Reviews

In smart contract repos, pull requests are not expected to be full contract vulnerability reviews. Instead, review style, dependency changes, tests, etc and perform a very brief contract review to see if you catch anything obvious. This means that just because a contract is in `master` does not mean it is ready for production.

{% hint style="success" %}
Review style, dependency changes, tests, etc and perform a very brief contract review to see if you catch anything obvious.
{% endhint %}

This creates an optimal environment for hackers and external contributors to find vulnerabilities the team might not have found. We have noticed that having branches categorized by review rigorousness creates an unfavorable environment where people don't look at less rigorous branches because they don't feel as if them finding a vulnerability in there is as important as finding one in a production branch, and they don't look at the more rigorous branches because there are less contracts there and they think they are less likely to find something worth their time.

