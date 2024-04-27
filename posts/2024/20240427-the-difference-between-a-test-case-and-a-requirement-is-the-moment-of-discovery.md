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

## What's a test case?

Also note that when I say "test case", I don't necessarily mean a test case created with a test design technique, based on a requirement, with pre-conditions, input, and an actual result. Actually, that kind of test case - any test case based on an explicit requirement - does not fit the statement that the distinction is in the moment of discovery. Such a test case is a [reframed requirement](link://slug/the-test-case-an-epistemological-deconstruction), probably made more concrete and specific, but it is a translation of a requirement. As such it's static, the thought process took place in the creating of the requirement, especially with formal test design techniques, where everyone should come up with the same test cases when using the same technique on the same requirement. It's an algorithm.

Rather with "test case" I mean: here is something we need to find out about the application under test. Which means we don't know it yet. We might have a plausible guess of what would happen. And we might or might not have some expecations of what should happen.


## Where is the line that divides requirements from test cases?


# What does it help us do?

## Can we move the separation line?