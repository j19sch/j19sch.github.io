<!--
.. title: The difference between a test case and a requirement is the moment of discovery (part two)
.. slug: the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery-part-two
.. date: 2024-06-04
.. category: 
.. tags: 
.. type: text
-->

There are several straightforward ways to distinguish a test case from a requirement. A test case tells you how to check some kind of thing about the application, a requirement tells you that the application should do some kind of thing. A test case is written by a tester, a requirement by a business analyst. A test case consist of an action and an evaluation of the result, a requirement takes the form of a sentence like "product ABC shall XYZ." (at least according to NASA[^1]).

[^1]: https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/

A less straightforward, but more interesting way to distinguish the two is what I posted on [Mastodon](https://chaos.social/@joeposaurus/111963169048720039) and [LinkedIn](https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di) about two months ago:

> The difference between a test case and a requirement is the moment of discovery.

In this post I want to explore the meaning of that statement. In the next post I'll explore how looking at requirements and test cases in this way, can help us to do better testing.


<!-- TEASER_END -->


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

---

# leftovers

That second (and similar) questions are crucial to me. It's one thing to come up with a nice aphorism. It's a lot more interesting to have an aphorism that can be a guide to improve some aspects of how you develop software.

Requirements part of the design. Because I love the same word meaning different things in different contexts: "If it's your decision to make, it's design. If it's not, it's a requirement." - Alistair Cockburn.