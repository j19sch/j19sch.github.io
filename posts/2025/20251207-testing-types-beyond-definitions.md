<!--
.. title: Testing types - beyond definitions
.. slug: testing-types-beyond-definitions
.. date: 2025-12-07
.. category: software testing
.. tags: 
.. type: text
.. description: 
-->

*This is an abridged and edited version of a talk I did at the Romanian Testing Conference in 2019: ["Testing our testing type."](https://smallsheds.garden/slides/rtc2019-testing-types.html) (Mostly, I left out all of the Wittgenstein stuff, or close to it.)*

Testing types in software testing are a mess - and not just [regression testing](link://slug/regression-testing-it-means-less-than-you-think). Just last week a colleague said *"We should also do regression testing."* So I asked *"What do you mean by regression testing?"*. And the reply was: *"Test frontend and backend together using Playwright."* Which made me think *"I see what you mean, but I would never call that intergration testing."* and made me reply: *"Yeah, we should."*

The typical solution to this problem is to start defining the different testing types. To me, that's just one approach of many to make sense of testing types as you hear them used. So far I have come up with six.

<!-- TEASER_END -->

# Six approaches

## Definitions

If we look up ["integration testing"](https://glossary.istqb.org/en_US/term/integration-testing?term=integration%20testing&exact_matches_first=true) in the ISTQB Glossary[^1], we get "A test level that focuses on interactions between components or systems." This might raise the question what a component is (which [is defined](https://glossary.istqb.org/en_US/term/component?term=component&exact_matches_first=true) in the glossary) and what a system is (which isn't defined in the glossary). Moreover, one might what a ["test level"](https://glossary.istqb.org/en_US/term/test-level?term=test%20level&exact_matches_first=true) is: "A specific instantiation of a test process." After which we check the definition of ["test process"](https://glossary.istqb.org/en_US/term/test-process?term=test%20process&exact_matches_first=true), i.e. "The set of interrelated activities comprising of test planning, test monitoring, test control, test analysis, test design, test implementation, test execution, and test completion."

[^1]: Not that I'm a huge proponent of ISTQB, but it is the obvious choice if one is looking for a testing glossary.

So definitions are a good example of "turtles all the way down" or [infinite regress](https://en.wikipedia.org/wiki/Turtles_all_the_way_down). They are helpful, however, if you do have some basic level of knowledge that allows you to understand the definitions. And definitions clarify the relations between different concepts.


## Opposites

There are quite a few oppposites in testing types: functional vs non-functional testing, dynamic vs static testing, scripted vs exploratory testing, negative vs positive testing. There are also testing types without an opposite: agile testing, developer testing, regression testing. Not that it's impossible to come up with an opposite, but you never hear anyone use it. Finally, there are opposites, but on a scale, so sometimes we add a term for something in between. For example, gray-box testing for when you do something that's neither black-box, nor white-box testing.

Opposites allow us to explore what a thing is by looking at what it isn't. And if that thing it isn't, is its own testing type or not. We should be mindful of false dichotomies, though. We like to split up things in either/or, but they are rarely that simple.


## All the elements

Some testing types make most sense when in a list of similar testing types. Performance testing, security testing, accessibility testing are all forms of quality characteristic testing. Desktop, mobile, and browser are forms of device type testing.

Unit testing can fit in different lists. There's unit - API - UI, but also unit - component - system - integration - end-to-end. And there are plenty other option, even if you only focus on [pyramids](https://www.testingreferences.com/here_be_pyramids.php).

Listing all or several testing types that fit the same category allows them to clarify each other's meaning. They will be the same in some sense, because they fit in the same category. They will be different, because they are different testing types[^2].

[^2]: Unless they're synonyms, which raises the question: do true synonyms exist?


## Combinations



## Software development model

## Social aspects

# Closing thoughts