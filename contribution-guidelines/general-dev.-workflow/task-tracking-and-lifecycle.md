---
description: Our methodology for keeping track of development work.
---

# Task Tracking & Lifecycle

## All in Github

{% hint style="info" %}
See [Git Code Style & Guidelines](../code-style-and-guidelines/git.md) for our message and branch names style and guidelines.
{% endhint %}

We try to keep the number of tools we use to a minimum for simplicity and ease of on-boarding. The new features of Github make it possible to keep most of the project management next to the code, and this is our approach:

| Issues                                                  | Projects                               | Milestones                                             |
| ------------------------------------------------------- | -------------------------------------- | ------------------------------------------------------ |
| Reference a specific task and keep track of its status. | Reference a long term project or goal. | Are used to group issues into time-controlled sprints. |

## Labels for Days

We also have a very comprehensive set of labels that can be automatically added to a repo using [Kathari](broken-reference/). It's important that all issues and pull requests have a priority, status, and type, and that they keep track of who is working and who is reviewing, if anyone.

### **Optional**

* duplicate 2️⃣ - Is a duplicate.
* starter 🍼 - Good for new contributors.

### **Priority**

* **Critical 🔥** - Mission critical.
* **High** - Top of to-do list.
* **Low** - Bottom of to-do list.
* **Medium** - Somewhere in the middle of to-do list.

### Status

* **Abandoned** - The assigned contributor gave up.
* **Available** - Open for anyone to work on.
* **Blocked** - Blocked by another issue.
* **In Progress** - Someone is already working on it.
* **On Hold** - Purposely paused.
* **Proposal** - Don't work on it until accepted.
* **Review Needed** - Pending reviews.

### Type

* **Bug 🐛** - Bugs.
* **Documentation 📚** - Documentation work.
* **Enhancement ✨** - Enhancements.
* **Maintenance 🚧** - Chores.
* **Question ❔** - Queries about the project.

## Lifecycle

The lifecycle of a task goes like this:

{% hint style="info" %}
We don't have a complicated issue or pull request template, we just ask for common sense and for all necessary information.
{% endhint %}

1. An issue is raised with the description of what needs to be done.
2. Discussion takes place and someone is assigned to the issue.
3. The issue is added to a project and/or milestone, if applicable.
4. The assignee branches off `develop` to work and submits a pull request when ready.
5. Our CI/CD process lints, formats, and tests the code.
6. The pull request is merged after all the changes are reviewed and accepted, and any requested changes are made.
