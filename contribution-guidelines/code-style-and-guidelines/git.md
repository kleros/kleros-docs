---
description: Controlling version control.
---

# Git

We use Git for version control and use [Conventional Commits](https://www.conventionalcommits.org) for branch names and commit messages to enforce consistency and enjoy automatic changelog generation.

## Branches

Use short and descriptive, kebab-cased names with a conventional commits type prefix separated by a slash, like so:

* `feat/implement-arbitrator`
* `fix/invalid-rulings-from-arbitrator`

When several people are working on a branch, you may create personal branches that can be merged before merging the main branch to `develop`. For example:

* `feat/implement-arbitrator/alice`
* `feat/implement-arbitrator/bob`

{% hint style="info" %}
Always delete merged branches, locally and remotely. You can use the following command to list them, `git branch --merged | grep -v "\*"`.
{% endhint %}

## Commits

It's important for commits to follow a standard to allow efficient navigation of change history in the case of regressions and to make reviewers' lives easier.

### When to Commit

As a general guideline, each commit should be a single logical change. Don't make several logical changes in one commit. For example, if a commit fixes a bug and optimizes the performance of a feature, split it. Here are some useful tips:

* Use `git add -p` to interactively stage specific portions of modified files.
* Commit early and often. Small, self-contained commits are easier to understand and revert when something goes wrong.
* Order commits logically.

When working locally, it's OK if your branch history is not perfect, but that should be cleaned up before pushing upstream.

### Messages

Follow [Conventional Commits](https://www.conventionalcommits.org). If the repo uses [Kathari](), you can just run `yarn run cz` and follow the prompts to craft a valid message.

{% hint style="info" %}
Note that all the words in a commit message are in **present tense** except for the first word in the footer, e.g. Closes, Fixes, etc.
{% endhint %}

## Merging

{% hint style="danger" %}
Branches that are used by CI/CD processes, like `develop` and `master` should never have their history rewritten.
{% endhint %}

Before merging:

* [x] Make sure the branch you are merging is fresh by rebasing it into the target branch.
* [x] Verify that all commits adhere to this guide, otherwise, fix them.
* [x] Wait for all CI/CD processes to give the green light.

{% hint style="info" %}
Always alert other people who are working on a branch when you are about to rewrite its history.
{% endhint %}

## Misc. Tips

{% hint style="danger" %}
Test before you push. Do not push half-done work.
{% endhint %}

{% hint style="info" %}
Use lightweight tags to bookmark commits for future reference.
{% endhint %}

{% hint style="success" %}
Keep repos in good shape by performing maintenance tasks from time to time:

* `git-gc`
* `git-prune`
* `git-fsck`
{% endhint %}



