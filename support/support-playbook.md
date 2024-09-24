# Support Playbook
**🚧 In Progress 🚧**

## 👉 Start Here
This document is for *things that look broken* somewhere in the Kleros product ecosystem.

<center>
<img src="../.gitbook/assets/broken-icosahedron.png" width="400"/>
</center>

If you’re pretty sure you’ve found something that’s broken, please ask yourself...

###  🔔🗯 **Is this a *major* issue that needs to be resolved in 24 hours or less?** 
If so, follow the steps  in the [Major Issues section below](#major-issues).

Examples:
* Any **downtime in vital fonctions** of the application.
* Any 🛡**security issue** that cannot wait another minute.
* An issue putting the **Kleros reputation** at major risk.


### 🔕💬 **Is this something that can be addressed on a longer timeline?** 
If so, follow the steps in the [Everything Else section below](#everything-else).


## 🚨 Major Issues

### 🛡 Security Issues
Please refer to the [Security Disclosure page](../contribution-guidelines/smart-contract-workflow/reporting-vulnerabilities.md).

### 🧯 Non-Security Issues

If you have found a major issue that needs to be resolved in **24 hours or less** (this should be rare), please:

1. Go to the [TODO] channel in the ***Product Support*** section/thread etc
2. Create a message with the following information: 
    * Where you found the issue,
    * Description of the behavior, step-by-step instructions on how to recreate the issue,
    * User account information for any known impacted accounts,
    * Screenshots (if relevant),
    * Relevant device info (mobile/desktop, browser, etc).
3. Someone from the Team will respond to you ASAP to let you know that the issue has been seen. The Team member will pull in the relevant team members to begin working on the problem and provide updates in [TODO: public issue tracker?].

## 🐛 Everything Else 

If you have found an issue that does not need to be resolved immediately (this should be most things), please:

1. Go to the [TODO] channel in the ***Product Support*** section/thread for the product/protocol for which you need help:
    * Integrations & Developers
    * Court
    * Proof of Humanity
    * ...
2. Create a short descriptive title for the issue with the following information: 
    * Where you found the issue,
    * Description of the behavior, step-by-step instructions on how to recreate the issue,
    * User account information for any known impacted accounts,
    * Screenshots (if relevant),
    * Relevant device info (mobile/desktop, browser, etc).
5) The Product Owner will acknowledge seeing your tag within the next business day and add the issue to the backlog. They may ask follow-up questions as part of this process. Once in the backlog, the issue will be prioritized accordingly and the Product Owner will provide updates as appropriate. 

## 🚑 Support Service Levels

Support is provided by resources made available by the **Kleros Cooperative**.

### 👨‍⚕️ Playbook & Expectations
**🚧 In Progress 🚧**

|  Playbook                 | 🚨 Emergencies | 🐛 Everything Else |
| --- | --- | --- |
| **Support channel** | [TODO] <br/> `#emergency-support` | [TODO] <br/> `#dev-support` <br/> `#[product]-support` |
| **Monitored by** | Product Owner <br/>AND<br/> Engineers On-Call | Product Owner |
| **Triage and Prioritization** | Whoever sees the issue first begins work immediately | Wait for prioritization by Product Owner |
| **First response time**  | ASAP | Within 1 business day |
| **Expectations** | Issue is worked on until resolved, even outside of normal business hours | Issue is *not* worked on outside of normal business hours unless indicated otherwise
| **Escalation after** | 1 Hour | 5 days if stagnant |
| **Escalation channel** | Tag the `@TODO` team| Tag `@[Product]Owner` |

### 🌡 Useful Metrics
These metrics may be observed over different time periods (daily, weekly, monthly, quarterly, yearly).

* Satisfaction
* Average Issue Count
* Ticket Backlog
* First Response Time
* First Response Resolution Rate (for example a response pointing to a * solution documented in the [Support FAQ](./support-faq.md)).
* Average Response Time
* Number of Interactions per Issue
* Average Ticket Resolution Issue
* Issue Resolution Rate

For [more information on these metrics](https://blog.hubspot.com/service/customer-experience-metrics).

## 🧗‍♀️ Escalation Contacts

* Security Team: [Reporting Page](../contribution-guidelines/smart-contract-workflow/reporting-vulnerabilities.md)
* Developer Relations: Emmett (@TG)
* Product Owners
    * Court v1: [TODO (@TG)]
    * Court v2: [TODO (@TG)]
    * Curate: [TODO (@TG)]
    * Tokens: [TODO (@TG)]
    * Reality oracle: [TODO (@TG)]
    * Proof of Humanity v1: [TODO (@TG)]
    * Proof of Humanity v2: [TODO (@TG)]
    * Governor and Zodiac Reality: [TODO (@TG)]
    * Moderate: [TODO (@TG)]
    * Vea bridge: [TODO (@TG)]
    * Escrow: [TODO (@TG)]
    * Linguo: [TODO (@TG)]
    * Dispute Resolver: [TODO (@TG)]

## 🌿 Ticket Lifecyle

### 📝 From Issue Report to Ticket Creation

The relevant Team members are responsible for monitoring the issues reported in the Support communication channels/threads below according to the severity of the issue. As a general rule, *a ticket is created to track the issue*, it is then triaged and prioritized before being picked up a team member. This process is fast-tracked for emergencies.

### 🤝 Resolution

Once a ticket has been assigned or self-assigned, the assigned engineer is responsible for further ticket hygiene including:
* Keeping the ticket status up to date (In Progress, PR review, etc)
* Attaching relevant PRs.
* Staying focused on the ticket and completing in high priority.

If the assigned engineer does not finish their ticket before [TODO: rotating schedule for support duties?], they will either:
* Notify the Product Owner that they will stay with the ticket through completion, OR
* Document their notes and hand-off to the next on-call engineer.

### 🚦 Status Tracking
[TODO: public issue tracker?]

The following status markers are used:
* 🔴 Issue has been received & is being triaged
* ⭕️ Issue is on-going & being worked on
* 🟡 A fix has been provided for the issue and is awaiting confirmation/deployment
* 🟢 Issue is resolved

 
