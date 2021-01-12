---
description: 'How we push new code to staging, production, and beyond.'
---

# Releases

## Branch Deploys

In an effort to keep everything as automated as possible, we have two main protected branches that get automatically deployed in most of our projects:

| `develop` | `master` |
| :--- | :--- |
| Deploys to a staging environment. | Deploys to a production environment. |

{% hint style="info" %}
Pull requests also get deploy previews when applicable.
{% endhint %}

## Version Bumps & Releasing

When a task is finished, it gets merged to `develop`. When `develop` is tested and ready to become a production release, the following process takes place:

1. We run [standard-version](https://github.com/conventional-changelog/standard-version) on `develop` and take advantage of our [Git](../code-style-and-guidelines/git.md) style conventions to automatically create or update a changelog and bump the version number following [semver](https://semver.org) guidelines.
2. We push and submit a pull request  to `master`.
3. We conduct one final review before merging and letting CI/CD take care of the rest.

