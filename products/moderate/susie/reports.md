---
description: Who Moderates the moderators?
---

# Reports

As groups grow, so do their moderation problems. We're all busy people who don't have time to monitor groups 24/7. Moderators are asleep, and some jerk comes in and starts spamming all over the place? Moderators broke the rules? Who Moderates the moderators? Often users dispute moderation actions by admins and have no recourse.&#x20;

Susie enables crowd-sourced moderation using [Reality.eth and Kleros](../../oracle.md).

When users are reported, a question is created on Reality.Eth asking 'did the user break the rules?'. The question can be answered yes/no with a bond (1 DAI). Successful reports result in penalties (1 day, 10 days, 100 days, permaban).

<figure><img src="../../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

Answers to reports can be disputed, creating a case in the [Kleros Court](../../court/).

### User Commands

`/report` Reply to a message to report it

`/info` Returns active reports in a group

`/info` \<reply to user> Returns report history for user

### Admin Commands

`/adminreportable` Allows admins to be reported.

`/trial` Toggles a trial version of Susie where no penalties are enforced.
