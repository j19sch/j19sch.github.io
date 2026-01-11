<!--
.. title: Testing as three stages of enquiry
.. slug: 
.. date: 2026-01-01
.. category: 
.. tags: 
.. type: text
.. description: 
-->

The product of testing is information. (The product of good testing is actionable, relevant information, but that's another blog post.) So how does that information come about?

In my post ["The nine skills of exploratory testing"](link://slug/the-nine-skills-of-exploratory-testing) I wrote:

> As you explore, as you try things and notice how what you're testing responds, you build a model of how something might work. This kind of thinking is called [abduction](https://plato.stanford.edu/entries/abduction/) or abductive reasoning.

If you follow that link, you'll notice that it covers *"abduction in the modern sense"*, but that there's also a historical sense *"which had its origin in the work of Charles Sanders Peirce"*.

This historical sense is described in the supplement ["Peirce on Abduction"](https://plato.stanford.edu/entries/abduction/peirce.html), which refers to Fann 1970 for a *"a concise yet thorough account of the development of Peirce’s thoughts about abduction"*. So of course I bought that book, i.e. *"Peirce's Theory of Abduction"* by K. T. Fann. (I really like that this 63-page book that's over a 50 years old, apparantly is __the__ reference on this topic.)

And in that book I found something more interesting than just abduction: Peirce's three stages of inquiry. Or how - according to Peirce - the three phases of the methodology of science are abduction - deduction - induction. And it seems to me that testing works in a very similar way.[^1]

[^1]: I very deliberately wrote "in a very similar way". Because this blog post is no more than that: noticing an interesting similarity between what I understand of Peirce's thoughts based on Fann's book and what I believe about testing. If I'd want to make a stronger claim, e.g. about the similarities between testing and science, or about Peirce correctly describing the scientific method, I'd have to do a lot more research.


<!-- TEASER_END -->


# The three stages of inquiry

Let's look at each three of these in a little more detail and then in the next section how they might relate to testing.

The first stage of inquiry, abduction, starts with noticing a surprising fact. Now an explanation is required. So we adopt a hypothesis as suggested by the facts. This hypothesis should be able to explain the observed facts. Nota that we adopt it on probation only. It must be tested.

Then we move on to the second stage, deduction. What are the necessary and probable consequences of the hypothesis? If our hypothesis is true, what else has to be true as well? If we want to be able test our hypothesis, at least some of these consequences must be testable. (The hypothesis itself is not testable, since it's an explanation, an interpretation.)

Finally, we proceed to the third and last stage, induction. We test our hypothesis by running experiments. Either the consequences we deduced hold true, supporting our hypothesis. In that case we can either decide we're done or deduce additional consequences to test. Or, the consequences do not hold true, invalidating our hypothesis. In that case we return to the abduction stage, trying to come up with a new hypothesis.

Or as K.T. Fann summarizes in the Introduction of their book:

> Peirce conceived of the three kinds of reasoning as three stages of inquiry. Abduction invents or proposes an hypothesis; it is the initial proposal of an hypothesis on probation to account for the facts. Deduction explicates hypotheses, deducing from them the necessary consequences which may be tested. Induction consists in the process of testing hypotheses. Thus, "Abduction is the process of forming an explanatory hypothesis. It is the only logical operation which introduces any new ideas; for induction does nothing but determine a value, and deduction merely evolves the necessary consequences of a pure hypothesis" (5.171). *- Fann, p10*


# The three stages and testing

At a surface-level there's a clear similarity between the three stages of inquiry and testing. Abduction is coming up with test ideas, things you wonder about. Deduction is coming up with the actual tests based on those test ideas. And induction is when you execute those tests and interpret the results.

While I agree with that similarity, it's not very informative. To get somewhere interesting, we need to dig a little deeper. That, however, is something for the next post.
