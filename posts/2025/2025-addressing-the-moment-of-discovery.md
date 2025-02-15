<!--
.. title: The difference between a test case and a requirement is the moment of discovery (part two)
.. slug: the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery-part-two-two
.. date: 2024-07-01
.. category: 
.. tags: 
.. type: text
-->


In my [previous post](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery) I explored the meaning of claiming that *"The difference between a test case and a requirement is the moment of discovery."* In this post I want to go deeper into what this means in practice. How it can help us to do better testing.

I think it does so in at least three ways:
- exploratory testing is key
- exploratory testing should happen as early as possible
- how best to divide up / share in the testing work


# exploratory testing is key
ToDo: link to section in previous post

In my previous post I distinguished test cases that are translated requirements from ones that aren't. With the ones that are, you know in advance what you want to evaluate, i.e. the requirement. With the ones that aren't, you don't. You first make a discovery, then you decide how to evaluate it. That's the core of exploratory testing: you explore and you evaluate - with each feeding into the other.

While these first kind of test cases are important - they are the requirements after all, they are from a testing perspective less interesting. We know the thing we're building needs to do a certain thing. So the people designing it know, the people building it know, and the people testing it know. (With some luck these are essentialy the same people, working as a team.)

For the second kind that's not the case. It's only through interacting with what we've built[^1], we discover what it does and decide if it should keep doing that. In a very real sense, we are discovering new requirements. That's why exploratory testing is key. To discover requirements that are impossible or impractical to discover in any other way.

