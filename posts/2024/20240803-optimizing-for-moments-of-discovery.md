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


# Exploratory testing is key / Being intentional about exploratory testing

Because not based on requirements. So if not doing ET, then missing out.

it's not requirement vs test, it's requirements vs exploratory testing
everyone does requirements (in some way), exploratory testing is still implicit, 'fringe', afterthought

everyone does design, requirements throughout, but not exploratory testing
or ET is the key part of testing, the easily missed part, the not-done-well part

it's done everywhere anyway, better to be intentional about it



In the previous post I distinguished test cases that are translated requirements from one that aren't.

As James Lyndsay explains it: the former are focused on value, the latter on risk. It makes sense to test the requirements. To confirm that our upfront, explicit requirements are met. That's not enough, however. We also have to look for surprises and decide how we feel about them. Exploratory testing is investigation and evaluation, all rolled into one.

https://www.workroom-productions.com/why-exploration-has-a-place-in-any-strategy/


Or as Elizabeth Zagroba said at NewCrafts 2024:

> Exploratory testing is when you're testing and also thinking about what you're doing, and whether it matters.

https://ncrafts.io/speaker/elizabethzagroba no video, because migration to youtube



All the surprises you didn't find and address, are likely to catch up to you some day. So best to find the most important ones in time.


external imagination (Maaret) -> What can I discover by interacting with it? from Five favourite testing questions, inc reference
> “Exploratory testing is an approach to testing that centers learning. Test design and test execution form an inseparable pair where the application and feature we are testing is our external imagination.” - “Exploratory Testing Foundations” by Maaret Pyhäjärvi

more stuff is output than you think


## it's better when it's intentional

happening implicitly anyway

how often do you look at the application, the code, the monitoring and it gives you an idea?


so be intentional about it
so not just when time left


## it's a skill
not clicking around

noticing is a key skill in ET
doing is key, so brief and debrief are lacking -> leftovers?

Arguably the difference between good and bad testing is in the details:

- what do you notice while testing? seeing what actually is there
- what choices do you make to select your test data
- how many variations can you come up with, to try? -> "here is a rock? what can you do with it?"
- modelling the application
- how varied are your oracles
- using the application as your external imagination -> new ideas


## it's full stack
not as-if-a-user
includes reading code and writing tests and building tools

## tooling supports, extends and/or amplifies
not no tools/automation
includes reading code and writing tests and building tools

> We do use a wide variety of tools to support, extend and amplify our testing.
Testing manifesto principle 5




# Optimizing for moments of discovery

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