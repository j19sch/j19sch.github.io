<!--
.. title: Being intentional about exploratory testing
.. slug: being-intentional-about-exploratory-testing
.. date: 2024-09-08
.. category: 
.. tags: exploratory testing, quality engineering
.. type: text
.. description: todo
-->

ToDo:
- remove file with previous version
- link to EZ's NewCrafts talk
- update title etc
- save text for next post
- link from "what do you fix" to this post

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

*This is the second post in a (to be) three-part series about my statement "The difference between a test case and a requirement is the moment of discovery."*

In the previous post I [distinguished](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery#translated-requirements) test cases that are translated requirements from ones that aren't. This is basically something I learned from [James Lyndsay](https://www.workroom-productions.com/). As he describes in *["Why Exploration has a Place in any Strategy"](https://www.workroom-productions.com/why-exploration-has-a-place-in-any-strategy/)*:

> "Some tests are designed to find risks. They're made on-the-fly and run once. Some are designed to tell us about retained value. They're made once, and run forever after. You need *both*: they tell you different things."

The tests with a focus on value are based on requirements, on things we know we want, they are prescribed (as in: written before). The tests with a focus on value are exploratory, they are based on our decisions in the moment, we look for surprises and decide how we feel about those surprises.

If both of these kinds of testing, prescribed and exploratory, are important, then why am I focusing on this post on the exploratory part?

There are three reasons:

1. there are still a lot of misconceptions about what exploratory testing is
1. there are still a lot of misconceptions about how explorarory testing relates to prescribed testing
1. there's a lot of hidden, implicit exploratory testing that could deliver more value

<!-- TEASER_END -->

## What is exploratory testing?

During her [live exploratory testing session](https://ncrafts.io/speaker/elizabethzagroba)[^1] at [NewCrafts](https://ncrafts.io/) 2024, [Elizabeth Zagroba](https://elizabethzagroba.com/) adlibbed the following definition:

> Exploratory testing is when you're testing and also thinking about what you're doing, and whether it matters.

[^1]: Unfortunately the video is currently unavailable, as NewCrafts is migrating their videos from Vimeo to Youtube.

This continuous reflection on what you're doing is a key component of exploratory testing. You're interacting with an application, discovering things, and making decisions on what to do next based on those discoveries.

Or as [Maaret Pyhäjärvi](https://maaretp.com/) summarizes in her [*"Exploratory Testing Foundations"*](https://dev.to/maaretp/exploratory-testing-foundations-4lb3):

> Exploratory testing is an approach to testing that centers learning. Test design and test execution form an inseparable pair where the application and feature we are testing is our external imagination.


Some people might read these (or other) definitions and walk away with the following picture of exploratory testing: exploratory testing is someone clicking around in the application, hoping to discover a bug. While technically that is exploratory testing, it's not a very effective form of it.

There are two important things missing from that picture of exploratory testing:

- exploratory testing is a learned skill
- exploratory testing can be as 'technical' as you want

### Exploratory testing is a learned skill

For decades testers have been collecting heuristics that have helped them guide their testing:

- [Test Heuristics Cheat Sheet](https://www.ministryoftesting.com/articles/test-heuristics-cheat-sheet) by Elisabeth Hendrickson
- the product elements of RST's [Heuristic Test Strategy Mode](https://www.satisfice.com/download/heuristic-test-strategy-model)l
- [FEW HICCUPS](https://developsense.com/blog/2012/07/few-hiccupps) Michael Bolton
- [Microheuristics](https://www.schladebeck.de/microheuristics/) by Alex Schladebeck
- Analysis, Test Design, and Test Execution Heuristics from [The Little Black Book on Test Design](http://www.thetesteye.com/papers/TheLittleBlackBookOnTestDesign.pdf)

Having these lists of heuristics is a great start, but applying them hinges on two skills: noticing what there is to notice, and choosing the right heuristic to apply. Neither can be done perfectly. You can't notice everything. You can't know for sure upfront what the right heuristic is.

But you can do these (noticing and deciding) rather well or rather poorly. And that's the invisible skill of exploratory testing. Invisible, because it's all in the mind of the person of doing exploratory testing.[^3] And as any other skill, exploratory testing can be practiced and refined. It's not something some people just happen to do well due to some innate ability.

[^3]: One day I'll properly study Boyd's [OODA loop ](https://en.wikipedia.org/wiki/OODA_loop) and how it applies to exploratory testing.


### Exploratory testing can be as 'technical' as you want

First off, I thoroughly dislike how the word 'technical' has and is being used for gatekeeping, especially in testing. If you work in tech, you're technical. Period.

Similarly, exploratory testing is always technical. You're investigating and evaluating a tech product, how can it not be? And that gives you options.

Exploratory testing can be done on any piece of the application, anywhere in the stack. If you've ever looked at a function or unit test, and said to yourself *"I wonder what this function does if I give it these parameters..."*, added a test with those parameters, and ran it, you have done exploratory testing.

You can include as many or few layers of the stack as you want. Whether it's the whole stack, just the backend, the frontend with a mock service, etc. Any way to interact with an application, any interface, is valid to exploratory testing. The code itself, APIs, CLIs, GUIs, config files, the database, etc.

This also means that tools are crucial to exploratory testing. [Tools support, extend and/or amplify](link://slug/reflections-on-my-testing-manifesto#5-tools) our testing. This includes anything from a notebook, to browser dev tools, to an IDE, to test data generators, to code that interacts with the application in some way.

Anything that helps you learn about the application is fair game in exploratory testing. How technical that testing is, depends on what it is you want to test and how you want to approach that.



## How does exploratory testing relate to prescribed / scripted and automated testing?

not separate

exploratory is learning, so input for presribed testing, and input for design and build
so how does it make sense to separate the three?


what are the miconceptions:

- exploratory testing is the cloud on top
- exploratory testing is after you've done the rest
- requirements are prescribed tests are input for building, not for learning
- exploratory and prescribed testing are two different things
	- not what James Lyndsay said
	- exploratory -> learning, prescribed -> confirming, change detection, check if still

better:

- prescribed tests as output of exploratory testing
- design and build and test go together ======> optimizing for moments of discovery, which is next post

so what is input and what is output

prescribed tests are output of learning, exploratory testing
-> link with previous post: what do you fix when you fix a test

still a lingering belief we can mostly specify software in advance, instead of having to discover as we go
	instead of write a bit, evaluate a bit

===> prescribed tests and requirements are ways to capture what we have learned so far; we learn through exploratory testing (in the broad sense)

==> so exploratory testing is input for scripted and automated tests (one of the inputs)

==> exploratory testing is learning, so what's the output of learning: test cases, test automation, user stories, docs

==> > "It is in the doing of the work that we discover the work that we must do. Doing exposes reality." Woody Zuill, https://agilemaxims.com/

==> we learn through building and investigating what we must build, so let's write down what we learned

This is not a new thought. As James Lyndsay wrote in ["Why Exploration has a Place in any Strategy"](https://www.workroom-productions.com/why-exploration-has-a-place-in-any-strategy/):

> We *need* exploratory tests. They're great. They tell us about risk - unexpected, unpredicted, emergent - that goes hand-in-hand with the system that has been delivered. Exploratory tests are immediate, of the moment. The risk is known - and you'll not need to test for it again until you've addressed it, and *written* a test to show you that it's gone.

And [Maaret Pyhäjärvi](https://maaretp.com/) has been saying the same. In [contemporary exploratory testing](https://www.getxray.app/blog/contemporary-exploratory-testing-podcast-highlights) exploration and automation go hand-in-hand. And test cases, whether they are executable (i.e. automated) or not, are the output of (exploratory) testing.

---


=> post starts with this in "Be intentional about exploratory testing"

To figure out the relation between exploratory testing and prescribed testing (test scripts and automation), we only need to go back to the start of this post. Prescribed tests are based on requirements. Exploratory testing is a way to discover additional requirements.

Arguably, exploratory testing is not only about discovering additional requirements. It's also about discovering in which way(s) the application inadvertently does not meet some explicit or implicit (because 'obvious') requirement. That leads to some interesting questions about where "design" ends and "build" starts. Is writing code the part where we build the software? Or is it creating the final and most-detailed design? It also leads to interesting quetsions about the relation between "design" and "build" on the one hand, and "test" on the other. Do we first design and build, and then test? Or are they interrelated and intertwined?

If you write code and momentarily forgot about a requirement, does your code meet the requirements?

To me this shows the problematic position of requirements. In many small ways we still seem to think it's possible that if you just write down what you want the software to do, it can be built, and then tested to see if it meets the requirements. That in essence, it's a mechanical, linear, algorithmical process. And sure we agree requirements can never be complete and unambiguous and ... but that's nuance to this belief at the core of it all: it is possible to sufficiently define a piece of software through requirements.
! lingering old beliefs!

This makes us see requirements and user stories and prescribed tests (both scripts as automation) as input - and sufficient input! - for other work. It's essentially still a waterfall.

Instead, we could put writing a bit of code and evaluating it at the center of what we do. And yes, it's probably a good idea to take some time to think for a bit in advance[^2] about what code you'll write. And think about what you're writing, as you write it. And think some more after as well. (We could even call (most of) this sort of thinking "testing".) And all of that thinking results in output. Code and requirements and test cases and automated tests. As we do and think, we learn things. And ideally, we capture what we learn in the most approriate way.

[^2]: That's another misconception about exploratory testing. That you have to immediately start interacting with what you're testing. This is not true. Taking time to think is as much part of exploratory testing as is interacting with what you're testing.

That was all a bit philosophical. What does this mean in practice?

=> https://visible-quality.blogspot.com/2024/08/explaining-exploratory-testing.html: a typical social agreement of how I work with an agile team

=> https://elizabethzagroba.com/posts/2024/08_17_exploratory_testing/: what and how


~Hence my statement that kicked off these blog posts: *"The difference between a test case and a requirement is the moment of discovery."*~



---


==> optimizing for moments of discovery


the incorrect views on exploratory testing:
- when time left
- domain experts
- test automation pyramid, aka sprinkled on top
- agile testing quadrants? kinda, quadrant 3



scripted and automated tests, prescribed tests, -> translated requirements
exploratory testing -> newly discovered requirements (good and bad surprises)

so exploratory testing is input for scripted and automated tests (one of the inputs)


also heard from Maaret, who has expounded(?) on that idea by focusing on how so many more things are output of learning, with learning including building, such as user stories
more stuff is output than you think - Maaret

segue into second part: ~optimizing for moments of discovery~ being intention about exploratory testing



## What you miss out on by keeping exploratory testing implicit // Being intentional about your exploratory testing

if exploratory testing is so important, there's good and bad news
it's important, because not doing it is deciding you don't need to discover additional requirements
arguably it's not about doing more of it, there's already so much of it happening, it's about being intentional about it en getting better at it

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

the skill is in the doing of ET, so pairing and ensembling with reflection/teaching/coaching is the way forward











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
