<!--
.. title: Optimizing for moments of discovery
.. slug: optimizing-for-moments-of-discovery
.. date: 2024-08-03
.. category: 
.. tags: 
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

What's my point?
- ET is key because not based on requirements
- optimizing the moment
	- what about req eng later?
	- should have been requirement or test
	- should have been sooner or later
	- ET early because for some stuff it's more effective than req eng
	- continuous ET and req eng, instead of all design upfront, ET at the end
	- thin vertical slices FTW -> serves both, JIT design and test
- better get good at ET, be intentional


# Exploratory testing is key

In the previous post I distinguished test cases that are translated requirements from one that aren't.

As James Lyndsay explains it: the former are focused on value, the latter on risk. It makes sense to test the requirements. To confirm that our upfront, explicit requirements are met. That's not enough, however. We also have to look for surprises and decide how we feel about them. Exploratory testing is investigation and evaluation, all rolled into one.

https://www.workroom-productions.com/why-exploration-has-a-place-in-any-strategy/

The first kind of testing is single loop learning, the second kind is double loop learning. You're not just learning if the product behaves as expected. You're learning about the product and its requirements and how the two interrelate.

Or as Elizabeth Zagroba said at NewCrafts 2024:

> Exploratory testing is when you're testing and also thinking about what you're doing, and whether it matters.

https://ncrafts.io/speaker/elizabethzagroba no video, because migration to youtube

All the surprises you didn't find and address, are likely to catch up to you some day. So best to find the most important ones in time.

external imagination
more stuff is output than you think

In a sense, requirements are dead. Requirements are answers (even if tenuous). Test cases are questions. The trick is to limit test cases to only those questions that can be answered by exploring / interacting with the code / the application. The rest can be a requirement.


# Moving the moment of discovery

If I could tell you in detail what and how I would test upfront, I'd add those as requirements / acceptance criteria from the start. Then you could build it right/correct from the start, instead of having me test it afterwards. // if I can tell you what to test without exploring, it could have been a requirement

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


# Be intentional about your exploratory testing
it's done everywhere anyway, better to be intentional about it

Building exploratory testing skills

includes reading code and writing tests and building tools

is kind of like being intentional

- when
- who
- skills

doing is key, so brief and debrief are lacking

Arguably the difference between good and bad testing is in the details:

- what do you notice while testing? seeing what actually is there
- what choices do you make to select your test data
- how many variations can you come up with, to try? -> "here is a rock? what can you do with it?"
- modelling the application
- how varied are your oracles
- using the application as your external imagination -> new ideas