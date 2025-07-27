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

And in that book I found something more interesting than just abduction: Peirce's three stages of inquiry. Or how - according to Peirce - the three phases of the methodology of science are abduction - deduction - induction. And it seem to me that testing works in a very similar way.[^1]

[^1]: I very deliberately wrote "in a very similar way". Because this blog post is no more than that: noticing an interesting similarity between what I understand of Peirce's thoughts based on Fann's book and what I believe about testing. If I'd want to make a stronger claim, e.g. about the similarities between testing and science, or about Peirce correctly describing the scientific method, I'd have to do a lot more reading and studying.


<!-- TEASER_END -->


# The three stages of inquiry

Let's look at each three of these in a little more detail and then in the next section how they might relate to testing.

The first stage of inquiry, abduction, starts with noticing a surprising fact. Now an explanation is required. So we adopt a hypothesis as suggested by the facts. This hypothesis should be able to explain the observed facts. Nota that we adopt it on probation only. It must be tested.

Then we move on to the second stage, deduction. What are the necessary and probable consequences of the hypothesis? If our hypothesis is true, what else has to be true as well? Since we want to test our hypothesis, at least some of these consequences must be testable. (The hypothesis itself is not testable, since it's an explanation, an interpretation.)

Finally, we proceed to the third and last stage, induction. We test our hypothesis by running experiments. Either the consequences we deduced hold true, supporting our hypothesis. In that case we can either decide we're done or deduce additional consequences to test. Or, the consequences do not hold true, invalidating our hypothesis. In that case we return to the abduction stage, trying to come up with a new hypothesis.

Or as K.T. Fann summarizes in the Introduction of their book:

> Peirce conceived of the three kinds of reasoning as three stages of inquiry. Abduction invents or proposes an hypothesis; it is the initial proposal of an hypothesis on probation to account for the facts. Deduction explicates hypotheses, deducing from them the necessary consequences which may be tested. Induction consists in the process of testing hypotheses. Thus, "Abduction is the process of forming an explanatory hypothesis. It is the only logical operation which introduces any new ideas; for induction does nothing but determine a value, and deduction merely evolves the necessary consequences of a pure hypothesis" (5.171). *- Fann, p10*


# The three stages and testing

At a surface-level there's a clear similarity between the three stages of inquiry and testing. Abduction is coming up with test ideas, things you wonder about. Deduction is coming up with the actual tests based on those test ideas. And induction is when you execute those tests and interpret the results.

While I agree with that similarity, it's not very informative. To get somewhere interesting, we need to dig a little deeper. That, however, is something for the next post.

---

Can I split the follow-ups in abduction, deduction, induction?

When does testing go from
deduction (explicating hypothesis, deduce/evolve necessary consequences which may be tested)
to
induction (process of testing hypotheses, determining a value)

induction seems to be: interact - observe/measure - evaluate; setting up experimental environment

---

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
- it's weird that we usually talk about test design and execution, so deduction and induction, but skip the abduction

---

## Only exploratory testing counts as abduction

Creating test cases based on requirements does not count as abduction. It's deduction. The hypothesis is already formed: the application behaves as per the requirement. So the steps left are deduction and induction. Deducing what you expect to be true if the hypothesis holds and inducing if it truly holds.

(Note that there's a difference between an expectation being true and something happening. You might expect something to happen or expect something not to happen. Either can be tested if they hold to be true, if the result is something that can be observed.)

=> footnote This is something I covered 10 years ago in ["The test case - an epistemological deconstruction".](link://slug/the-test-case-an-epistemological-deconstruction). There I warned against separating strategy, tactics and operations in testing too far apart. Those three levels are not dissimilar from abduction - deduction - induction. And I warned against how test cases break up the OODA-loop in testing. Even worse, it's often not a loop at all when using test cases. (OODA stands for Observe - Orient - Decide - Act, it's a model created by John Boyd.)

To re-iterate, when using test cases based on requirements, there is no abduction. There is no surprising fact leading to the need for a hypothesis. We're not trying to understand the universe after it's been created. We have the universe and we have the blueprints. All that's left is verifying that the universe matches the blueprints, i.e. deduction and induction. Any surprising fact we discover, is a bug. Something that does not meet requirements. (more on this later)

Abduction only happens when you engage in exploratory testing. You explore the application. Something surprises you. So you form a hypothesis and explore further based on that hypothesis. It only happens when - as Maaret says - you use the application as your external imagination.


---

the flavors (the test is introduction of new ideas in form of hypothesis to account for facts)
- test cases as in scripts
- test ideas as in exploratory testing
- additional requirements

when do we come up with new ideas and hypotheses
- application as external imagination
- generating test ideas: I wonder how the applications behave when ...
- not when verifying requirements

facts are behavior of software, requirements are not; also see below

What if you come up with test ideas upfront? What is that? Speculative requirements engineering?

---


Now what if you identify a missing requirement? I'd say that that is abduction. You identified an additional thing about the behavior. It's not testing, though, as I argued in my post ... (which one? or was it a note?), it's requirements engineering. We can also see how the similarity with the three stages of inquire breaks down here. Inquiry starts from observing some behavior in the world. Requirements engineering is specifying how something should behave. So for the similarity to work, to be at least informative, abduction is more "are we discovering something new - even if it's only tentatively?" versus "are we encountering a surprising fact?"


## We don't have facts, we have behavior based on requirements

=> hypothesis/test idea when exploratory testing, i.e. exploring and evaluating
=> or only software behavior is fact, documentation is not

The largest way the similarity breaks down is that we don't just have access to the behavior. We have access to information about the intended behavior. Both to the documents describing it and to the people implementing it. (Actually, we are some of the people implementing the behavior.) However, experience has shown that's not enough.

It is not possible to create the perfect requirements, implement those perfectly, and know with absolute certainty you have implemented it perfectly. And that's ignoring the whole platform you are relying on to do those things.

> Any sufficiently complex system is either incomplete or self-contradictory. (?) Gödel

That 'last' one is a funny one. Being able to specify and implement requirements perfectly, without the ability to know if you did so, is in a sense no better than not being able to do these things perfectly. Or is the knowing implicit in the perfection?

So again the breaks up our testing in two types, as I described in "Being intentional about exploratory testing". There's tests that look for value and there's tests that look for risk (James Lyndsay).

Limiting yourself to tests that look for value, that are based on deduction and induction, but skip the abduction, "because we have the requirements" is incredibly (epistemologically) naïve.

Ignoring or skipping the tests based on requirements is equally naïve though. While few people will set up things on purpose, there are still plenty of teams that work this way. (information debt!) Testers are not allowed access to the source code. Testers are not included in design meetings. Testers operate one sprint behind, making interaction with the programmers harder. ~~Or they automate one sprint behind.~~ Or testers are in a separate team all together.

The reverse happens as well by they way. Testers having specified their tests, but not wanting to share them with the programmers, "because then they'll just build something that passes the tests".

!!! Is requirements-based testing like reproducing earlier experiments?

So the trick in testing seems to be to decide well when and how much to do of each kind of testing. To switch between verifying expected facts and discovering new facts.

And not to separate the two. To not go: we'll first test for all the requirements and do some exploration at the end, if there's time, as the cherry on top.

This is one of the strengths of contemporary exploratory testing (Maaret!). You take the requirements, and the code, and the existing (automated) tests, and your domain knowledge, etc. and you go look for what's missing. Gaps in what's been tested already. Gaps in the understanding of what needs to be built and what has been built. Surprising new facts about what's been built. And this results in fixes and improvements. And in automated induction: increased test coverage running in a pipeline.


## Running experiments - how often, how many?

I remember the days when getting a new release meant first doing some smoke and regression testing, manually. How much of it to do always was an interesting question. You would have no insight in what had been changed, beside a list of the work items that have been implemented in the release. You also had no idea what exactly had been tested. So yeah, that's about as black box as it gets. And this was custom work. So the guarantees by the supplier only went so far. "We've built this the way we think you've asked us to. But do check for yourselves. And once you accept the release, there are no more bugs, only change requests." As one of my old project managers used to say: "The question is not whether it will be fixed or not. The question is who is going to pay for it."

Contrast this with a modern development team. Hopefully each programmer makes small changes, which then go through a pipeline with a sufficient level of test coverage. That's a lot of induction happening right there, and it takes zero effort to run. (It does take effort to add additional tests, of course.) And while it's not the be-all-end-all of quality, I don't think I ever want to go back to a team that does not have this. Every test is a small hypothesis that once held true. And we can re-verify each of them automatically. How great!

This is why some people call automated tests change detectors. They tell you if a hypothesis no longer holds true. That might be a bad thing (most of the time it is), but that might also be a good thing (hypothesis no longer should be true), or an interesting thing (we learn something new). But it's definitely a good thing that you know about it.

Tests as hypothesis is a cool angle for TDD. Because you first falsify the hypothesis by running the test before having written the code. Then you write the code that should make the hypothesis true. Then you verify.

### The problem of lazy induction and lazy deduction

A tricky question is: how often do you have to run the same test to trust its results? And I'm talking about running the same test on exactly the same code under (presumably) the same circumstances. If you've seen something once, has it been tested? How well do you control and have insight on the circumstances?

Is it possible to ~~step into the same river~~ execute the same test twice? Arguably not, because you are not the same. What about automated? How do we know everything is still exactly the same? And doesn't an automated test need a human somewhere in the loop, so in that sense it's not the same test? Unless they're amnesiac?

This question is the most relevant when testing bug fixes. "If I do A, the application should do B, but it does C." "I fixed it." "I do A, the application does B. Bug closed!" That seems like a very lazy way of testing. It's very lazy deduction. Only focusing on the one explicit hypothesis of the bug report. Not looking into side effects - either intended or unintended (???) of the bug fix.

### How often - manually or automatically

A curious thing about software compared to the universe, is that it keeps changing. While it's certainly possibly to discover new things about an existing piece of software, it's when we change things in the software, that we do testing.

In science you want to rerun an experiment to check the validity of the experiment. If the part of the universe you're running your experiment on, has changed since you (or someone else) did the experiment last, that's a problem with the experiment, not the universe.

If you rerun a test on some software, there's quite a few options. Perhaps the software changed as intended, but the test did not. Or the software shouldn't have changed, but luckily the test detected it. Or the software changed but the test fails to detect the change. Or the test was changed (incorrectly), and not the software.

So reproducing an experiment is a different game. There is a similarity: we do want our tests to produce the same results on everyone's machine and on the CI/CD server. I've often used it as a test for test automation. It runs on my machine, does this run on yours too? Especially when I was in a team where we had three different OS-es across the team members, this was an important thing to test.

The reason it's a different game is because as we change the software, we want to rerun the same tests. Use them as change detectors. Check the we only changed what we intended to change. (mentioned above as well, and in regression-testing-it-means-less-than-you-think) We might be experimenting against a different universe.

That also means that you want to run these tests whenever you suspect something might have changed. Which brings us to the importance of running these tests automatically:

> Without a pipeline, you have *manual* test automation. Pipelines transform programs from their writing form to their running form.
> - Maaret Pyhäjärvi on [LinkedIn](https://www.linkedin.com/posts/maaret_i-know-it-is-silly-to-quote-yourself-but-activity-7323961095969292289-0dRw/)

Not that running tests in a pipeline is the whole story. If no desicions are informed by the pipeline going either green or red, you might as well not have bothered.



?? the problem of reproducibility in software

- have said this (look at results) somewhere before, but where?
	- reflections on manifesto mentions extended cognition but for tools
- test automation that needs to be run manually vs automated in a pipeline -> how often experiments


## Automating tests is not the way

A still common approach to testing is to first design a bunch of test cases, execute them, and then automate the most important ones (sometimes only in the next sprint). There are several issues with that.

First of all, there's either no abduction or a very poor form of it. No abduction if you design your test cases based on the requirements. A very poor form of it if you do some exploration, but (not?) as actual testing, but merely to collect (additional) information to design your test cases with.

Secondly, for the automation part, splitting the designing, executing and automating in three seprate phases is a very inefficient way of doing things. Both the manual execution and the automation can and should inform your design. But they have different constraints, not everything that's done (easily) manually can be automated and not everything that's done automated can be done (easily) manually.[^3] Thirdly, as you automate, you'll have to execute again, so it's an additional execution, but you don't really care about the results at that point in time. Fourthly, a lot of the value of the automation is to run it often, cheaply. After you have executed your tests manually, but before you have automated them, there's a gap. And in that gap lives risk. Because it's not very enticing to manually execute a test, that passed recently, and is really close to being automated.

[^3]: This has been the problem of the field of AI since it's inception. What's easy for a human to do, e.g. identify things and their location in space through sight, can be very hard for a machine to do - and vice-versa.

manual and automation require different deduction? or induction? they don't translate 1-to-1

this section is too long, not related to stages of inquiry


## affinity between man and nature -> affinity between tester and software behavior

what does that mean?

how to increase?



## how come we so rarely speak about abduction, e.g. generating test ideas

exercise Rikard Edgren


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
