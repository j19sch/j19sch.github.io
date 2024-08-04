<!--
.. title: Optimizing for moments of discovery
.. slug: optimizing-for-moments-of-discovery
.. date: 2024-08-03
.. category: 
.. tags: exploratory testing, quality engineering
.. type: text
-->

ToDo:
- remove file with previous version
- link to EZ's NewCrafts talk

goal of this post: get concrete after previous more philosophical post

---

# from previous posts

> A requirement is an answer, a “should”. It serves the purpose of design. A test case is a question, a “what if?”. It serves the purpose of evaluation.

> The value of distinguishing test cases from requirements by their moment of discovery, lies in making us aware of that moment - and where that moment fits in our processes. It lets us notice, when we discover something we expect of our software, if we discover it either as a requirement or as a test case, as part of design or as part of testing.

> And once we notice this moment, this distinction, we can reflect on it. We have a new angle to explore how we might get better at either type of discovery. We can decide if we want to move that moment of discovery, either earlier or later. And it lets us ask the question: should some discoveries be moved to other side of that moment?

---

# intro
refer to previous post

> The difference between a requirement and a test case is the moment of discovery.

previous post theoretical

this one practical:
- be intentional about exploratory testing
- optimize for moments of discovery


What's my point?
- ET is key to good testing, because not based on translated requirements
	- so better be intentional
	- better be good at it
- optimizing for moments of discovery
	- thin vertical slices, JIT design and test



- (old) optimizing the moment
	- thin vertical slices FTW -> serves both, JIT design and test
	- what about req eng later?
	- should have been requirement or test
	- should have been sooner or later
	- ET early because for some stuff it's more effective than req eng
	- continuous ET and req eng, instead of all design upfront, ET at the end


# Be intentional about exploratory testing

