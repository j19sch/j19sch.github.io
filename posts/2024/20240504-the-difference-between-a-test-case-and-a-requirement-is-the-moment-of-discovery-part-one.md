<!--
.. title: The difference between a test case and a requirement is the moment of discovery (part one)
.. slug: the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery-part-one
.. date: 2024-05-04
.. category: 
.. tags: 
.. type: text
-->

There are several straightforward ways to distinguish a test case from a requirement. A test case tells you how to check some kind of thing about the application, a requirement tells you that the application should do some kind of thing. A test case is written by a tester, a requirement by a business analyst. A test case takes the shape of an action and an evaluation of the result, a requirement takes the form of a sentence like "product ABC shall XYZ." (at least according to NASA[^1]).

[^1]: [https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/](https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/)

A less straightforward, but more interesting way to distinguish a test case and a requirement, is what I posted on [Mastodon](https://chaos.social/@joeposaurus/111963169048720039) and [LinkedIn](https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di) about two months ago:

> The difference between a test case and a requirement is the moment of discovery.

In this post I want to explore the meaning of that statement. In the next post I'll explore how looking at requirements and test cases in this way, can help us to do better testing. So this post will be more theoretical and philosphical; the next one more practical.


<!-- TEASER_END -->

# About requirements and test cases

## What's a requirement?

A requirement describes some aspect of the thing we are building. It tells us what the thing should be or should do. Requirements are input for the building of software.

I do realize here I'm glossing over the difference between explicit and implicit requirements. For the purpose of this post, a requirement is anything that the team as a whole believes the thing they're building should be or do. So early on something might be a requirement because the lead dev knows it to be. Later on, it might only be a requirement if it's part of the shared understanding among the developers. If it's only a passing thought of a single team member, not really.


## What's a test case?

A test case describes something we want to find out about the thing we're building. It tells us how we might learn something about the thing. Test cases are input for the evaluation of software.

<!-- !!! later I want to say that test cases are output !!! -->

In that sense, the term "test idea" might be more apt than "test case". Whenever someone says "test case", I always wonder what they mean exactly. Do they mean "something we should test", so a test idea or a charter for [exploratory testing](https://pragprog.com/titles/ehxta/explore-it/)? Or "if you do this in the application, this other thing should happen", so what I would call a test case? Or do they mean a list of steps with detailed descriptions of what to do and what to check, so a test script?


### Test cases that are translated requirements versus ones that aren't

<!-- For the purpose of this post, on the one hand all three, test ideas, test cases, and test scripts, count as test cases; on the other hand, only the test ideas do. -->

For the purpose of this post, while all three (test ideas, test cases, and test scripts), count as test cases, there is a distinction to be made between test cases and test scripts on the one hand, and test ideas on the other.

Test cases and test scripts are translations of requirements. There is an expected result. We know what the thing we're building, should do. That makes them rephrasings of the requirements. This is especially clear if you [create a test case through a formal test design technique](link://slug/the-test-case-an-epistemological-deconstruction). The test case is no more than the transformation of a requirement by a logarithmic test design technique.

With test ideas, on the other hand, there's no expected result specified upfront. They take the form of "I wonder what would happen if ..." and "I'm curious about ..." So the goal is to discover something first, and then to evaluate it. How to evaluate that discovery, might be immediately obvious in the moment of discovery. Or it might take some work to figure out how to evaluate it. To - in a sense - decide if you've found a requirement or a bug.

I do realize here that I'm assuming that translating a requirement to a test case is trivial. Often enough, that's not the case. And arguably there are some requirements that are so difficult to translate into test cases, that for all practical purposes they are un-translatable. So in that sense the distinction I'm making here is more of a theoretical nature than a practical one: between test cases that are translations of requirements, even if in practice you wouldn't perform this translation, and test cases that are not and can not be translations of requirements. The latter are test ideas, where we're not sure what will happen and/or how we will evaluate what will happen.

We'll return to this issue in the second part of this blog post. Because one of the things that help us to do better testing, is to distinguish these categories of requirements and test cases, and make conscious decisions about them and what to do.
<!-- THIS NEEDS MORE TEXT -->


## Requirements are for creation, test cases for evaluation

A requirement is an answer, a "should". A test case is a question, a "what if?"

A requirement serves the purpose of design, a test case the purpose of evaluation.

As such, a requirement is input for building, a test case input for testing.

And still, they are the same thing. It's just that for a requirement we already know what it is the software should do. For a test case, sometimes we do (test cases that are translated requirements) and sometimes we don't (test ideas).

If they are the same, though, how does it make sense to distinguish the two based on the moment of discovery?


# The moment of discovery

The moment of discovery for a requirement happens while we are designing what we are going to build. The moment of discovery for a test case happens while we are evaluating what we have built - or, what we will have built. This leaves a lot of space for these moments to happen. A requirement can be discovered months before a line of code is written, or in the case of TDD, mere seconds. The same for the discovery of a test case: it might be discovered months before the test executed, or in the case of exploratory testing, mere seconds.

The value of making the distinction between a requirement and a test case based on the moment of discovery, lies in the "or, what we will have built" in the previous paragraph.

If you can come up with a test case for something before it's been built, then why are not involved in defining the requirements? Why are we separating design from test?[^2] Why are they done by separate people, in separate "phases", in different formats? Using different skills and techniques, or at least with differently named skills and techniques?

[^2]: And from build? See the closing thought of this post.

Did we discover this as part of design, as input for building? Or did we discover it though evaluation, as input for testing?
That's not a straight line we can draw through our software development process. We can't pinpoint a moment in time, where everything before is a test case, and everything after is a test case. <!-- different meanings to moment of discovery -->


creation vs evaluation
incidental: format etc; essential: for building or for testing
but some test cases should have been requirements, not because "should have found earlier" but because our process separates them incorrectly
Now you could argue, that it's possible to use test cases as input for creation. Of course, you can, but then they are requirements. The difference is not in how you title them, what template you use, the format you write them in. That's incidental, not the essense, superficial. The difference is what you do with them. -> answers and questions

What this means, is that anyting you discover early enough, is a requirement. Anything discovered later, is a test case. Discover it early and it's input for design and building. Discover it later and it's input for evaluation (aka [verification and validation](link://slug/three-arguments-against-the-verification-validation-dichotomy/)). This raises the question: where exactly is that dividing line between requirement and test case? And can we move that line?


## (leftover) three process options

In an ideal but impossible world, we would be able to define all the requirements upfront, translate them all to test cases, automate all of those, and then we'd just have to build a piece of software that passes all the tests. It's like waterfall, but even better.

In an ideal world we could aspire to, we would define all the requirements and related test cases upfront (as far as feasible). And we'd have an initial list of test ideas prepared. As we build the software, we keep revisiting the requirements, the test cases, and the test ideas.

In the actual world, things are messier. We define requirements until we feel it's time to start building. Then we start building and testing, hopefully discovering additional requirements to a sufficient degree. That may not sound that different from the previous paragraph, but the difference is the lack of intentionality in the momnent of discovery of requirements and test cases. While in the second part of this post, we'll see how being deliberate about this moment, will lead to better testing and better software.

The distinction between the moment of discovery, is: did we discover this requirement through testing or through design?
Where we don't want to discover the requirements through testing, that we could have discovered through design. That's something for the next part.



# Closing thought - designing vs building vs testing

is it even possible to distinguish designing from building (programming) from testing?

Arguably they're part of the building. So there is not separate testing. There's only designing and building. While even writing code can be seen as design, and building comes even later. => change building to programming?

like ET is paralellel design - execuation - evaluation (check definition!)

