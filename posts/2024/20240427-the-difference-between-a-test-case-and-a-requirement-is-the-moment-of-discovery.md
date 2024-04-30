<!--
.. title: The difference between a test case and a requirement is the moment of discovery
.. slug: the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery
.. date: 2024-04-27
.. category: 
.. tags: 
.. type: text
-->

<!-- 
	goal of the post:
	- explain the meaning of the aphorism on its own
	- describe the (at least) three things we can do based on that aphorism

	not the goal:
	- make the aphorism the be-all-end-all on the distinction between test cases and requirements
 -->

There are several straightforward ways to distinguish a test case from a requirement. One is written by a tester, the other by a business analyst. One tells you how to check if the application does a specific thing, the other tells you that the application should do a specific thing. One has a format with pre-conditions, inputs, and expected results, the other takes the shape of "product ABC shall XYZ." (at least according to NASA[^1]).

[^1]: https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/

A less straightforward, but more interesting way to distinguish the two is:

> The difference between a test case and a requirement is the moment of discovery.

which I posted about two months ago [on Mastodon](https://chaos.social/@joeposaurus/111963169048720039) and [LinkedIn](https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di?utm_source=share&utm_medium=member_android).

What this means, is that anyting you discover early enough, is a requirement. Anything discovered later, is a test case. Discover it early and it's input for design and building. Discover it later and it's input for evaluation (aka [verification and validation](link://slug/three-arguments-against-the-verification-validation-dichotomy/)). This raises the question: where exactly is that dividing line between requirement and test case? And can we move that line?

That second (and similar) questions are crucial to me. It's one thing to come up with a nice aphorism. It's a lot more interesting to have an aphorism that can be a guide to improve some aspects of how you develop software.


<!-- TEASER_END -->

# What does it even mean? What does this thing even mean?

## What's a requirement?

Which also leads us to the Alistair Cockburn quote that I discovered thanks to Maaret Pyhäjärvi:

> If it's your decision to make, it's design. If it's not, it's a requirement.

But that's for another post.

In a sense, requirements are dead. Requirements are answers (even if tenuous). Test cases are questions.

A requirement is a "should", a test case a "what if?"


## What's a test case?

Test cases can take many forms. (Even thouh I suggested otherwise in the intro to this post.) They can vary from a test idea ("We should test this thing.") to a detailed description on how to test one particular thing.

The main characteristic is that they describe something we want to find out about the application under test. That means we don't know it yet. We might have a plausible guess of what would happen. And we might or might not have some expecations of what should happen.

<!-- Is this true? What about all the stuff that runs in the pipeline? I guess we know what it should do, but we do want to be very sure it still does this. But then how is it different from test cases derived with test design techniques? -->

<!--
	the distinction is in the moment of discovery, so no rephrasing of requirements into test cases
	perhaps I don't have a clear anwers and this is more of an exploration of meaning
	how does this link to contemporary exploratory testing? to putting exploratory testing really early in the process?
		external imagination, not knowing (yet)
		ET is not at the end, it's part of the dev process, together with automation
		ET is exploring and evaluation once you've done something based on the requirements
-->


Also note that when I say "test case", I don't necessarily mean a test case created with a test design technique, based on a requirement, with pre-conditions, input, and an actual result. Actually, that kind of test case - any test case based on an explicit requirement - does not fit the statement that the distinction is in the moment of discovery. Such a test case is a [reframed requirement](link://slug/the-test-case-an-epistemological-deconstruction), probably made more concrete and specific, but it is a translation of a requirement. As such it's static, the thought process took place in the creating of the requirement, especially with formal test design techniques, where everyone should come up with the same test cases when using the same technique on the same requirement. It's an algorithm.



## Where is the line that divides requirements from test cases?

The dividing line between what's a test case and a requirement is the question: is this input for creation or for evaluation? If it's for creation, it's a requirement; if it's for evaluation, it's a test case.

Which aligns with the thought that TDD is not about testing, but about specification.

Now you could argue, that it's possible to use test cases as input for creation. Of course, you can, but then they are requirements. The difference is not in how you title the, what template you use, the format you write them in. That's incidental, not the essense, superficial. The difference is what you do with them. -> answers and questions

Now you could argue, that requirements need validation too. You might think your requirement is a good one, but that doesn't mean it actually is. While that's true, and important and needed, in the end it's working software, something interactive, in its real-life context, that needs to be evaluated if it's good enough. Imagination can take you far, mock ups further, but in the end we need the software.

---


# What does it help us do? help us see? do differently?

what levers does this give us?
move the tipping point where requirements become test cases
test early, build quality in


## Exploratory testing is key / The exploratory part to testing is crucial

If I could tell you in detail what and how I would test upfront, I'd add those as requirements / acceptance criteria from the start. Then you could build it right/correct from the start, instead of having me test it afterwards. // if I can tell you what to test without exploring, it could have been a requirement

application is external imagination

discovery learning


## Can we move the separation line?
earlier is better

what if we can create a feedback loop between requiring and testing?

is this contemporary exploratory testing? credit Maaret Pyhäjärvi


In a sense, requirements are dead. Requirements are answers (even if tenuous). Test cases are questions. The trick is to limit test cases to only those questions that can be answered by exploring / interacting with the code / the application. The rest can be a requirement.



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