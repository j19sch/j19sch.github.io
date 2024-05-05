<!--
.. title: The difference between a test case and a requirement is the moment of discovery (part one)
.. slug: the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery-part-one
.. date: 2024-05-04
.. category: 
.. tags: 
.. type: text
-->

There are several straightforward ways to distinguish a test case from a requirement. A test case tells you how to check some kind of thing about the application, a requirement tells you that the application should do some kind of thing. A test case is written by a tester, a requirement by a business analyst. A test case consist of an action and an evaluation of the result, a requirement takes the form of a sentence like "product ABC shall XYZ." (at least according to NASA[^1]).

[^1]: [https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/](https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/)

A less straightforward, but more interesting way to distinguish the two is what I posted on [Mastodon](https://chaos.social/@joeposaurus/111963169048720039) and [LinkedIn](https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di) about two months ago:

> The difference between a test case and a requirement is the moment of discovery.

In this post I want to explore the meaning of that statement. In the next post I'll explore how looking at requirements and test cases in this way, can help us to do better testing.


<!-- TEASER_END -->

# About requirements and test cases

## What's a requirement?

A requirement describes some aspect of the thing we are building. It tells us what the thing should be. Requirements are input for the building of software.

I realize I'm glossing over the difference between explicit and implicit requirements here. For the purpose of this post, a requirement is anything that the team as a whole believes the thing they're building should meet. So early on something might be a requirement because the lead dev knows it to be. Later on, it might only be a requirement if it's part of the shared understanding among the developers.


## What's a test case?

A test case describes something we want to find out about the thing we're building. It tells us how we might learn something about the thing. Test cases are input for the evaluation of software.

<!-- !!! later I want to say that test cases are output !!! -->

In that sense, the term "test idea" might be more apt than "test case". Whenever someone says "test case", I always wonder what they mean exactly. Do they mean "something we should test", so a test idea or a [charter for exploratory testing](https://pragprog.com/titles/ehxta/explore-it/)? Or "if you do this in the application, this other thing should happen", so what I would call a test case? Or do they mean a detailed description of what to do and what to check, so a test script?


### Test cases that are translated requirements versus ones that aren't

<!-- For the purpose of this post, on the one hand all three, test ideas, test cases, and test scripts, count as test cases; on the other hand, only the test ideas do. -->

For the purpose of this post, while all three (test ideas, test cases, and test scripts), count as test cases, there is a distinction to be made between test cases and scripts on the one hand, and test ideas on the other.

Test cases and test scripts are translations of requirements. There is an expected result, which makes them rephrasings of the requirements. This is especially clear if you [create a test case through a formal test design technique](link://slug/the-test-case-an-epistemological-deconstruction). The test case is no more than the transformation of a requirement by a logarithmic test design technique.

With test ideas there's no expected result specified upfront. They take the form of "I wonder what would happen if ..." and "I'm curious about ..." So your goal is to discover something first, and then to evaluate it. How to evaluate your discovery, might be immediately obvious. Or it might take some work to figure out how to evaluate it. To decide if you've found a requirement or a bug.

As we'll see in the next part of this post, this distinction will be relevant for improving how we do testing bases on this idea that the difference between a test case and a requirement is in the moment of discovery.

I do realize that I'm assuming here that translating a requirement to a test case is trivial. From my own experience I can say: that's not true. Sometimes it's far from trivial. And arguably there are some requirements that are so difficult to translate into test cases, that for all practical purposes they are un-translatable. So in that sense the distinction I'm making here is more of a theoretical nature than a practical one: between test cases that are translations of requirements, even if in practice you wouldn't perform this translation, and test cases that are not translations of requirements. The latter are test ideas, where we're not sure what will happen and/or how we will evaluate what will happen.


<!-- If the difference between a test case and a requirement is in the moment of discovery, it's the test ideas that are most important. Or are they? Is this for the next part and the importance of ET? -->


<!-- What about all the stuff that runs in the pipeline? I guess we know what it should do, but we do want to be very sure it still does this. But then how is it different from test cases derived with test design techniques? -->

<!--
	the distinction is in the moment of discovery, so no rephrasing of requirements into test cases
	perhaps I don't have a clear anwers and this is more of an exploration of meaning
	how does this link to contemporary exploratory testing? to putting exploratory testing really early in the process?
		external imagination, not knowing (yet)
		ET is not at the end, it's part of the dev process, together with automation
		ET is exploring and evaluation once you've done something based on the requirements
-->

## Test cases and requirements - the short version

A requirement is an answer, a "should". A test case is a question, a "what if?"

A requirement is design, a test case is evaluation.

As such, a requirement is input for building, a test case input for evaluating.

And still, they are the same thing. It's just that for a requirement we already know what it is the software should do. For a test case, sometimes we do (test cases that are translated requirements) and sometimes we don't (test ideas).

If they are the same, though, how is there a distinction to be made based on the moment of discovery?

The moment of discovery for a requirement is while we are designing what we are going to build.[^2] The moment of discovery for a test case is while we are evaluating what we have built.[^3]

[^2]: Hence the statement that TDD is more about design than it is about testing.

[^3]: Just as with TDD where design happens just before the writing of the code, in exploratory testing the test design happens (mostly) just before the test.

In an ideal but impossible world, we would be able to define all the requirements upfront, translate them all to test cases, automate all of those, and then we'd just have to build a piece of software that passes all the tests.

In an ideal world we could aspire to, we would define all the requirements and related test cases upfront, that are feasible to define upfront. And have an initial list of test ideas prepared. As we build the software, we keep revisiting the requirements, the test cases, and the test ideas.

In the actual world, things are a lot messier. We define requirements until we feel it's time to start building. Then we start building and testing, hopefully discovering additional requirements to a sufficient degree. That may not sound that different from the previous paragraph, but the difference is the lack of intentionality in the momnent of discovery of requirements and test cases. While in the second part of this post, we'll see how being deliberate about this moment, will lead to better testing and better software.

<!-- The distinction between the moment of discovery, is: did we discover this requirement through testing or through design?
Where we don't want to discover the requirements through testing, that we could have discovered through design. That's something for the next part. -->

<!-- Is the distinction in fact between requirements and test ideas? No, that's the ideal situation -> next part. -->


## Test cases and requirements - the moment of discovery

The opening paragraph of this post already listed some different interpretations of the moment of discovery between test cases and requirements. The more waterfall-like your process, the more you'll have a group of people involved early on defining requirements, and a different group later one defining test cases. They have a different background and somewhat different skills, so they use different formats.

In essence, though, they are doing the same thing. They are defining requirements and writing them down - either in the format of a requirement or of a test case. Or they are translating requirements to test cases and writing those down.

If all of that is true, there's something

if this is true, that reqs and test cases are equivalent, there's limited value in translating existing requirements into test cases, there is more value in discovering test cases that are not requirements yet as early as possible
hence ET, product as external imagination, hence thin vertical slices for richer exploration


<!-- different meanings to moment of discovery -->

Actually, that kind of test case - any test case based on an explicit requirement - does not fit the statement that the distinction is in the moment of discovery.

In a sense, requirements are dead. Requirements are answers (even if tenuous). Test cases are questions.

a test case that's a directly translated required is not very interesting

not a straight line dividing the moment of disovery, but -> building vs -> evaluating



# What should be the line that divides requirements from test cases?

<!-- what should be the line that divides? -->

The dividing line between what's a test case and a requirement is the question: is this input for creation or for evaluation? If it's for creation, it's a requirement; if it's for evaluation, it's a test case.

Which aligns with the thought that TDD is not about testing, but about specification.

Now you could argue, that it's possible to use test cases as input for creation. Of course, you can, but then they are requirements. The difference is not in how you title the, what template you use, the format you write them in. That's incidental, not the essense, superficial. The difference is what you do with them. -> answers and questions

Now you could argue, that requirements need validation too. You might think your requirement is a good one, but that doesn't mean it actually is. While that's true, and important and needed, in the end it's working software, something interactive, in its real-life context, that needs to be evaluated if it's good enough. Imagination can take you far, mock ups further, but in the end we need the software.


What this means, is that anyting you discover early enough, is a requirement. Anything discovered later, is a test case. Discover it early and it's input for design and building. Discover it later and it's input for evaluation (aka [verification and validation](link://slug/three-arguments-against-the-verification-validation-dichotomy/)). This raises the question: where exactly is that dividing line between requirement and test case? And can we move that line?


# Closing thought - designing vs building vs testing

is it even possible to distinguish designing from building (programming) from testing?

Arguably they're part of the building. So there is not separate testing. There's only designing and building. While even writing code can be seen as design, and building comes even later. => change building to programming?

like ET is paralellel design - execuation - evaluation (check definition!)

