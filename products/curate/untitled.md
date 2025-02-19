---
description: How to create Token Curated Lists using Kleros Curate
---

# Kleros Curate Tutorial

## Enter Kleros Curate - A.K.A  The TCR \(Token Curated Registry\) <a id="enter-kleros-curate-a-k-a-the-tcr-token-curated-registry-"></a>

Kleros Curate uses financial incentives to keep a list on topic. Would you post a scammy item if it cost you money? Would you challenge a listing if you could win money?

The answers to these questions from our data are, 'No, probably not' and 'Yes, sure!' respectively.

![](https://blog.kleros.io/content/images/2020/06/Curate_Key-Use-Cases.jpg)

These are the fundamentals of the curation system. On top lies a layer of ‘collective intelligence’ in the form of crowdsourced and incentivized jurors whose job it is to keep that list on point.

When a user submits an item to Curate, it is first vetted by a challenge period which allows anyone else to challenge that submission. If the submission isn’t challenged, it’s deemed legitimate and on topic, if it is, the challenged submission is sent to Kleros jurors to decide whether it is, or isn’t valid for the list in question.

When you submit something to eBay or make a post on Facebook, you don’t need a financial incentive, as those respective companies have plenty of their own to keep that list and its items on point. Facebook moderators are exposed to extreme content and are paid by Facebook to do so.

You the user pay Facebook with your personal data which is then in turn used to keep extreme content out of your feed.

When there is no centralized actor to do the dirty work, you need some incentivized actors to take over.

## Cool. Does all this fancy stuff work? <a id="cool-does-all-this-fancy-stuff-work"></a>

In short, yes.

We’ve had one of [our lists](http://tokens.kleros.io/) running for some time which is a collection of Ethereum ERC20 tokens that meet a certain predefined criteria \(which we call “The Policy”\) as curated by the decentralized community.

This particular list stipulates that each of the items \(in this case tokens\) conform to a predefined [criteria](https://cdn.kleros.link/ipfs/QmbqgkZoGu7jJ8nTqee4NypEhK7YVBEJJmPJbJxz8Bx8nY/t2cr-primary-doc.pdf).

You can see in the image below a clearly defined policy regarding item submissions to the list

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-05-29-at-16.28.05-1.png)

The image below is the end result of the process. A curated registry of tokens that fit the above criteria as decided by a decentralized community.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-05-29-at-16.44.43.png)

**Key Points:**

*  No centralized actors can delete or modify any of these items.
* Without consensus via both a challenge and subsequent case, a listing can not be removed by any one person.  
* Each submission ‘lives’ on-chain. Assuming Ethereum isn’t compromised, for better or worse the item is uncensorable.

The image below shows those submissions that didn’t make it to the list. They were rejected for not conforming to the lists criteria.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-05-29-at-16.46.12.png)

To interact with this list you must make a deposit \(or stake\) which acts as your financial incentive not to submit tokens with characteristics that do not meet the criteria \(or policy\) of that list.

**The Cryptoeconomics are in some respect** [**'Law'**](https://kleros.io/whitepaper_en.pdf) **here.**

## Blurb Over - Let’s Create a List <a id="blurb-over-let-s-create-a-list"></a>

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-10-at-17.18.23.png)

Upon landing on Curate, you will be greeted with a screen similar to the above. Initially, you will see a list of cards which are each lists of their own. This is the top level \(a list of lists if you will\) which can be related to the top level ‘Music’ category in the Amazon example. Below music, we had a tree-like structure of subgenres each pertaining to their own list.

The first thing we’re going to do is create a list ourselves. This involves deploying two smart contracts \(these are the inner logic and workings of the platform\) to the Ethereum blockchain.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-10-at-17.01.53.png)

Click ‘Create a List’ in the header which will direct you to the initial creation page

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-03-at-15.17.55.png)

* **Title**

Reasonably self explanatory, the title of your list. To illustrate in the simplest form, I chose something reasonably straightforward in Hiphop Legends.

* **Description**

A short write up of what your list is about.

* **Acceptance Criteria**

This field is a critical piece of information for the smooth operation of your list. The Primary Document \(or acceptance criteria\) is the document specifying what can and can't be accepted to the list.  

For our example Hip Hop Legends list, the criteria document is as follows:

* Accept if Gold or Platinum record selling artist
* Accept if famous before 2016
* Accept if &gt; 100k YouTube view on at least one song

**Rejection:**

* Reject if trap artist
* Reject if grime artist
* Reject if parody artist
* Reject if PG friendly lyrics
* **Item name**

This is the field in which you would choose the overall name for the items submitted to your list. In our case, an item \(or submission\) is ‘Hip Hop Legend’ which will be listed in the ‘Hip Hop Legends’ list.

The item could be Eminem, Tupac, Snoop Dogg, etc.

* **Slider**

The slider is the easiest way to set the parameters for your list. If you’re an advanced user, you can follow the instructions below.

The cheaper the ETH submission price, the more likely you will see submissions made as it’s less risky to do so. However, it’s also more likely to see malicious submissions due to the cheaper cost of doing so. The opposite is also true for high ETH deposit submissions. The higher they are, the less likely you will receive malicious entries, but fewer submitters may want to take the risk of submissions.

