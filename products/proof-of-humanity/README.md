---
description: A Sybil-resistant (=duplicate and bot-proof) registry of humans
---

# Proof of Humanity

👤 [Proof of Humanity App](https://proofofhumanity.id/)👤

![](../../.gitbook/assets/image%20%2823%29.png)

**Proof of Humanity** is a system combining social verification with video submission in order to create a Sybil-proof list of humans. It is meant to be used by individuals as a point-of-entry to a myriad of new use cases that require users to prove they are real humans and not duplicate/fake/bot accounts. It will be plugged into a variety of existing and new applications in need for such identity systems.

{% embed url="https://youtu.be/bVUGvCHd3w0" caption="" %}

Building this type of advanced identity registry is not an end in itself. It is a point-of-entry to a myriad of new use cases that require Sybil-resistance \(duplicate resistance\) and also to be plugged into a variety of existing and new applications in need for such identity systems. Let's browse through a non-exhaustive list of use cases that benefit from PoH.

{% page-ref page="proof-of-humanity-tutorial.md" %}

{% page-ref page="proof-humanity-tutorial-remove-and-challenge.md" %}

{% page-ref page="poh-faq.md" %}

## Proof of Humanity Use Cases <a id="proof-of-humanity-use-cases"></a>

#### Universal Basic Income <a id="universal-basic-income"></a>

Universal basic income \(UBI\) is a program for a periodic payment delivered to all individuals of a given population with no strings attached.

The Proof of Humanity registry technology enables a truly universal and fairer form of distribution for UBI projects as the only condition to receive it would be to be registered as a verified human.

A UBI project based on Proof of Humanity is already underway as a collaboration between Kleros and Democracy Earth.

Check out the [_announcement of the UBI token launch_](https://blog.kleros.io/proof-of-humanity-building-the-internet-of-humans/) to learn more about this.

#### Innovative DAO frameworks <a id="innovative-dao-frameworks"></a>

DAO frameworks and apps using the PoH registry to check the “humanity” of voters can experiment with truly democratic systems \(1 person = 1 vote\) and innovative preferential or quadratic voting features for which Sybil-resistance is required.

For example, the UBI DAO will be based on a governance system such as this one in order to better account for the voices of every community member. A similar system could be added as a plugin to common DAO tools such as Colony, Aragon, or DAOstack.

#### Better Funding Mechanisms <a id="better-funding-mechanisms"></a>

By extending the concept of Quadratic Voting to a funding mechanism, one can create new mechanisms for endogenous community formation. [Quadratic funding](https://wtfisqf.com/) is a design for philanthropic or publicly-funded seeding to allow \(near\) optimal provision of a decentralized, self-organizing ecosystem of public goods.

Citizens make public goods contributions to projects of value to them. The amount received by a project is proportional to the square of the sum of the square roots of contributions received.

This mechanism requires accounts to be Sybil-resistant as splitting one’s funding across multiple accounts increases the amount given to the target project. And Proof of Humanity allows for this Sybil-resistance. Proof of Humanity can be an important piece of infrastructure to bring into reality some of the innovative governance ideas explained in the book "Radical Markets". For example, quadratic voting.

#### Universal Identifiers and Self-Sovereign Identities <a id="universal-identifiers-and-self-sovereign-identities"></a>

Accounts created on PoH can directly be used as a universal login method: imagine dapps recognizing users automatically without the need for registration.

They can also be associated with other existing identity-adjacent systems such as 3box, ENS, or Serto.id to add Sybil-resistance to a user's profile.

#### Certification and Reputation Systems <a id="certification-and-reputation-systems"></a>

Various certifications or reputation points \(such as credit scoring\) could be added to PoH profiles.

Registered individuals would select the certifications they want to be made public. These could be confirmed by central entities or through a curated registry and displayed as a badge on the individual profile.

Certifications can include:

* Country of citizenship
* Degrees and professional certifications
* Skills \(for example an “experienced Solidity developer” badge which could be assessed by looking at open source code published by the individual\)

#### Sybil-Resistant Airdrops, Yield Farming, and NFT Distribution <a id="sybil-resistant-airdrops-yield-farming-and-nft-distribution"></a>

Airdrops are a popular way to distribute tokens. However, even when requiring different forms of identification \(telegram accounts, passports\), those airdrops were typically Sybil-attacked.

This led to a switch toward airdrops proportional to the user balance of a specific coin and lock drops \(where users need to lock some coins and receive tokens proportionally\). Those techniques, despite being Sybil-resistant, benefit users already having a high amount of crypto-holdings.

Proof Of Humanity will allow Sybil-resistant airdrops where participants will each be given the same amount of coins. The same method can be applied to Sybil-resistant yield-farming \(UBI token accrual, for example\); to ensure gift NFTs are not hoarded by a small minority, or to ensure free subscription schemes are not abused.

#### Anti-Spam Tools <a id="anti-spam-tools"></a>

Systems often use captchas \(small exercises testing user capacity to analyze an image or a sound which are hard to complete for AIs\) before allowing a user action in order to prevent spam.

These are wasting user time and do not prevent spam from a determined user who would be willing to spend the time to solve them \(or outsource the solution\). People in the PoH registry could be allowed a number of captcha-free interactions \(potentially high enough such that they never have to fill a captcha\).

Users spamming the system could get temporarily or permanently banned. And they would not be able to just create a new account in order to evade the ban.

#### Sidechains Secured by Proof-of-Humanity Consensus <a id="sidechains-secured-by-proof-of-humanity-consensus"></a>

The PoH registry could also be used to create a novel type of sidechain secured by Proof Of Identity with a “1 person = 1 vote” principle. This would assume an honest majority of humans in the registry and would work in a way similar to Proof Of Authority sidechains.

_**And many others such as social recovery, inheritance planning...**_

## The Next Level: Adding Privacy to Proof of Humanity <a id="the-next-level-adding-privacy-to-proof-of-humanity"></a>

All of these use cases can be improved upon by building new privacy layers on top of Proof of humanity that will enrich it with new capabilities. A key step for the future would be the creation of anonymous Sybil-resistant identities.

Identities stored in the PoH registry currently are not anonymous. It is however possible to create private Sybil-resistant identities from them. It can be done through the use of [Traceable Ring Signature](https://eprint.iacr.org/2006/389.pdf) or other using zero-knowledge proof mechanisms.

This would allow individuals to prove that they are humans and not bots while not revealing their identity. For example, certifications could be used in the context of privacy-preserving KYC by giving zero-knowledge proof showing that you are a citizen of a specific country or above a specific age without revealing who you are.

Another good use of anonymous identities is being able to prove one’s reputation or scoring without detailing the full history of actions made by one’s account in the past.

### Just Start Building! <a id="just-start-building-"></a>

Proof of Humanity is an open-source project. You are free to start integrating it into your project or building on top of it as soon as you are ready to do it.

**If you need some support, feel free to reach out to Cooperative Kleros at** [**contact@kleros.io**](mailto:contact@kleros.io)**,** [**Discord**](https://discord.gg/WfmtDdGe9p)**,** [**Telegram**](https://t.me/kleros)**.**

