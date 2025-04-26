<!--
.. title: Testing as three stages of enquiry
.. slug: 
.. date: 2025-05-12
.. category: 
.. tags: 
.. type: text
.. description: 
-->

The product of testing is information. (The product of good testing is actionable, relevant information, but that's another blog post.) So how does that information come about?

In my post ["The nine skills of exploratory testing"](link://slug/the-nine-skills-of-exploratory-testing) I wrote:

> As you explore, as you try things and notice how what you're testing responds, you build a model of how something might work. This kind of thinking is called [abduction](https://plato.stanford.edu/entries/abduction/) or abductive reasoning.

If you follow that link, you'll notice that it covers *"abduction in the modern sense"*, but that there's also a historical sense *"which had its origin in the work of Charles Sanders Peirce"*.

This historical sense is described in the supplement ["Peirce on Abduction"](https://plato.stanford.edu/entries/abduction/peirce.html), which refers to Fann 1970 for a *"a concise yet thorough account of the development of Peirce’s thoughts about abduction"*. So of course I bought that book, i.e. "Peirce's Theory of Abduction" by K. T. Fann. (I really like that this 63-page book that's over a 50 years old, apparantly is __the__ reference on this topic.)

And in that book I found something more interesting than just abduction: Peirce's three stages of inquiry. Or how the three phases of the methodology of science are abduction - deduction - induction. And it seem to me that testing works in a very similar way.[^1]

[^1]: I very deliberately wrote "in a very similar way". Because this blog post is no more than that: noticing an interesting similarity between what I understand of Peirce's thoughts based on Fann's book and what I believe about testing. If I'd want to make a stronger claim, e.g. about the similarities between testing and science, or about Peirce correctly describing the scientific method, I'd have to do a lot more reading and studying.


<!-- TEASER_END -->


# The three stages of inquiry

Let's look at each three of these in a little more detail and then in the next section how they might relate to testing

The first stage of inquiry, abduction, starts with noticing a surprising fact. Now an explanation is required. So we adopt a hypothesis as suggested by the facts. This hypothesis should be able to explain the observed facts. We adopt it on probation only. It must be tested.

Then we move on to the second stage, deduction. What are the necessary and probable consequences of the hypothesis? If our hypothesis is true, what else has to be true as well? Since we want to test our hypothesis, at least some of these consequences must be testable. (The hypothesis itself is not testable, since it's an explanation.)

Finally, we proceed to the third and last stage, induction. We test our hypothesis by running experiments. Either the consequences we deduced hold true, supporting our hypothesis. In that case we can either decide we're done or deduce additional consequences to test. Or, the consequences do not hold true, invalidating our hypothesis. In that case we return to the abduction stage, trying to come up with a new hypothesis.

Or as K.T. Fann summarizes in the Introduction of their book:

> Peirce conceived of the three kinds of reasoning as three stages of inquiry. Abduction invents or proposes an hypothesis; it is the initial proposal of an hypothesis on probation to account for the facts. Deduction explicates hypotheses, deducing from them the necessary consequences which may be tested. Induction consists in the process of testing hypotheses. Thus, "Abduction is the process of forming an explanatory hypothesis. It is the only logical operation which introduces any new ideas; for induction does nothing but determine a value, and deduction merely evolves the necessary consequences of a pure hypothesis" (5.171). *- Fann, p10*


# The three stages and testing

At a surface-level there's a clear similarity between the three stages of inquiry and testing. Abduction is coming up with test ideas, with things you want to test. Deduction is coming up with the actual tests informed by those test ideas. And induction is when you execute those tests.

While I agree with that similarity, it's not very informative. To get somewher interesting, we need to dig a little deeper.


## Abduction

Testing includes looking for surprisings facts.

In testing you have the written requirements.


## Deduction


how many experiments/observations are needed? in testing often one or lots

## Then what



## Summary of the three stages

In the Introduction Fann describes the three stages of inquiry as follows:




# Optimizing for moments of discovery


A (the?) key aspect of abduction is that it's only one of the three stages that 
synthetic


# Affinity between man and nature

built by man versus built by nature

---

TODO:
- link from here to the part about abduction in The nine skills of exploratory testing
- link from here to being intentional about exploratory testing
- link from here to espitemological deconstruction

---

#  Verification

Abduction is adopting a hypothesis as suggested by the facts. We notice a surprising fact and now an explanation is required. A good hypothesis explains the observed facts (the facts must follow from the hypothesis deductively) and its conclusions are capable of verification[^2]. A hypothesis is always adopted on probation and must be tested.

[^2]: Peirce died 20 years before Karl Popper published "Logik der Forschung". [Karl Popper's Wikipedia page](https://en.wikipedia.org/wiki/Karl_Popper#Falsifiability_and_the_problem_of_demarcation) however states "This[sic] Popper's falsifiability resembles Charles Peirce's nineteenth-century fallibilism. In *Of Clocks and Clouds* (1966), Popper remarked that he wished he had known of Peirce's work earlier."

# Three stages

> Scientific method begins with abduction or hypothesis: because of some perhaps surprising or puzzling phenomenon, a conjecture or hypothesis is made about what actually is going on. This hypothesis should be such as to explain the surprising phenomenon, such as to render the phenomenon more or less a matter of course if the hypothesis should be true. - https://plato.stanford.edu/entries/peirce/#dia

> Scientific method then proceeds to the stage of deduction: by means of necessary inferences, conclusions are drawn from the provisionally-adopted hypothesis about the obtaining of phenomena other than the surprising one that originally gave rise to the hypothesis. Conclusions are reached, that is to say, about other phenomena that must obtain if the hypothesis should actually be true. These other phenomena must be such that experimental tests can be performed whose results tell us whether the further phenomena do obtain or do not obtain. - https://plato.stanford.edu/entries/peirce/#dia

> Finally, scientific method proceeds to the stage of induction: experiments are actually carried out in order to test the provisionally-adopted hypothesis by ascertaining whether the deduced results do or do not obtain. - https://plato.stanford.edu/entries/peirce/#dia


> At this point scientific method enters one or the other of two “feedback loops.” If the deduced consequences do obtain, then we loop back to the deduction stage, deducing still further consequences of our hypothesis and experimentally testing for them again. But, if the deduced consequences do not obtain, then we loop back to the abduction stage and come up with some new hypothesis that explains both our original surprising phenomenon and any new phenomena we have uncovered in the course of testing our first, and now failed, hypothesis. Then we pass on to the deduction stage, as before. The entire procedure of hypothesis-testing, and not merely that part of it that consists of arguing from sample to population, is called induction in Peirce’s later philosophy. - https://plato.stanford.edu/entries/peirce/#dia
