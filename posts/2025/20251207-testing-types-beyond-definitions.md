<!--
.. title: Testing types - beyond definitions
.. slug: testing-types-beyond-definitions
.. date: 2025-12-07
.. category: software testing
.. tags: communication, heuristics, semantics, software testing, test management
.. type: text
.. description: clarifying over correcting
-->

Testing types in software testing are a mess. It's not just ["regression testing"](link://slug/regression-testing-it-means-less-than-you-think) that can mean more things than there are people in the room. It's probably true for all of them.

Just last week a teammate said *"We should also do integration testing."* So I asked *"What do you mean by integration testing?"*. And the reply was: *"Testing the frontend and backend together using Playwright."* Which made me think *"I see what you mean, but I would never call that integration testing."* and made me reply: *"Yeah, we should."*

The typical solution to this problem is to start defining the different testing types. To me, that's just one approach of many to make sense of testing types. So far I've come up with an additional five.

<!-- TEASER_END -->

# Definitions {.small}

If we look up ["integration testing"](https://glossary.istqb.org/en_US/term/integration-testing?term=integration%20testing&exact_matches_first=true) in the ISTQB Glossary[^1], we get *"A test level that focuses on interactions between components or systems."* This might raise the question what a component is (which [is defined](https://glossary.istqb.org/en_US/term/component?term=component&exact_matches_first=true) in the glossary) and what a system is (which isn't). Moreover, one might wonder what a ["test level"](https://glossary.istqb.org/en_US/term/test-level?term=test%20level&exact_matches_first=true) is: *"A specific instantiation of a test process."* After which you check the definition of ["test process"](https://glossary.istqb.org/en_US/term/test-process?term=test%20process&exact_matches_first=true), i.e. *"The set of interrelated activities comprising of test planning, test monitoring, test control, test analysis, test design, test implementation, test execution, and test completion."*

[^1]: Not that I'm a huge proponent of ISTQB, but it is the obvious choice if one is looking for a testing glossary.

So definitions are a good example of "turtles all the way down" or [infinite regress](https://en.wikipedia.org/wiki/Turtles_all_the_way_down). They are helpful, however, if you do have some basic level of knowledge that allows you to understand the definitions. And definitions clarify the relations between different concepts.


# Opposites {.small}

There are quite a few opposites in testing types: functional vs. non-functional testing, dynamic vs. static testing, scripted vs. exploratory testing, negative vs. positive testing. There are also testing types without an opposite: agile testing, developer testing, regression testing. Not that it's impossible to come up with an opposite, but you never hear anyone use it. Finally, there are opposites, but on a scale, so sometimes we add a term for the thing in between. For example, gray-box testing for when you do something that's neither black-box, nor white-box testing.

Opposites allow us to explore what a thing is by looking at what it isn't. And to decide if that thing that it isn't, is its own testing type - or not. We should be mindful of false dichotomies, though. We humans like to split things up in either/or, this-or-that, but things are rarely that simple.


# All the elements {.small}

Some testing types make more sense when part of a list of similar testing types. Performance testing, security testing, accessibility testing are all forms of quality characteristic testing. Desktop testing, mobile testing, and browser testing are forms of device type testing.

Unit testing can fit in different lists. There's unit - API - UI, but also unit - component - system - integration - end-to-end. And there are plenty of other options, even if you only focus on [pyramids](https://www.testingreferences.com/here_be_pyramids.php).

Listing all or several testing types that fit the same category allows them to clarify each other's meaning. They will be the same in some sense, because they fit in the same category. They will be different, because they are different testing types.


# Combinations {.small}

There are many different testing type categories, meaning a lot of testing types are not mutually exclusive. That means you can combine some of them and see how that works out. For example, manual unit testing, automated usability testing, static integration testing.


Or if you take it to extremes: dynamic functional whitebox regression mobile UI exploratory pair testing. (I hope I got the [order](https://en.wikipedia.org/wiki/Adjective#Order) right.)

As you combine testing types, ask yourself: Is the result obvious? Is it curious? Weird? Wrong? Something else?


# Software development model {.small}

Some testing types have different meanings depending on what kind of software development is practiced. "Acceptance testing" is a different thing in the [V-model](https://en.wikipedia.org/wiki/V-model_(software_development)) than in [Acceptance Test-Driven Development (ATDD)](https://en.wikipedia.org/wiki/Acceptance_test-driven_development).

"Developer testing" is done by developers, but are they in an outsourced development team or in an agile one? When you say "automated testing", do you mean the automation of manual test scripts, or the tests that run in your pipeline?

And there's also at least one testing type that makes it very clear what kind of software development it expects: "agile testing".

All this to say that testing types do not exist in isolation. They are part of something larger, i.e. an approach to software development.


# Social aspects {.small}

Testing is a social activity. So some testing types tell us with whom we are testing: pair testing, ensemble or mob testing, crowd testing.

Some testing types have different meanings in different groups. Most developers seem to mean with "end-to-end testing" testing through the whole stack, while most testers seem to mean testing a group of applications from one end to another. Which has resulted in some people distinguishing horizontal from vertical end-to-end testing. And so the number of testing types grows...

Testing types can also be used to exert power. A classical (but hopefully outdated) example is testers not getting access to the code of the application they are testing, because they are supposed to do "black-box testing". Or an organization in which testing equals "scripted testing", because it results in a kind of legibility that gives management a sense of control.

And then there's "technical testing" or "automated testing", which - if you're able to do them - gives you more leverage when negotiating your salary.

Testing types do not exist outside of any social context. They affect how people interact with each other.


# Closing thoughts {.small}

Testing types can refer to just about anything. For "X testing", anything can be the "X", so the meaning of "X testing" can be anything. It might refer to how you're testing, what you're testing, the goal of your testing, etc. And the meaning of "X testing" will differ depending on the person, the circumstances, shifts and changes in software testing, etc.

Which how we get to Wittgenstein's philosophy of language:

> *For a large class of cases of the employment of the word "meaning" - though not for all - this word can be explained in this way: the meaning of a word is its use in language.* (PI 43, Ludwig Wittgenstein)

Hence, the six approaches listed above to explore meaning. Because clarity of meaning matters in communication. And if meaning is usage, clarifying is better than correcting.

So if someone mentions a testing type in a way that puzzles you, explore what they mean, engage in dialogue, or ask *"Can you show me?"*

---

*This is an abridged and edited version of a talk I did at the Romanian Testing Conference in 2019: ["Testing our testing type."](https://smallsheds.garden/slides/rtc2019-testing-types.html) Basically, I left out most of the Wittgenstein stuff.*