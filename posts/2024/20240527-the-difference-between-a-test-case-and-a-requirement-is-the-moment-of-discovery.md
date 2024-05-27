<!--
.. title: The difference between a test case and a requirement is the moment of discovery
.. slug: the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery
.. date: 2024-05-27
.. category: software testing
.. tags: exploratory testing, quality engineering, semantics, software development, software testing, test cases
.. type: text
-->

There are several straightforward ways to distinguish a test case from a requirement. A test case tells you how to check some kind of thing about the application, a requirement tells you that the application should do some kind of thing. A test case is written by a tester, a requirement by a business analyst. A test case takes the shape of an action and an evaluation of the result, a requirement takes the form of a sentence like "product ABC shall do XYZ."[^1]

[^1]: At least according to NASA: [https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/](https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/)

A less straightforward, but more interesting way to distinguish a test case and a requirement, is this:

> The difference between a test case and a requirement is the moment of discovery.[^2]

[^2]: See [https://chaos.social/@joeposaurus/111963169048720039](https://chaos.social/@joeposaurus/111963169048720039) and [https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di](https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di)

In this post I want to explore the meaning of that statement. In the next post I'll explore how looking at requirements and test cases in this way, can help us to do better testing. So this post will be a bit more philosophical, the next one more practical.


<!-- TEASER_END -->


# About requirements and test cases

## What is a requirement?

A requirement describes some aspect of the thing we are building. It tells us what the thing should be or should do. Requirements are input for the building of software.

So a requirement is anything that the team as a whole believes the thing they're building should be or do. Early on something might be a requirement because the lead dev knows it to be. Later on, it might only be a requirement if it's part of the shared understanding within the team. While if it's only a passing thought of a single developer, not really.


## What is a test case?

A test case describes something we want to find out about the thing we're building. It tells us how we might learn something about the thing. Test cases are input for the evaluation of software.

In that sense, the term "test idea" might be more apt than "test case". Whenever someone says "test case", I always wonder what they mean exactly. Do they mean *"something we should test"*, so a test idea or a charter for [exploratory testing](https://pragprog.com/titles/ehxta/explore-it/)? Or *"if you do this in the application, this other thing should happen"*, so what would I call a test case? Or do they mean a list of steps with detailed descriptions of what to do and what to check, so a test script?


## Test cases that are translated requirements versus ones that aren't

While all three (test ideas, test cases, and test scripts), count as test cases for the purpose of this post, there is a distinction to be made between test cases and test scripts on the one hand, and test ideas on the other.

Test cases and test scripts are translations of requirements. There is an expected result. We know what the thing we're building, should do. That makes them rephrasings of the requirements. This is especially clear if you [create a test case through a formal test design technique](link://slug/the-test-case-an-epistemological-deconstruction). The test case is no more than the transformation of a requirement by an algorithmic test design technique.

With test ideas, on the other hand, there's no expected result specified upfront. They take the form of *"I wonder what would happen if ..."* and *"I'm curious about ..."* So the goal is to discover something first, and then to evaluate it. How to evaluate that discovery, might be immediately obvious in the moment of discovery. Or it might take some work to figure out how to evaluate it. To decide - in a sense - if you've found a feature or a bug.



# The difference lies in the when, not in the what

A requirement is an answer, a "should". It serves the purpose of design. A test case is a question, a "what if?". It serves the purpose of evaluation.

And still, they are the same thing. They both capture something that the thing we are building, should do. It's just that for a requirement we already know what it is. For a test case, sometimes we do (test cases and scripts) and sometimes we don't (test ideas).

So it's not the "what" that distinguishes a test case from a requirement, but the "when". The difference lies in the moment of their discovery. For a requirement the moment of discovery is while we are designing what we are going to build. For a test case it's while we are evaluating (or preparing to evaluate) what we have built.



# The moment of discovery

The value of distinguishing test cases from requirements by their moment of discovery, lies in making us aware of that moment - and where that moment fits in our processes. It lets us notice, when we discover something we expect of our software, if we discover it either as a requirement or as a test case, as part of design or as part of testing.

And [once we notice](link://slug/an-approach-to-teaching-agile-20-years-after-the-agile-manifesto#noticing-options-principles) this moment, this distinction, we can reflect on it. We have a new angle to explore how we might get better at either type of discovery. We can decide if we want to move that moment of discovery, either earlier or later. And it lets us ask the question: should some discoveries be moved to other side of that moment?

More on those questions in the next post.
