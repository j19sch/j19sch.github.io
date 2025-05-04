<!--
.. title: Testing as three stages of enquiry
.. slug: 
.. date: 2025-05-12
.. category: 
.. tags: 
.. type: text
.. description: 
-->

The product of testing is information. (The product of good testing is actionable, relevant information, but that's another blog post.) So how does that information come about?

In my post ["The nine skills of exploratory testing"](link://slug/the-nine-skills-of-exploratory-testing) I wrote:

> As you explore, as you try things and notice how what you're testing responds, you build a model of how something might work. This kind of thinking is called [abduction](https://plato.stanford.edu/entries/abduction/) or abductive reasoning.

If you follow that link, you'll notice that it covers *"abduction in the modern sense"*, but that there's also a historical sense *"which had its origin in the work of Charles Sanders Peirce"*.

This historical sense is described in the supplement ["Peirce on Abduction"](https://plato.stanford.edu/entries/abduction/peirce.html), which refers to Fann 1970 for a *"a concise yet thorough account of the development of Peirce’s thoughts about abduction"*. So of course I bought that book, i.e. "Peirce's Theory of Abduction" by K. T. Fann. (I really like that this 63-page book that's over a 50 years old, apparantly is __the__ reference on this topic.)

And in that book I found something more interesting than just abduction: Peirce's three stages of inquiry. Or how the three phases of the methodology of science are abduction - deduction - induction. And it seem to me that testing works in a very similar way.[^1]

[^1]: I very deliberately wrote "in a very similar way". Because this blog post is no more than that: noticing an interesting similarity between what I understand of Peirce's thoughts based on Fann's book and what I believe about testing. If I'd want to make a stronger claim, e.g. about the similarities between testing and science, or about Peirce correctly describing the scientific method, I'd have to do a lot more reading and studying.


<!-- TEASER_END -->


# The three stages of inquiry

Let's look at each three of these in a little more detail and then in the next section how they might relate to testing

The first stage of inquiry, abduction, starts with noticing a surprising fact. Now an explanation is required. So we adopt a hypothesis as suggested by the facts. This hypothesis should be able to explain the observed facts. We adopt it on probation only. It must be tested.

Then we move on to the second stage, deduction. What are the necessary and probable consequences of the hypothesis? If our hypothesis is true, what else has to be true as well? Since we want to test our hypothesis, at least some of these consequences must be testable. (The hypothesis itself is not testable, since it's an explanation.)

Finally, we proceed to the third and last stage, induction. We test our hypothesis by running experiments. Either the consequences we deduced hold true, supporting our hypothesis. In that case we can either decide we're done or deduce additional consequences to test. Or, the consequences do not hold true, invalidating our hypothesis. In that case we return to the abduction stage, trying to come up with a new hypothesis.

Or as K.T. Fann summarizes in the Introduction of their book:

> Peirce conceived of the three kinds of reasoning as three stages of inquiry. Abduction invents or proposes an hypothesis; it is the initial proposal of an hypothesis on probation to account for the facts. Deduction explicates hypotheses, deducing from them the necessary consequences which may be tested. Induction consists in the process of testing hypotheses. Thus, "Abduction is the process of forming an explanatory hypothesis. It is the only logical operation which introduces any new ideas; for induction does nothing but determine a value, and deduction merely evolves the necessary consequences of a pure hypothesis" (5.171). *- Fann, p10*


# The three stages and testing

At a surface-level there's a clear similarity between the three stages of inquiry and testing. Abduction is coming up with test ideas, with things you want to test. Deduction is coming up with the actual tests informed by those test ideas. And induction is when you execute those tests. Or when a pipeline does it for you.


While I agree with that similarity, it's not very informative. To get somewhere interesting, we need to dig a little deeper.

The things:
- only exploratory testing counts as abduction
	- requirements engineering is abduction (arguably) -> my comment on shift left
- we don't have facts, we have behavior based on requirements
- how often do we need to run experiments? how many is enough?
- manual vs automated execution and the need for someone to look at the results (extended cognition)
	- Maaret said something about this: manual automation if someone has to run it -> Workflowy link
	- have said this (look at results) somewhere before, but where?
	- reflections on manifesto mentions extended cognition
	- test automation that needs to be run manually vs automated in a pipeline -> how often experiments
- affinity between man and nature -> affinity between tester and software behavior


## Only exploratory testing counts as abduction

Creating test cases based on requirements does not count as abduction. It's deduction. The hypothesis is already formed: the application behaves as per the requirement. So the steps left are deduction and induction. Deducing what you expect to be true if the hypothesis holds and inducing if it truly holds.

(Note that there's a difference between an expection being true and something happening. You might expect something to happen or expect something not to happen. Either can be tested if they hold to be true, if they result in something that can be observed.)

This is something I covered 10 years ago in ["The test case - an epistemological deconstruction".](link://slug/the-test-case-an-epistemological-deconstruction). There I warned against splitting strategy, tactics and operations in testing too far apart. Which is not dissimilar from abduction - deduction - induction. And I warned against how test cases break up the OODA-loop in testing. Even worse, it's often not a loop at all when using test cases. (OODA stands for Observe - Orient - Decide - Act, it's a model created by John Boyd.)

To re-iterate, when using test cases based on requirements, there is no abduction. There is no surprising fact leading to the need to form a hypothesis. We're not trying to understand the universe after it's been created. We have the universe and we have the blueprints. All that's left is verifying that the universe matches the blueprints. Any surprising fact we discover, is a bug. Something that does not meet requirements. (more on this later)

Now what if you identify a missing requirement? I'd say that that is abduction. You identified an additional thing about the behavior. It's not testing, though, as I argued in my post ... (which one? or was it a note?), it's requirements engineering. We can also see how the similarity with the three stages of inquire breaks down here. Inquiry starts from observing some behavior in the world. Requirements engineering is specifying how something should behave. So for the similarity to work, to be at least informative, abduction is more "are we discovering something new - even if it's only tentatively?" versus "are we encountering a surprising fact?"


## We don't have facts we have behavior based on requirements

The largest way the similarity breaks down is that we don't just have access to the behavior. We have access to information about the intended behavior. Both to the documents describing it and to the people implementing it. (Actually, we are some of the people implementing the behavior.) However, experience has shown that's not enough.

It is not possible to create the perfect requirements, implement those perfectly, and know with absolute certainty you have implemented it perfectly. And that's ignoring the whole platform you are relying on to do those things.

> Any sufficiently complex system is either incomplete or self-contradictory. (?) Gödel

That 'last' one is a funny one. Being able to specify and implement requirements perfectly, without the ability to know if you did so, is in a sense no better than not being able to do these things perfectly. Or is the knowing implicit in the perfection?

So again the breaks up our testing in two types, as I described in "Being intentional about exploratory testing". There's tests that look for value and there's tests that look for risk.

Limiting yourself to tests that look for value, that are based on deduction and induction, but skip the abduction, "because we have the requirements" is incredibly (epistemologically) naïve.

Ignoring or skipping the tests based on requirements is equally naïve though. While few people will set up things on purpose, there are still plenty of teams that work this way. (information debt!) Testers are not allowed access to the source code. Testers are not included in design meetings. Testers operate one sprint behind, making interaction with the programmers harder. ~~Or they automate one sprint behind.~~ Or testers are in a separate team all together.

The reverse happens as well by they way. Testers having specified their tests, but not wanting to share them with the programmers, "because then they'll just build something that passes the tests".

!!! Is requirements-based testing like reproducing earlier experiments?

So the trick in testing seems to be to decide well when and how much to do of each kind of testing. To switch between verifying expected facts and discovering new facts.

And not to separate the two. To not go: we'll first test for all the requirements and do some exploration at the end, if there's time, as the cherry on top.

This is one of the strengths of contemporary exploratory testing (Maaret!). You take the requirements, and the code, and the existing (automated) tests, and your domain knowledge, etc. and you go look for what's missing. Gaps in what's been tested already. Gaps in the understanding of what needs to be built and what has been built. Surprising new facts about what's been built. And this results in fixes and improvements. And in automated induction: increased test coverage running in a pipeline.


## Running experiments - how often, how many?

I remember the days when getting a new release meant first doing some smoke and regression testing, manually. How much always was an interesting question. You would have no insight in what had been changed, beside a list of the work items that have been implemented in the release. You also had no idea what exactly had been tested. So yeah, that's about as black box as it gets. And this was custom work. So the guarantees by the supplier only went so far. "We've built this the way we think you've asked us to. But do check for yourselves. And once you accept the release, there are no more bugs, only change requests." As one of my old project managers used to say: "The question is not whether it will be fixed or not. The question is who is going to pay for it."

Contrast this with a modern development team. Hopefully each programmer makes small changes, which then go through a pipeline with a sufficient level of test coverage. That's a lot of induction happening right there, and it takes zero effort to run. (It does take effort to add additional tests, of course.) And while it has its limitations, I don't think I ever want to go back to a team that does not have this. Every test is a hypothesis that once held true. And we can re-verify each of them automatically. How great!

This is why some people call automated tests change detectors. They tell you if a hypothesis no longer holds true. That might be a bad thing (most of the time it is), but that might also be a good thing (hypothesis no longer should be true), or an interesting thing (we learn something new). But it's definitely a good thing that you know about it.

Tests as hypothesis is a cool angle for TDD. Because you first falsify the hypothesis by running the test before having written the code. Then you write the code that should make the hypothesis true. Then you verify.

### How often - problem of induction

A tricky question is: how often do you have to run the same test to trust its results? And I'm talking about running the same test on exactly the same code under (presumably) the same circumstances. If you've seen something once, has it been tested? How well do you control and have insight on the circumstances?

Is it possible to ~~step into the same river~~ execute the same test twice? Arguably not, because you are not the same. What about automated? How do we know everything is still exactly the same? And doesn't an automated test need a human somewhere in the loop, so in that sense it's not the same test? Unless they're amnesiac?

This question is the most relevant when testing bug fixes. "If I do A, the application should do B, but it does C." "I fixed it." "I do A, the application does B. Bug closed!" That seems like a very lazy way of testing. It's very lazy deduction. Only focusing on the one explicit hypothesis of the bug report. Not looking into side effects - either intended or unintended (???) of the bug fix.




---

---

## Surprising facts versus requirements
In testing we have multiple sources of facts. No, we have one, the application. The rest is consequences, hence deduced before the fact.
In testing you have the written requirements.

Do test ideas based on requirements count?

requirements do some (most? all?) of the deduction for us

If I could tell you in detail what and how I would test upfront, I'd add those as requirements / acceptance criteria from the start. Then you could build it right/correct from the start, instead of having me test it afterwards. // if I can tell you what to test without exploring, it could have been a requirement
if there would be no need for exploration/abduction, there would be no test engineers, only requirement engineers

requirements are input for abduction, just like observation, or not

it's not because it's in the requirements, that's how the software works
 start with behavior or start with code


does abduction count when looking at requirements? yes, but is not software testing; it's requirements engineering?



## How many experiments do you need?
how many and how varied?
how many / how often relates to human versus machine execution

test automation is running pre-defined induction, so limited, so powerful


## misc notes

Testing includes looking for surprisings facts. So does inquiry, because it assumes doing science.

Noticing is key for induction.

Deduction -> my epistemological deconstruction; my presentation about philosophy of science

deduction and test design: idea: ?? importance of understanding software/hardware/people/... ?? => affinity thing?


# Optimizing for moments of discovery

only abduction results in new ideas

A (the?) key aspect of abduction is that it's only one of the three stages that 
synthetic


# Affinity between man and nature

built by man versus built by nature

---

TODO:
- link from here to the part about abduction in The nine skills of exploratory testing
- link from here to being intentional about exploratory testing
- link from here to espitemological deconstruction

---

#  Verification

Abduction is adopting a hypothesis as suggested by the facts. We notice a surprising fact and now an explanation is required. A good hypothesis explains the observed facts (the facts must follow from the hypothesis deductively) and its conclusions are capable of verification[^2]. A hypothesis is always adopted on probation and must be tested.

[^2]: Peirce died 20 years before Karl Popper published "Logik der Forschung". [Karl Popper's Wikipedia page](https://en.wikipedia.org/wiki/Karl_Popper#Falsifiability_and_the_problem_of_demarcation) however states "This[sic] Popper's falsifiability resembles Charles Peirce's nineteenth-century fallibilism. In *Of Clocks and Clouds* (1966), Popper remarked that he wished he had known of Peirce's work earlier."

# Three stages

> Scientific method begins with abduction or hypothesis: because of some perhaps surprising or puzzling phenomenon, a conjecture or hypothesis is made about what actually is going on. This hypothesis should be such as to explain the surprising phenomenon, such as to render the phenomenon more or less a matter of course if the hypothesis should be true. - https://plato.stanford.edu/entries/peirce/#dia

> Scientific method then proceeds to the stage of deduction: by means of necessary inferences, conclusions are drawn from the provisionally-adopted hypothesis about the obtaining of phenomena other than the surprising one that originally gave rise to the hypothesis. Conclusions are reached, that is to say, about other phenomena that must obtain if the hypothesis should actually be true. These other phenomena must be such that experimental tests can be performed whose results tell us whether the further phenomena do obtain or do not obtain. - https://plato.stanford.edu/entries/peirce/#dia

> Finally, scientific method proceeds to the stage of induction: experiments are actually carried out in order to test the provisionally-adopted hypothesis by ascertaining whether the deduced results do or do not obtain. - https://plato.stanford.edu/entries/peirce/#dia


> At this point scientific method enters one or the other of two “feedback loops.” If the deduced consequences do obtain, then we loop back to the deduction stage, deducing still further consequences of our hypothesis and experimentally testing for them again. But, if the deduced consequences do not obtain, then we loop back to the abduction stage and come up with some new hypothesis that explains both our original surprising phenomenon and any new phenomena we have uncovered in the course of testing our first, and now failed, hypothesis. Then we pass on to the deduction stage, as before. The entire procedure of hypothesis-testing, and not merely that part of it that consists of arguing from sample to population, is called induction in Peirce’s later philosophy. - https://plato.stanford.edu/entries/peirce/#dia