[^1]: As [Maaret Pyhäjärvi](https://maaretp.com/) says: we use the application as our [external imagination](https://exploratorytestingacademy.com/courses/index.html).

And these can be input for new test cases in the first sense and for test automation.


# earlier exploratory testing is better





# dividing up the work / where is expertise needed
if the key of exploratory testing is in external imagination (noticing and deciding !heuristics!)
than you want the best et-ers doing testing on the most important (most risk, most value) things
not: brief and debrief someone else with the best et-er




---

# the old stuff

There are several straightforward ways to distinguish a test case from a requirement. A test case tells you how to check some kind of thing about the application, a requirement tells you that the application should do some kind of thing. A test case is written by a tester, a requirement by a business analyst. A test case consist of an action and an evaluation of the result, a requirement takes the form of a sentence like "product ABC shall XYZ." (at least according to NASA[^1]).

[^1]: https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/

A less straightforward, but more interesting way to distinguish the two is what I posted on [Mastodon](https://chaos.social/@joeposaurus/111963169048720039) and [LinkedIn](https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di) about two months ago:

> The difference between a test case and a requirement is the moment of discovery.

In this post I want to explore the meaning of that statement. In the next post I'll explore how looking at requirements and test cases in this way, can help us to do better testing.


<!-- TEASER_END -->



if this is true, that reqs and test cases are equivalent, there's limited value in translating existing requirements into test cases, there is more value in discovering test cases that are not requirements yet as early as possible
hence ET, product as external imagination, hence thin vertical slices for richer exploration

# What does it help us do? help us see? do differently?

what levers does this give us?
move the tipping point where requirements become test cases
test early, build quality in


## Exploratory testing is key / The exploratory part to testing is crucial

If I could tell you in detail what and how I would test upfront, I'd add those as requirements / acceptance criteria from the start. Then you could build it right/correct from the start, instead of having me test it afterwards. // if I can tell you what to test without exploring, it could have been a requirement

application is external imagination

discovery learning

interesting test cases are output
so interesting user requirements are output too? -> Maaret

<!-- If the difference between a test case and a requirement is in the moment of discovery, it's the test ideas that are most important. Or are they? Is this for the next part and the importance of ET? -->

### Closing thought - designing vs building vs testing

is it even possible to distinguish designing from building (programming) from testing?

Arguably they're part of the building. So there is not separate testing. There's only designing and building. While even writing code can be seen as design, and building comes even later. => change building to programming?

like ET is parallel design - execution - evaluation (check definition!)


---

## Can we move the separation line?
earlier is better

needs to be more than just: shift left
rater, can we ET sooner? or something like that

what if we can create a feedback loop between requiring and testing?

is this contemporary exploratory testing? credit Maaret Pyhäjärvi

In a sense, requirements are dead. Requirements are answers (even if tenuous). Test cases are questions. The trick is to limit test cases to only those questions that can be answered by exploring / interacting with the code / the application. The rest can be a requirement.

If you can come up with a test case for something before it's been built, then why are not involved in defining the requirements? Why are we separating design from test?[^2] Why are they done by separate people, in separate "phases", in different formats? Using different skills and techniques, or at least with differently named skills and techniques?

[^2]: And from build? See the closing thought of this post.


---


## How to divide the testing work?

A common way to increase the testing capacity in a team, is to have a tester and programmer pair on discussing what to test, after which the programmer does the testing. Optionally the programmer debriefs with the tester afterwards. This make sense from a time management perspective. The task that takes the most time is done by the programmer.

However, it's also the task that takes the most testing skill. Thinking upfront what to test is easier in two ways than doing actual testing:

- time is not a factor, you have as much time as you take, you're not constrained by the application state, there is no noticing of application behavior, only reasoning
- it's not too far from how programmers think during design, thinking about risk, correctness, non-functionals

It's also an question how much value this "thinking about what to test" really contributes to the value of the testing. In a stable team working on a stable enough product, you can probably do this using a one page checklist.

Arguably the difference between good and bad testing is in the details:

- what do you notice while testing? seeing what actually is there
- what choices do you make to select your test data
- how many variations can you come up with, to try? -> "here is a rock? what can you do with it?"
- modelling the application
- how varied are your oracles
- using the application as your external imagination -> new ideas

Everyone must have had the experience where they missed a glaring bug, because it happened in the third step of a five step-setup process and it's only after the setup, you would actually begin testing?

---

# leftovers

creation vs evaluation
incidental: format etc; essential: for building or for testing
but some test cases should have been requirements, not because "should have found earlier" but because our process separates them incorrectly

That second (and similar) questions are crucial to me. It's one thing to come up with a nice aphorism. It's a lot more interesting to have an aphorism that can be a guide to improve some aspects of how you develop software.

Requirements part of the design. Because I love the same word meaning different things in different contexts: "If it's your decision to make, it's design. If it's not, it's a requirement." - Alistair Cockburn.

What about all the stuff that runs in the pipeline? I guess we know what it should do, but we do want to be very sure it still does this. But then how is it different from test cases derived with test design techniques?

the distinction is in the moment of discovery, so no rephrasing of requirements into test cases
perhaps I don't have a clear anwers and this is more of an exploration of meaning
how does this link to contemporary exploratory testing? to putting exploratory testing really early in the process?
	external imagination, not knowing (yet)
	ET is not at the end, it's part of the dev process, together with automation
	ET is exploring and evaluation once you've done something based on the requirements

Is the distinction in fact between requirements and test ideas? No, that's the ideal situation -> next part.

<!-- The opening paragraph of this post already listed some different interpretations of the moment of discovery between test cases and requirements. The more waterfall-like your process, the more you'll have a group of people involved early on defining requirements, and a different group later one defining test cases. They have a different background and somewhat different skills, so they use different formats.

In essence, though, they are doing the same thing. They are defining requirements and writing them down - either in the format of a requirement or of a test case. Or they are translating requirements to test cases and writing those down. -->



<!--
next post
if this is true, that reqs and test cases are equivalent, there's limited value in translating existing requirements into test cases, there is more value in discovering test cases that are not requirements yet as early as possible
hence ET, product as external imagination, hence thin vertical slices for richer exploration
-->




<!-- Actually, that kind of test case - any test case based on an explicit requirement - does not fit the statement that the distinction is in the moment of discovery. -->


<!-- a test case that's a directly translated required is not very interesting -->

<!-- what should be the line that divides? -->

<!-- The dividing line between what's a test case and a requirement is the question: is this input for creation or for evaluation? If it's for creation, it's a requirement; if it's for evaluation, it's a test case. -->

<!-- Which aligns with the thought that TDD is not about testing, but about specification. -->

<!-- Now you could argue, that it's possible to use test cases as input for creation. Of course, you can, but then they are requirements. The difference is not in how you title them, what template you use, the format you write them in. That's incidental, not the essense, superficial. The difference is what you do with them. -> answers and questions -->

Now you could argue, that requirements need validation too. You might think your requirement is a good one, but that doesn't mean it actually is. While that's true, and important and needed, in the end it's working software, something interactive, in its real-life context, that needs to be evaluated if it's good enough. Imagination can take you far, mock ups further, but in the end we need the software.


## (leftover) three process options

In an ideal but impossible world, we would be able to define all the requirements upfront, translate them all to test cases, automate all of those, and then we'd just have to build a piece of software that passes all the tests. It's like waterfall, but even better.

In an ideal world we could aspire to, we would define all the requirements and related test cases upfront (as far as feasible). And we'd have an initial list of test ideas prepared. As we build the software, we keep revisiting the requirements, the test cases, and the test ideas.

In the actual world, things are messier. We define requirements until we feel it's time to start building. Then we start building and testing, hopefully discovering additional requirements to a sufficient degree. That may not sound that different from the previous paragraph, but the difference is the lack of intentionality in the momnent of discovery of requirements and test cases. While in the second part of this post, we'll see how being deliberate about this moment, will lead to better testing and better software.

The distinction between the moment of discovery, is: did we discover this requirement through testing or through design?
Where we don't want to discover the requirements through testing, that we could have discovered through design. That's something for the next part.

<!-- The value of making the distinction between a requirement and a test case based on the moment of discovery, lies in the "or, what we will have built" in the previous paragraph. -->
<!-- IS IT THOUGH? Is this a poor version of part of the next post? -->

<!-- The value of making the distinction between a requirement and a test case based on the moment of discovery, lies in making us aware of that moment. It makes us notice if we discovered something as a requirement, or as a test case. And [once we notice](link://slug/an-approach-to-teaching-agile-20-years-after-the-agile-manifesto#noticing-options-principles) this, once we're aware, we can think if it was the right moment, if we might want to change it, make changes to influence when that moment of discovery happens. We can think about how where that moment falls, influences how we do software development. -->

<!-- What this means, is that anyting you discover early enough, is a requirement. Anything discovered later, is a test case. Discover it early and it's input for design and building. Discover it later and it's input for evaluation (aka [verification and validation](link://slug/three-arguments-against-the-verification-validation-dichotomy/)). This raises the question: where exactly is that dividing line between requirement and test case? And can we move that line? -->


<!-- lies in making us able to think about that moment discovery as a thing, as an event. As something that happens at a certain point in time(?) and where can change what exact point of time that is. -->

<!-- Did we discover this requirement as part of design, as input for building? Or did we discover it as part of evaluation, as input for testing? Did we discover this as part of design, as input for building? Or did we discover it though evaluation, as input for testing? -->


<!-- Now you could argue, that it's possible to use test cases as input for creation. Of course, you can, but then they are requirements. The difference is not in how you title them, what template you use, the format you write them in. That's incidental, not the essense, superficial. The difference is what you do with them. -> answers and questions -->


what I posted on [Mastodon](https://chaos.social/@joeposaurus/111963169048720039) and [LinkedIn](https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di) about three months ago

<!-- I do realize that I'm assuming that translating a requirement to a test case is trivial. Often enough, that's not the case. And arguably there are some requirements that are so difficult to translate into test cases, that for all practical purposes they are un-translatable. So in that sense the distinction I'm making here is more of a theoretical nature than a practical one: between test cases that are translations of requirements, even if in practice you wouldn't perform this translation, and test cases that are not and can not be translations of requirements. The latter are test ideas, where we're not sure what will happen and/or how we will evaluate what will happen. -->

<!-- This leaves a lot of space for these moments to happen. A requirement can be discovered months before a line of code is written, or in the case of TDD, mere seconds. The same for the discovery of a test case: it might be discovered months before the test executed, or in the case of exploratory testing, mere seconds. -->

<!-- That's not to say there is a straight line we can draw through our software development process, separating the period of discovering requirements from discovering test cases. -->
<!-- That's not a straight line we can draw through our software development process. We can't pinpoint a moment in time, where everything before is a test case, and everything after is a test case.different meanings to moment of discovery -->