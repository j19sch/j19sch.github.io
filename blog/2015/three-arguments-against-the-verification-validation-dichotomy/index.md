<!--
.. title: Three arguments against the verification-validation dichotomy
.. slug: three-arguments-against-the-verification-validation-dichotomy
.. date: 2015-03-24 20:53:24 UTC+01:00
.. tags: exploration, semantics, verification and validation
.. category: philosophy of testing
.. link: 
.. description:
.. type: text
-->

Last week while talking with two colleagues, one of them mentioned the verification/validation thing. And I noticed it made me feel uneasy. Because I know well enough what is meant by the distinction, but on a practical level I simply can't relate to it. When I think about what I do as a software tester and how verification versus validation applies to it, nothing happens. Blank mind. Crickets. Tumbleweed.
So after giving it some thought, I present you with three arguments against the verification-validation dichotomy.

First of course, we have the obligatory interlude of defining these two terms. A place to start is the Wikipedia page on [Software verification and validation](http://en.wikipedia.org/wiki/Software_verification_and_validation). Unfortunately it contains conflicting definitions, so if anyone cares enough, please do fix. Luckily there's also the general [Verification and validation](http://en.wikipedia.org/wiki/Verification_and_validation) page of Wikipedia, which gives us (among others) the tl;dr version of the distinction:

- Verification: *Are we building the product right?*
- Validation: *Are we building the right product?*

Finally there's the [ISTQB glossary v2.4](http://www.istqb.org/downloads/finish/20/145.html) that borrows from ISO 9000:

- Verification: *Confirmation by examination and through provision of objective evidence that specified requirements have been fulfilled.*
- Validation: *Confirmation by examination and through provision of objective evidence that the requirements for a specific intended use or application have been fulfilled.*

Now on to the three arguments.

<!-- TEASER_END -->

## 1. It screams V-model, silos and contracts.
When talking about verification vs validation, there is the (often implicit) assumption that we do verification first and then validation. That makes sense, if you ask someone else to build something for you. The developer in question can more easily verify (Am I building what I was asked to build?) than validate (Is this fit for my client's purpose?).

The next step is to realize that in such cases client and developer are most likely in different departments or perhaps even companies. So we need to decide who's responsible for what, who will pay for what, etc. And we might as well write that down somewhere in some sort of agreement or contract. The most sensible way to divide responsibilities, is to make the developers responsible for building what was designed and thus verification. The client will be responsible for the validation during what is often called acceptance tests. (Admittedly, there may be some verification first in those acceptance tests.)

In this context, one of assigning responsibilities within a contract, it makes sense to distinguish between verification and validation. As a result (bonus?) you enter the domain of utterances like: "That's not a bug, that's a change request." and "Hey, works as designed." (Or as some developers I know, lacking a proper design document, said: "Hey, works as built.")

As a tester doing actual testing, however, I honestly don't care. I don't ask: Am I doing validation or verification here? I do ask: Could there be a problem here?

Oh, and as a member of a sufficiently agile team, I don't think I care that much either.

## 2. There are more sources for test ideas.
Looking at the definitions there are only two sources for test ideas: "the specified requirements" (verification) and "the requirements for a specific intended use or application" (validation). Contrast this with the [Little Black Book on Test Design](http://www.thetesteye.com/papers/TheLittleBlackBookOnTestDesign.pdf) by [Rikard Edgren](http://thetesteye.com/blog/author/rikarde/) which contains 37 [sic] sources for test ideas divided into 6 categories: Product, Business, Team, Project, Stakeholders, External.

There are several ways you could try to map each of these 37 sources to either verification or validation and perhaps you would even succeed. However, does that make sense for test idea sources like rumors, product image or debt? More importantly, why limit yourself to a list with two items when you can use one with thirty-seven?

## 3. What about asking non-confirmatory questions?
Both verification and validation are defined as a form of confirmation (just reread the definitions, it's the first word in there). They're focused on the question: how might the product work? Yet in testing, there are two other questions that are at least as interesting: How might the product not work? and What can we make the product do?

My favorite description of the job of a software tester is: making software do interesting things. (Sometimes I still find it hard to believe you can get paid for that.) Some things are interesting because they show how the product might work; other things because they show how the product might not work. And yet other things are interesting because we're not quite sure if it falls into the working or not-working category, but we really should make an effort to find out.

Within the verification-validation distinction, however, this whole area of exploration, investigation and experimentation is nowhere to be found. All we do is confirm against requirements.

<br />
And with that I say goodbye to another concept of traditional testing methodologies, because it has no use to me. So goodbye to both of you, verification and validation. Am surprised it lasted as long as it did.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2015/02/10/three-arguments-against-the-verification-validation-dichotomy/).*
