<!--
.. title: A backlog item is a backlog item is a backlog item
.. slug: a-backlog-item-is-a-backlog-item
.. date: 2023-03-18 10:11:25 UTC+01:00
.. tags: work management, backlog, bugs, tech debt, agile
.. category: work management
.. link: 
.. description: 
.. type: text
-->

maintenance or tech debt?

---

Originally Scrum was very much about *"You tell us what needs building. We'll decide how we build it and how soon we'll deliver."*[^1] I've never seen that version of Scrum. The version I have seen, has a product manager try to get as many features into a sprint as reasonably possible - for varying degrees of reasonable. This comes at the expense of maintenance work, such as keeping libraries up-to-date or removing technical debt. And it incentivises the team to cut corners on features, to not leave code in a better state than they found it, to not fix smaller bugs and instead log them somewhere for later.

[^1]: See for examples [this Twitter thread](https://threadreaderapp.com/thread/1405184303126953987.html) by Alistair Cockburn about Scrum's anti-management position and sprint commitments.

One solution I see to this problem, is to put an engineering manager fully in charge of the team. The product manager prioritizes the features. The engineering manager prioritizes the full scope of work for the team. That's not a simple change to pull off, however.

Another solution might be to change the way we use our backlogs. If a product manager gets to prioritize all the work, and the tool they use is a backlog, then we should make sure that all the work[^2] is in the backlog: features, bugs, and technical debt.

[^2]: Or rather, all the work that's relevant within a relatively short horizon. The shorter the horizon, the smaller the backlog, the easier it is to manage.

<!-- TEASER_END -->

*Sidenote:* A solution I don't believe in is that engineers should learn to have better conversations with their product manager or product owner. That puts the responsibility solely on one party, the engineers, blaming them for being poor communicators and for not having a formula that converts engineering value to business value. It puts product management in a position of power-over instead of power-with engineering, where any conversation about what to work on, needs to happen on product management terms.



# Features

If you have a backlog, it already contains features. So no need to change anything here. You could argue - as I did in [*"Our work management tools are limiting our imagination"*](link://slug/our-work-management-tools-are-limiting-our-imagination) - that there might be better ways to manage work than having features in a backlog. That's not what this post is about. The assumption is that you have a backlog, owned by a product manager or product owner, containing the upcoming work for the team.



# Bugs

Putting bugs in your backlog is a tricky proposition, because it becomes the default action for bugs that are not obviously urgent. So before you know it, you have a bunch of bugs in your backlog and all of them feel kind of important but then again, also not that important. The number of bugs grows, some of them become outdated, it's too much work to re-triage them all again, and now what?

A solution to this problem is to first ask: Should we fix this immediately? With immediately meaning either that someone drops what they're doing and starts fixing it right away, or that someone wraps up what they're doing and then picks up the fix. For a bug in a story that's in developement, in most cases the answer to "Should we fix this right now?" should be "Yes." Fix it now and you'll never have to think about it again. For other bugs, e.g. based on a support ticket, the answer will be "yes" less often, because they're not related to the work the team is doing at that moment.

If you decide to answer the question of fixing the issue immediately with "no", it's important to be very clear what that means. Often that "no" seems to be taken as *"Good thing we logged it, so at some point in the future we can get back to it and fix it."* While that comes from a place of good intentions, I think there's a better way to look at that "no". By not fixing it right away, it becomes one of many items in the prioritization cycle, where it might never get enough priority to actually get picked up. So that "no" means accepting the issue might not ever get fixed at all.

That leads us to the third option of dealing with issues, simply forgetting about them. You're not fixing the issue immediately. You're not fixing it soon, so it shouldn't get a spot in the backlog. Then don't weigh yourself down by keeping track of them, let it go.[^3] And for those contexts in which there is value in logging all bugs, whether you will fix them or not, do log them, but not in your backlog. Record them somewhere else.

[^3]: Sometimes a cheap way to log a bug is adding an automated test that captures the bug's behavior. Do make sure it's not just as easy to also fix the bug, though.


# Technical debt and maintenance

"Technical debt" has many different definitions, with people disagreeing over which are the correct ones. In this post I'm using the term in its more general sense: "tech stuff that's making us slower than we could be". A related type of work is maintenance work, such as keeping dependencies up-to-date. For the purpose of this post, they both for the third category of backlog items, all the work of which your engineers are the main users and stakeholders.[^4]

[^4]: I suppose that makes compliance-related work either features or bugs?

While features and bugs tend to get added to the backlog, technical debt and maintenance usually don't. Or at least not in the same way, the bar seems to be significantly higher. There's a reluctance and they only get added to the backlog when there's really no other choice. And something I have yet to see, is a team consciously incurring some technical debt and immediately adding an item to the backlog to pay off that debt.

So what you tend to end up with is a product manager or product owner with an incomplete view of technical debt and maintenance work, because of two reasons:

1. They never interact with the codebase that lets them experience how tech debt slows down the work. It's more an annoying fact-of-life in software developmentthat explains why things take longer than anticipated.
1. The tool they use to manage the priorities, the backlog, is 'complete' when it comes to features and bugs, but not when it comes to technical debt and maintenance.

The first of these is definitely worth doing something about, e.g. through ensemble programming (also known as mob programming). A way to address the second one is to add technical debt and maintenance to the backlog in exactly the same way that features and bugs are. Scrolling through the backlog should give an accurate picture of the actual ratios of the three types of work. Make all the work visible. 



# All backlog items are equal

Features, bugs, and maintenance all are things we could do to increase the value of the product. (Or at least, we believe they would.) In that sense, from a work management perspective they are the same kind of thing. They are all backlog items. Work you intend to pick up soon.

If you want to, you can give them different labels, but I think there's a misleading aspect to doing so. At what point does a bug become a feature? A wrong calculation is clearly a bug. But what about supporting part of a process better? And why do we treat the people working on the system, as second-rate users? Why are the features and bugs they care about, treated as second-class citizens compared to those of other users?

Hence my proposal for a simple experiment. If you have a product manager who gets to make all the priority decisions about the work, then put all the work in the backlog: features, bugs, and maintenance. Make it visible. And if someone complains this makes the backlog too large, then have a conversation about what can be thrown out. But at least you'll start that conversation with a more complete picture of the work that could be done to increase the value of the product.

---


the are the same: backlog item
they are different: add pos. value, remove neg. value, improve dev experience

---

- keep backlogs as small as possible
- add all potential things we can do to increase the value of the product

---


While my idea is inspired by "let's log all the things in the backlog".
What if tech debt is logged in backlog like bugs? But then also same applies: now - log - forget.

I've seen too many teams where the product owner/product manager makes all the decisions about what work is done and what work is not. Response to that is usually "learn to have better conversations with your PO/PM" instead of putting an engineering manager in charge of the engineering team. Given that situation, I think putting tech debt in the backlog would help with visibility.

Backlog items, whether they are features, bugs or technical debt, are all potential things we can do to increase the value of the product.

So you might label them differently, but in the end they are all the same thing: a backlog item. things that might add value to the product /  things that we expext will add value to the product / will increate the value of the product

Whoever gets to prioritize all the work, benefits from having visibility on all the work.



---

## Thoughts from other people

This blog post started as a [question on Mastodon](https://chaos.social/@joeposaurus/110031968940811638):

> "What if you started to log technical debt as bugs in Jira?"

In response, [Krys](https://chaos.social/@krys@spore.social) said:

> "I fear relabeling would only reinforce everyone’s troublesome view of the PO  being the teams boss and having authority/obligation to micromanage their workday instead of demanding technical excellency from the team while trusting them to know best how to get that"

[Markus Tacker](https://chaos.social/@coderbyheart) said:
> "Nothing. Technical debt is valid implementation. As long as developers do not get permission (or sense of urgency) to change it, it will get ignored. Work on providing the resources needed to address it instead."

> "Tech debt impacts the ability to deliver new features. And that's why it does not belong in the backlog. Only features do. If feature backlog is empty, no need to address tech debt. If feature backlog keeps growing: fix tech debt."

[Zebulon](https://chaos.social/@zebulon@mas.to) shared a link to Chelsea Troy's [*"Stop saying 'technical debt'"*](https://stackoverflow.blog/2023/02/27/stop-saying-technical-debt/).

[Willem van den Ende](https://chaos.social/@mostalive@mastodon.social) shared his article [*"Product Hurricane Maps to take into account tech debt when roadmapping"*](https://www.qwan.eu/2022/03/29/product-hurricane-map.html).
