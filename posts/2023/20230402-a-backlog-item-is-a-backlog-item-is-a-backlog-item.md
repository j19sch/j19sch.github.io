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

Originally Scrum was very much about *"You tell us what needs building. We'll decide how we build it and how soon we'll deliver."*[^1] I've never seen that version of Scrum. The version I have seen, has a product manager try to get as many features into a sprint as reasonably possible - for varying degrees of reasonable. This comes at the expense of maintenance work, such as keeping libraries up-to-date or removing technical debt. And it incentivises the team to cut corners on features: to not leave code in a better state than they found it, to not fix smaller bugs and instead log them somewhere.

[^1]: See for examples [this Twitter thread](https://threadreaderapp.com/thread/1405184303126953987.html) by Alistair Cockburn about Scrum's anti-management position and sprint commitment.

One solution I see to this problem, is to fully put an engineering manager in charge of the team. The product manager prioritizes the features. The engineering manager prioritizes the work the team does. That's not a simple change, however.

Another solution might be changing the way we use our backlogs. If a product manager gets to prioritize all the work, and the tool they use is a backlog, then we should make sure that all the work[^2] is in the backlog.

[^2]: Or rather, all the work relevant to a relatively short horizon. The shorter the horizon, the smaller the backlog, the easier it is to manage.

<!-- TEASER_END -->


# Features

If you have a backlog, it already contains features. So no need to change anything here. You could argue - as I did in [*"Our work management tools are limiting our imagination"*](link://slug/our-work-management-tools-are-limiting-our-imagination) - that there might be better ways to manage work than having features in a backlog. That's not in scope for this post. The assumption is that you have a backlog, owned by a product manager or owner, containing the upcoming work for the team.



# Bugs

Putting bugs in your backlog is a tricky proposition, because it becomes the default action for bugs that are not obviously urgent. So before you know it, you have a bunch of bugs in your backlog and all of them feel important but not that important. The number of bugs grows, some of them become outdated, it's too much work to re-triage them all again.

A solution to this problem is to first ask: Should we fix this immediately? With immediately meaning that either someone drops what they're doing and starts fixing, or that someone wraps up what they're doing and then picks up the fix. For a bug in a story that's in developement, in the majority of cases that answer to "Should we fix this right now?" should be "Yes." Fix it now and you'll never have to think about it again. For other bugs, e.g. based on a support ticket, the answer will be "yes" less often, because they're not related to the work the team is doing at that moment.

To make the decision to fix immediately or not well, it's important to realize the meaning of answering that question with "no". It means you accept that the issue might not get fixed ever. If we don't fix it right away, one option is to add it to the backlog. There might always be something more important in the backlog, then we never fix the issue. The other option is to forget about the whole thing. You won't fix this anytime soon, so it makes no sense to add it to the backlog.

I can imagine that in some contexts there's value in logging all bugs, whether you will fix them or not. In that case, do log those bugs, just don't do that in your backlog. Record them somewhere else.



# Maintenance and tech debt

What if tech debt is logged in backlog like bugs? But then also same applies: now - log - forget.

While my idea is inspired by "let's log all the things in the backlog".

Features and bugs tend to get added to the backlog, while tech debt doesn't. So the Product Manager has an incomplete view of the actual backlog. Fixing that could help in getting more priority for fixing tech debt.

I should also either not use "tech debt" or explicitly define how I use the term. Currently using it in the sloppy/vague sense of "tech stuff that's making us slower than we could be".

I've seen too many teams where the product owner/product manager makes all the decisions about what work is done and what work is not. Response to that is usually "learn to have better conversations with your PO/PM" instead of putting an engineering manager in charge of the engineering team.

Given that situation, I think putting tech debt in the backlog would help with visibility.


# All backlog items are equal

Backlog items, whether they are features, bugs or technical debt, are all potential things we can do to increase the value of the product.

So you might label them differently, but in the end they are all the same thing: a backlog item.

Whoever gets to prioritize all the work, benefits from having visibility on all the work.

---

## Some thoughts from other people

This blog post started as a [question on Mastodon](https://chaos.social/@joeposaurus/110031968940811638):

> "What if you started to log technical debt as bugs in Jira?"

In response, [Krys](https://chaos.social/@krys@spore.social) said:

> "I fear relabeling would only reinforce everyone’s troublesome view of the PO  being the teams boss and having authority/obligation to micromanage their workday instead of demanding technical excellency from the team while trusting them to know best how to get that"

[Markus Tacker](https://chaos.social/@coderbyheart) said:
> "Nothing. Technical debt is valid implementation. As long as developers do not get permission (or sense of urgency) to change it, it will get ignored. Work on providing the resources needed to address it instead."

> "Tech debt impacts the ability to deliver new features. And that's why it does not belong in the backlog. Only features do. If feature backlog is empty, no need to address tech debt. If feature backlog keeps growing: fix tech debt."

[Zebulon](https://chaos.social/@zebulon@mas.to) shared a link to Chelsea Troy's [*"Stop saying 'technical debt'"*](https://stackoverflow.blog/2023/02/27/stop-saying-technical-debt/).

[Willem van den Ende](https://chaos.social/@mostalive@mastodon.social) shared his article [*"Product Hurricane Maps to take into account tech debt when roadmapping"*](https://www.qwan.eu/2022/03/29/product-hurricane-map.html).