In the previous post I [distinguished](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery#translated-requirements) test cases that are translated requirements from ones that aren't. This is basically something I learned from [James Lyndsay](https://www.workroom-productions.com/).

As he describes in *["Why Exploration has a Place in any Strategy"](https://www.workroom-productions.com/why-exploration-has-a-place-in-any-strategy/)*:

> Some tests are designed to find risks. They're made on-the-fly and run once. Some are designed to tell us about retained value. They're made once, and run forever after. You need *both*: they tell you different things.

The tests with a focus on value are prescribed (as in: written before), they are based on requirements, on things we know we want. The tests with a focus on value are exploratory, they are based on our decisions in the moment, we look for surprises and decide how we feel about those surprises.



---

If both kinds of testing, prescribed and exploratory, are important, then why am I focusing on the exploratory part? There are three reasons:
1. there are still a lot of misconceptions about what exploratory testing is
1. there are a lot of misconceptions about how exploratory testing relates to scripted and automated testing
1. a lot of exploratory testing is happening implicitly -> carries misconceptions with it

---


## What is exploratory testing?

During her [live exploratory testing session](https://ncrafts.io/speaker/elizabethzagroba)[^1] at [NewCrafts](https://ncrafts.io/) 2024, Elizabeth Zagroba adlibbed the following definition:

> Exploratory testing is when you're testing and also thinking about what you're doing, and whether it matters.

[^1]: Unfortunately the video is currently unavailable, as NewCrafts is migrating their videos from Vimeo to Youtube.

This continuous reflection on what you're doing is a key component of exploratory testing. You're interacting with an application, discovering things, and making decisions on what to do next based on those discoveries.

Or as [Maaret Pyhäjärvi](https://maaretp.com/) summarizes:

> Exploratory testing is an approach to testing that centers learning. Test design and test execution form an inseparable pair where the application and feature we are testing is our external imagination. - [*"Exploratory Testing Foundations"*](https://dev.to/maaretp/exploratory-testing-foundations-4lb3)


Some people might read these (or other) definitions and walk away with the following picture of exploratory testing: exploratory testing is someone clicking around in the application, hoping to discover a bug. While that technically is exploratory testing, it's not a very effective form of it.

Let's take a look at the three main things missing from that picture of exploratory testing:
- the learned skill
- the layers of the stack
- the tooling and automation


### Exploratory testing is a learned skill

For decades testers have been collecting heuristics that have helped them guide their testing:
- Test Heuristics Cheat Sheet by Elisabeth Hendrickson, https://www.ministryoftesting.com/articles/test-heuristics-cheat-sheet
- the product elements of RST's Heuristic Test Strategy Model, https://www.satisfice.com/download/heuristic-test-strategy-model
- FEW HICCUPS Michael Bolton https://developsense.com/blog/2012/07/few-hiccupps
- Microheuristics by Alex Schladebeck https://www.schladebeck.de/microheuristics/
- Analysis, Test Design, Test Execution Heuristics from The Little Black Book on Test Design, http://www.thetesteye.com/papers/TheLittleBlackBookOnTestDesign.pdf

Having these lists of heuristics is a great start, but applying them hinges on two skills: noticing what there is to notice, and choosing the right heuristic to apply. Neither can be done perfectly. You can't notice everything. You can't know for sure upfront what the right heuristic is.

But you can do these (noticing and deciding) rather well or rather poorly. And that's the invisible skill of exploratory testing. Invisible, because it's all in the mind of the person[^2] of doing exploratory testing. (One day I'll properly study Boyd's [OODA loop ](https://en.wikipedia.org/wiki/OODA_loop) and how it applies to exploratory testing.) And any skill can be practiced and refined. Exploratory testing is not just something some people do well.

[^2]: Or persons, plural, if you're doing ensemble testing.


### Exploratory testing can cover any and all layers of the stack

Exploratory testing can be done on any piece of the application. If you've ever looked at a unit test, said to yourself *"I wonder what this function does if I give it these parameters..."*, added a test with those parameters, and ran it, you have done exploratory testing.

Any way to interact with an application is valid to exploratory testing. Any inerface is fair game, so the code itself, APIs, CLIs, GUIs, config files, the database, etc.

And you can include as many or few layers of the stack as you want. Whether it's the whole stack, just the backed, the frontend with a mock service, etc.

Anything that helps you learn about the application and discover risk.


### Tooling and automation make exploratory testing more powerful

Tools [support, extend and/or amplify](link://slug/reflections-on-my-testing-manifesto#5-tools) our testing. This includes anything from a notebook, to browser dev tools, to an IDE, to test data generators, to code that interacts with the application in some way.

Again, aything that helps to learn, to make the application do interesting things.



## How does exploratory testing relate to scripted and automated testing?

To figure out the relation between exploratory testing and prescribed testing (test scripts and automation), we only need to go back to the start of this post. Prescribed tests are based on requirements. Exploratory testing is a way to discover additional requirements. Hence my statement that kicked off these blog posts: *"The difference between a test case and a requirement is the moment of discovery."*



the incorrect views:
- when time left
- domain experts
- test automation pyramid, aka sprinkled on top
- agile testing quadrants? kinda, quadrant 3


> We *need* exploratory tests. They're great. They tell us about risk - unexpected, unpredicted, emergent - that goes hand-in-hand with the system that has been delivered. Exploratory tests are immediate, of the moment. The risk is known - and you'll not need to test for it again until you've addressed it, and *written* a test to show you that it's gone. (James Lyndsay)


scripted and automated tests, prescribed tests, -> translated requirements
exploratory testing -> newly discovered requirements (good and bad surprises)

so exploratory testing is input for scripted and automated tests (one of the inputs)


also heard from Maaret, who has expounded(?) on that idea by focusing on how so many more things are output of learning, with learning including building, such as user stories
more stuff is output than you think - Maaret

segue into second part: ~optimizing for moments of discovery~ being intention about exploratory testing



## What you miss out on by keeping exploratory testing implicit

exploratory testing and automation start to feed into each other -> previous paragraphs


it's everywhere, it's fundamental, not "if time left"; RISKS!

noticing is a key skill in ET
doing is key, so brief and debrief are lacking -> leftovers?

happening implicitly anyway

how often do you look at the application, the code, the monitoring and it gives you an idea?


so be intentional about it
so not just when time left

Arguably the difference between good and bad testing is in the details:

- what do you notice while testing? seeing what actually is there
- what choices do you make to select your test data
- how many variations can you come up with, to try? -> "here is a rock? what can you do with it?"
- modelling the application
- how varied are your oracles
- using the application as your external imagination -> new ideas













---

---

---


# Optimize for moments of discovery -> part 3

thin vertical slices for richer exploration, for JIT design and test
as in elephant carpaccio (link to tag)

> "It is in the doing of the work that we discover the work that we must do. Doing exposes reality."
Woody Zuill, https://agilemaxims.com/

short feedback loop between design - build - test
mirrors: like ET is parallel design - execution - evaluation (check definition!)
"by treating test-related learning, test design, test execution, and test result interpretation as mutually supportive activities that run in parallel throughout the project" Kaner, https://kaner.com/?p=46

If I could tell you in detail what and how I would test upfront, I'd add those as requirements / acceptance criteria from the start. Then you could build it right/correct from the start, instead of having me test it afterwards. // if I can tell you what to test without exploring, it could have been a requirement => in link from ET part

<!-- is this just a post about why exploratory testing is important and how to get good at it? -->

<!--
	how does it tie in to the moment of discovery thing
	translated requirements vs ET
	moving the moment of discovery: should this have been a requirement? should this have been a test? how to get better at both? should we have required or tested this sooner or later?
-->

not shifting left because that's requirements engineering, both have their place
shifting left, what does it mean anyway?

The dividing line between what's a test case and a requirement is the question: is this input for creation or for evaluation? If it's for creation, it's a requirement; if it's for evaluation, it's a test case.

once there's a lot of requirements, it's hard to see the gaps -> testing requirements -> external imagination

there is more value in discovering test cases that are not requirements yet as early as possible
=> hence ET, product as external imagination, hence thin vertical slices for richer exploration

law of diminishing returns

just enough design, just enough testing
good enough for now, safe enough to try
architecture is decisions that are hard to change

how to get better
moving the moment of discovery, either earlier or later, move to other side?
Earlier exploratory testing is better, because earlier feedback on the thing itself

In a sense, requirements are dead. Requirements are answers (even if tenuous). Test cases are questions. The trick is to limit test cases to only those questions that can be answered by exploring / interacting with the code / the application. The rest can be a requirement.


---

end with reflection questions?

---

leftovers

The first kind of testing is single loop learning, the second kind is double loop learning. You're not just learning if the product behaves as expected. You're learning about the product and its requirements and how the two interrelate.

Exploratory testing is key / Being intentional about exploratory testing

Because not based on requirements. So if not doing ET, then missing out.

it's not requirement vs test, it's requirements vs exploratory testing
everyone does requirements (in some way), exploratory testing is still implicit, 'fringe', afterthought

everyone does design, requirements throughout, but not exploratory testing
or ET is the key part of testing, the easily missed part, the not-done-well part

it's done everywhere anyway, better to be intentional about it

All the surprises you didn't find and address, are likely to catch up to you some day. So best to find the most important ones in time.


All the surprises you didn't find and address, are likely to catch up to you some day. So best to find the most important ones in time.
