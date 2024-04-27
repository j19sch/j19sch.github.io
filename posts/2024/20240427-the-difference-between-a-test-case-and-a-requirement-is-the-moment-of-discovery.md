<!--
.. title: The difference between a test case and a requirement is the moment of discovery
.. slug: the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery
.. date: 2024-04-27
.. category: 
.. tags: 
.. type: text
-->

About two months ago, I said [on Mastodon](https://chaos.social/@joeposaurus/111963169048720039) and [LinkedIn](https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di?utm_source=share&utm_medium=member_android):

> The difference between a test case and a requirement is the moment of discovery.

Put simply, any discovery about the product made early enough in the process, is a requirement. If it's made later than some dividing line (we'll get into that in a minute), it's a test case. Early means it's input for design and building; later means it's input for evaluation (or [verification and validation](link://slug/three-arguments-against-the-verification-validation-dichotomy/), if you prefer those terms.)

While I'm quite happy with it as an aphorism, often aphorisms are not more than that. Cool things you can say, responded to with thoughtful nods. I'd like to be something more. It would be nice if you could do something with it. Use it as a heuristic. Before we go into the practical aspect, though, I first want to take some time to explore what this aphorism is telling us about test cases, requirements, and the dividing line between the two.

<!-- TEASER_END -->

# What does it even mean?

## What's a requirement?

Which also leads us to the Alistair Cockburn quote that I discovered thanks to Maaret Pyhäjärvi:

> If it's your decision to make, it's design. If it's not, it's a requirement.

But that's for another post.

In a sense, requirements are dead. Requirements are answers (even if tenuous). Test cases are questions.

A requirement is a "should", a test case a "what if?"


## What's a test case?

Also note that when I say "test case", I don't necessarily mean a test case created with a test design technique, based on a requirement, with pre-conditions, input, and an actual result. Actually, that kind of test case - any test case based on an explicit requirement - does not fit the statement that the distinction is in the moment of discovery. Such a test case is a [reframed requirement](link://slug/the-test-case-an-epistemological-deconstruction), probably made more concrete and specific, but it is a translation of a requirement. As such it's static, the thought process took place in the creating of the requirement, especially with formal test design techniques, where everyone should come up with the same test cases when using the same technique on the same requirement. It's an algorithm.

Rather with "test case" I mean: here is something we need to find out about the application under test. Which means we don't know it yet. We might have a plausible guess of what would happen. And we might or might not have some expecations of what should happen.


## Where is the line that divides requirements from test cases?

The dividing line between what's a test case and a requirement is the question: is this input for creation or for evaluation? If it's for creation, it's a requirement; if it's for evaluation, it's a test case.

Which aligns with the thought that TDD is not about testing, but about specification.

Now you could argue, that it's possible to use test cases as input for creation. Of course, you can, but then they are requirements. The difference is not in how you title the, what template you use, the format you write them in. That's incidental, not the essense, superficial. The difference is what you do with them. -> answers and questions

Now you could argue, that requirements need validation too. You might think your requirement is a good one, but that doesn't mean it actually is. While that's true, and important and needed, in the end it's working software, something interactive, in its real-life context, that needs to be evaluated if it's good enough. Imagination can take you far, mock ups further, but in the end we need the software.


# What does it help us do? help us see? do differently?

## Exploratory testing is key / The exploratory part to testing is crucial

If I could tell you in detail what and how I would test upfront, I'd add those as requirements / acceptance criteria from the start. Then you could build it right/correct from the start, instead of having me test it afterwards.

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