If you want to discuss more about this for your list, [contact us here](https://t.me/joinchat/GGUsLhwZj_-aa0SoQTBltA).

* **Court & Jurors**

Here, you will select which court the challenged submissions from your list will go to be resolved. Each court has differing arbitration costs which are correlated to the difficulty of the case in question.

If your list is of high value \(see the slider\) you may want to choose a higher cost court. If however, it’s a low cost list, you would probably want to use a far cheaper court. For most lists, we recommend using the ‘Curate’ court however, if your list is more complicated, feel free to contact us [here to ask](http://slack.kleros.io/).

### Advanced <a id="advanced"></a>

The advanced parameters are for power users looking to tweak deeper settings within the List builder. If you need more information on these variables, [click here](https://blog.kleros.io/choosing-parameters-in-kleros-curate/) for a detailed overview from our Research Lead, William George.

For now, here's a quick overview.  

* **Item Name**

What are the items you are submitting to this list? The example will pertain to certain high performance cars meeting the policy but it could also be a list of decentralized exchanges, the most valuable sneakers or highest valued \(in the eyes of the community\) crypto projects.

* **Submission Deposit**

This is the cost for a user to submit an item to your list in ETH. Remember, it’s a deposit stake so they will get it back if the submission is accepted.

* **Removal Deposit**

It’s possible that submissions make it on that may be subjective, somewhat borderline or adhering to an earlier set of criteria. If that’s the case, users can make an ETH deposit to remove a registered item on the list. Note, the item still has to go through a ‘challenge period’ and is not delisted immediately. It’s possible that jurors will rule that the removal request was not valid meaning the initial user who made it, would lose their deposit.

* **Challenge Submission Deposit.**

If a user makes a submission to a list that another user doesn’t believe meets the policy criteria, it can be challenged. A high challenge cost could make it less likely that items will be challenged however, a lower challenge cost could mean an increase in ‘bad challenges’. I.e, items that do merit acceptance to the list but are challenged otherwise.

* **Challenge Removal Deposit**

It is in fact possible to challenge a removal request which can be tweaked in this parameter. As an example:

An item that has previously been accepted to the list was subsequently challenged for removal by user A. User B doesn’t think it should be removed from the list and challenges User A.

Fill in all the parameters as you want and click next.

**Add Your Items**

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-12.13.01.png)

This screen lets you define your items, or fields that will be used on the list. You can add as many as you need.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-12.14.03.png)

Here, we can see only two separate fields were necessary for our simple Hip Hop Legends list.

We’ve called the first one ‘Name’, selected it as a text field and set ‘Index’ to on. The index button makes it possible for users to search based on that field. For example: If we submitted a Hip Hop Legend with the name ‘ Eminem’, users can search throughout the whole list just by searching for Eminem.

The second field is a simple image field allowing users to add a picture of their legend.

## Badge List Parameters <a id="badge-list-parameters"></a>

Badges allow your list to specify even more parameters which add ‘badges’ to certain submissions. This can create a tiered system in which an original submission is later ‘upgraded’ in its submission weight with further qualities.

As an example, we could add a ‘Grammy’ badge to our Hip Hop Legends list which specifies only submissions \(Hiphop Legends\) that have Grammy’s can apply for that badge.

Another example could be that of a ‘Platinum’ badge which specifies only submissions to list that have platinum selling records are allowed that badge.

We'll create a separate explainer for badges but if you want to add them and don't know how, just [ask us on Telegram](http://t.me/kleros).

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-12.15.07.png)

Once you’ve made it to the final screen, you’re now ready to deploy. You can also go back to previous screens and make sure all the information is correct.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-12.16.06.png)

If you’re happy with it, click Deploy!

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-12.16.24.png)

On doing so, you’ll be asked to pay the contract deployment fees \(both for the list and the badges. If you don’t need badges, that list is still available for use at a later date\).

Once you accept the Metamask transactions and pay the fees, your list will be deployed.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-12.27.49.png)

## Add Your List to The List of Lists <a id="add-your-list-to-the-list-of-lists"></a>

The List of Lists homepage. When you click 'Browse' you will instantly be directed to this page. 

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-11-at-17.47.46.png)

Once you've created your list it isn't automatically added to our Browser Registry. Your list is still fully usable but won't show up for users visiting the homepage of the Curate site.

Submitting your list to the list of lists requires similar actions as submitting an item did earlier.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-11-at-20.26.29.png)

Add your list to the 'List of lists' by clicking on the 'Submit List' button. You'll need to make a deposit confirming your list fits the criteria in the above image.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-11-at-21.36.39.png)

If accepted, your list will remain in The Registry indefinitely unless it is challenged at a later date. This may be due to the list going off topic or spammy for example. If a large amount of the listings no longer conform to the policy, that would be a reasonable challenge in this case.The current Curate homescreen showing The Registry \(List of Lists\) and some pending submissions. 

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-12-at-11.06.54.png)

## Submit <a id="submit"></a>

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-14.17.21.png)

Once your list has been deployed, you are ready to submit items. As you can see in the image above, our list has two submissions.

The first is not yet registered and the second has been challenged which replaces the original card with a ‘potentially offensive content’ placeholder which can be revealed by the user.

Click ‘Submit Hiphop Legend’ \(Remember that ‘Item Name’ field from the list creator? Here it is\).

### Make a Submission <a id="make-a-submission"></a>

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-03-at-17.39.15.png)

A Hip Hop Legend item ready to submit. Notice the deposit required is 0.075ETH. If the listing is accepted, you’ll get that back.

If it’s challenged, this deposit is used as part of the collateral used to pay jurors for the arbitration. You win, it’s returned, if you don’t, it’s lost.

### Challenge a Submission <a id="challenge-a-submission"></a>

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-14.17.57.png)

Select the listing you want to challenge and write a description of why you think it doesn’t belong on the list. This information will be sent to Kleros jurors who will make a decision on whether it makes it onto the list or not.

![](https://blog.kleros.io/content/images/2020/06/Screenshot-2020-06-02-at-14.18.37.png)

## Congratulations!  <a id="congratulations-"></a>

You have now learned how to take back control of your internet list creation.

Remember, what you create here can live forever on the Ethereum blockchain, use this power wisely to create uncensorable lists for the greater good of the community and the world as a whole.

