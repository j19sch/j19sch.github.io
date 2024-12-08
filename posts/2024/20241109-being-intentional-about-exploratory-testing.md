<!--
.. title: Being intentional about exploratory testing
.. slug: being-intentional-about-exploratory-testing
.. date: 2024-11-09
.. category: exploratory testing
.. tags: exploratory testing, quality engineering, software development, software testing,
.. type: text
.. description: Being intentional about exploratory testing, i.e. exploring and evaluating what you are building and what you have built throughout the development process, is a key skill in a high-performing team.
-->

*This is the second post in a (to be) three-part series about my statement "The difference between a test case and a requirement is the moment of discovery."*

In the previous post I [distinguished](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery#translated-requirements) test cases that are translated requirements from ones that aren't. This is something I learned from [James Lyndsay](https://www.workroom-productions.com/). As he describes in *["Why Exploration has a Place in any Strategy"](https://www.workroom-productions.com/why-exploration-has-a-place-in-any-strategy/)*:

> Some tests are designed to find risks. They're made on-the-fly and run once. Some are designed to tell us about retained value. They're made once, and run forever after. You need *both*: they tell you different things.

The tests with a focus on value are based on requirements, on things we know we want, they are prescribed (as in: written before). The tests with a focus on risks are exploratory, they are based on our decisions in the moment, we look for surprises and decide how we feel about those surprises.

One thing I've noticed through the years, is that a lot more exploratory testing is happening than we give credit for. It's hidden, a required but implicit part of the work. We do it, but we're not intentional about it.

Today I want to argue that it pays to be more intentional about exploratory testing. Before I get there, however, I want to explain what exploratory testing is, because there are still plenty of misconceptions going around.

<!-- TEASER_END -->

# What is exploratory testing?

During her [live exploratory testing session](https://ncrafts.io/speaker/elizabethzagroba)[^1] at [NewCrafts](https://ncrafts.io/) 2024, [Elizabeth Zagroba](https://elizabethzagroba.com/) ad-libbed the following definition:

> Exploratory testing is when you're testing and also thinking about what you're doing, and whether it matters.

[^1]: Unfortunately the video is currently unavailable, as [NewCrafts](https://ncrafts.io/) is migrating their videos from Vimeo [to Youtube](https://www.youtube.com/@NewCraftsConference/videos).

This continuous reflection on what you're doing is a key component of exploratory testing. You're interacting with an application, discovering things, and making decisions on what to do next based on those discoveries.

Or as [Maaret Pyhäjärvi](https://maaretp.com/) summarizes in her [*"Exploratory Testing Foundations"*](https://dev.to/maaretp/exploratory-testing-foundations-4lb3):

> Exploratory testing is an approach to testing that centers learning. Test design and test execution form an inseparable pair where the application and feature we are testing is our external imagination.


Some people might read these (or other) definitions and walk away with the following picture of exploratory testing: exploratory testing is someone clicking around in the application, hoping to discover a bug. While technically that is exploratory testing, it's not a very effective form of it.

There are two important things missing from that picture of exploratory testing:

- exploratory testing is a learned skill
- exploratory testing can be as 'technical' as you want

## Exploratory testing is a learned skill <a id="learned-skill" />

For decades testers have been collecting heuristics that have helped them guide their testing:

- [Test Heuristics Cheat Sheet](https://www.ministryoftesting.com/articles/test-heuristics-cheat-sheet) by Elisabeth Hendrickson
- the product elements of RST's [Heuristic Test Strategy Model](https://www.satisfice.com/download/heuristic-test-strategy-model)
- [FEW HICCUPS](https://developsense.com/blog/2012/07/few-hiccupps) Michael Bolton
- [Microheuristics](https://www.schladebeck.de/microheuristics/) by Alex Schladebeck
- Analysis, Test Design, and Test Execution Heuristics from [The Little Black Book on Test Design](http://www.thetesteye.com/papers/TheLittleBlackBookOnTestDesign.pdf)

Having these lists of heuristics is a great start, but applying them hinges on two skills: noticing what there is to notice, and choosing the right heuristic to apply. Neither can be done perfectly. You can't notice everything. You can't know upfront what the exact right heuristic is.

But you can do these (noticing and deciding) rather well or rather poorly. And that's the invisible skill of exploratory testing. Invisible, because it's all in the mind of the person doing the exploratory testing. And as any other skill, exploratory testing can be practiced and refined. It's not something some people just happen to do well, while others don't.


## Exploratory testing can be as 'technical' as you want

First off all, I thoroughly dislike how the word 'technical' has and is being used for gatekeeping, especially in testing. If you work in tech, in whatever role, you're technical. Period.

Similarly, exploratory testing is always technical. You're investigating and evaluating a tech product, how can it not be? And that gives you options.

Exploratory testing can be done on any piece of the application, anywhere in the stack. If you've ever looked at a function or at a unit test, and said to yourself *"I wonder what this function does if I give it these parameters..."*, added a test with those parameters, and ran it, you have done exploratory testing.

So you can include or exclude as many or few layers of the stack as you want. You can test a single function, the whole stack, just the backend, the frontend with a mock service, etc.

Also, any way to interact with any part(s) of the application is a valid way of doing exploratory testing. The code itself, APIs, CLIs, GUIs, config files, the database, etc. It's all fair game.

So how can exploratory testing not be technical?


# How does exploratory testing relate to prescribed testing?

Exploratory testing is about learning and discovery. Prescribed tests (whether automated or not) are built based on that learning. Which is why in the [previous post of this series](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery) I stated: *"The difference between a test case and a requirement is the moment of discovery."* We discover things through exploratory testing and through requirements engineering. Requirements and prescribed tests (test cases) are the outputs of those discoveries.

As [Woody Zuill](https://woodyzuill.com/) states in one of [his Agile Maxims](https://agilemaxims.com/
):

> It is in the doing of the work that we discover the work that we must do. Doing exposes reality.

Building and investigating what we have built, is key to discovering what it is that we should build. That investigation is exploratory testing. And once we know a little more about what we should build, it's a good idea to capture what we have learned. Prescribed tests, especially when automated and running in a pipeline, are a great way to do so.

As James Lyndsay wrote in ["Why Exploration has a Place in any Strategy"](https://www.workroom-productions.com/why-exploration-has-a-place-in-any-strategy/):

> We *need* exploratory tests. They're great. They tell us about risk - unexpected, unpredicted, emergent - that goes hand-in-hand with the system that has been delivered. Exploratory tests are immediate, of the moment. The risk is known - and you'll not need to test for it again until you've addressed it, and *written* a test to show you that it's gone.

And [Maaret Pyhäjärvi](https://maaretp.com/) has been saying the same. In [contemporary exploratory testing](https://www.getxray.app/blog/contemporary-exploratory-testing-podcast-highlights) exploration and automation go hand-in-hand. And test cases, whether they are executable (i.e. automated) or not, are the output of exploratory testing.


# Being intentional about exploratory testing

By now you may have realized that the question is not whether you do or don't do exploratory testing. You are doing it already, whether you explicitly label it as such or not.

The question is if you're being intentional about it.

Are you intentional about the when? Doing exploratory testing throughout the whole development process: designing, building, testing, and monitoring? And are you intentional about the what? What is working for you during exploratory testing and what isn't? How can you get even better at it?

In my experience, teams that are intentional about exploratory testing, that do regularly explore what the are building and what they have built, tend to outperform those that don't.
