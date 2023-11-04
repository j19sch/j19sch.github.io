<!--
.. title: A good tester is all over the place
.. slug: a-good-tester-is-all-over-the-place
.. date: 2023-11-04
.. tags: quality engineering
.. category: quality engineering, management, software development, software testing, test management
.. link: 
.. description: 
.. type: text
-->

* --> Before I start this post, I shoud say that we use "tester" in [so many different ways](link://slug/tester-is-an-overloaded-variable), that there are so many different views about what good testing is, let alone what good software development looks like, that either I had to cut a lot of the nuance from this post, or I had to write an extremely long post with nuances stacked on top of nuances. I chose for the former approach.*

<!-- TEASER_END -->

# Testers do testing

Let's start with a straightforward statement: a tester tests. Then what is testing? I [still like the definition](link://slug/reflections-on-my-testing-manifesto) *"Testing is investigating in order to evaluate a product."* The most obvious thing to investigate, to test, is the code that has been written[^1]. The best way to do this, in my opinion, is through the combination of exploratory testing and test automation, i.e. what [Maaret Pyhäjärvi](https://maaretp.com/) has named ["contemporary exploratory testing"](https://www.youtube.com/watch?v=T_67oQrPZhQ).

[^1]: Which can take different forms: from investigating the code as code, to investigating (part of) the code as it runs, to investigating the code as a product.

These two aspects, the exploratory and the automation activities, are the most visible parts. They would yield very poor results, though, without good strategy, planning, and design of the testing. And the results would of be of little use without good test reporting.

While the above covers the core of what a tester does, there's more testing to do. I expect testers to also be involved in monitoring production, in attending to CI/CD pipelines, and to participate in refinement, design, and architecture.

So that's quite a wide range of activities. Luckily, yet also unluckily, they are not the only ones doing testing.


## But they're not the only ones testing

What's curious about testing, is that the tester is not the only one doing it.

I expect developers to test their own work. It cannot be the case that when you ask a developer "Is the code you just wrote good enough?", the reply is "I have no clue, ask a tester to look at it." And as to the other set of activities I mentioned - monitoring, pipelines, design - it's hard to imagine developers not also being involved in those.

So it seems there's nothing that distinguishes a tester from a programmer in the types of activities they do. A cynical conclusion from that could be that testers are programmers who aren't good enough at programming. They get to be second-tier developers, focusing on stuff that needs to happen, but is not programming.

I don't accept that cynical conclusion, though. I've seen plenty of testers bring great value to their team, because they bring something different.


## Yet they bring something different

As mentioned above, the unique value testers bring, is not in what they do. They should not be the only ones testing. The unique thing a tester (or at least a good tester) brings, is in how they do testing.

By being "a tester", they have the space to focus on testing. First of all, they can focus their professional development skills on this area. They can build and deepen their testing skills beyond a level that would make sense for non-testers.[^2] Secondly, throughout the development process, testers can take a testing stance. The can keep the question "How might this work? And how might it not?" front of mind, leaving the question "How can I build this?" more in the background.

[^2]: If you're not getting that from your testers, there's an interesting conversation to be had.


## Please point at where the testing happens

All of this means, that it's hard to point in a meaningful way where testing happens. There's no single activity in which all the testing is concentrated. There isn't a single role either. Testing - as in: investigating in order to evaluate a product - happens everywhere, all the time, by everyone.[^3]

[^3]: My favorite far-fetched example is a programmer's proprioception if they are hitting the right keys while writing code.

That is not to say that all of that testing will be great or even adequate. Some of it will be too shallow, or poorly done, or the best you could get from someone who lacks skill, has a bad day, or isn't provided with an environment to support their best.

It is to say that testers need to be all over the place, because that's where testing happens.

And it is to say that testers both need to claim and not claim ownership of testing. -> doing vs support testing




---

# what testers do

testing throughout the sw dev cycle
uniqueness is not in what testers do, but in their expertise / skill-level
	refinement, exploratory testing, test automation, monitoring
	next to skill, also critical mindset, critical distance => allowed to focus on "investigating in order to evaluate"

Programmers write code, business analyists gather requirements, product owners set priorities, ux designers design. Others might help out here and there, but it's clear who's in the lead. Yet, when you ask: "Who tests?" The answer should be: "Hopefully not just the tester!"

uniqueness is not in what testers do, but in their expertise / skill-level
	next to skill, also critical mindset, critical distance => allowed to focus on "investigating in order to evaluate"

# three balancing acts, not balancing act, continuous movement

doing testing yourself versus supporting testing by others
being embedded in a team vs being in a separate team
doing your job versus improving the system

continusously moving


# what does this mean for the role of tester?

position of testers is an unsolved problem in the industry
hat tip to everyone, testers and non-testers, who make it work regardless

personnaly changed my perception of myself
one way to look at myself is: tester
the other: developer who doesn't specialize in programming
claiming my place as a developer who doesn't specialize in programming
does require showing results / impact

I'm a developer who doesn't specialize in programming
I'm a developer who 'just' happens not to specialize in programming



---




# Testers do testing




## But they're not the only ones

But a tester can also do testing by looking at monitoring, attending to CI/CD pipelines, participating in refinement. And that still leaves out some crucial acitivities, such as test strategy and test reporting. And the things we expect from every team member, e.g. participate in the retrospective.

Testers roles and services: https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html




What's curious about testing, though, is that the tester is not the only one doing it. Programmers write code, business analyists gather requirements, product owners set priorities, ux designers design. Others might help out here and there, but it's clear who's in the lead. Yet, when you ask: "Who tests?" The answer should be: "Hopefully not just the tester!"



# A tester's role is dynamic along three axes

link to [quality engineer experience report](link://slug/im-a-quality-engineer-and-im-not-sure-how-i-feel-about-that)

Maaret: be like water, but sometimes be ice

## Doing testing yourself versus supporting testing by others

## Being in a separate team versus being embedded in a team

## Doing your job versus improving the system

## Working inside and outside of the existing structures

What all of these have in common: working inside and outside of the existing structures


# Closing thoughts

unsolved problem in software development

programmer who 'just' happens not to specialize in testing.

---

questions for the reader