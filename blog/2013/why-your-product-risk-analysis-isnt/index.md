<!--
.. title: Why your Product Risk Analysis isn't
.. slug: why-your-product-risk-analysis-isnt
.. date: 2013-06-23 14:34:36 UTC+02:00
.. tags: test management, test reporting, test strategy
.. category: test strategy
.. link: 
.. description:
.. type: text
-->

Ok, going to try to keep this short and ranty (rantish?).

Typical test advice is to do a Product Risk Analysis (PRA, mind the capitalisation!) and based on that you decide what to test and how thoroughly. The most common way to do a PRA is with a workshop. Put some people in a room with a lot of stickies, let them list all the risks they can think of and then have them score them. Et voilà, Product Risk Analysis is done!

But that doesn't really make sense, now does it? If someone were to give you an object and asked you "What could possibly go wrong with this?", what would you do? Gather a bunch of people with some knowledge of the object, yet no actual experience with it and do a workshop imagining things that could go wrong? That's not an Analysis (capital A!), that's a SWAG – a scientific wild ass guess.

<!-- TEASER_END -->

Yet that's exactly what we do in software testing. After the workshop the PRA is done. It gets (at least!) version 1.0. But if the PRA is done, that is if we have a good analysis of the product risks, why do we need to test? Well of course, we didn't do a proper analysis, we did a SWAG and we want and need to do better.

It is through testing (and checking), through interacting and experimenting with the product, we can enhance our PRA from "best we can think of" to "this is what we observed". By testing we upgrade our risks from SWAG-status to three pieces of information: what works, what doesn't work and what hasn't been tested yet. Now that information is a lot more useful than what we got from our so-called PRA: "We have a moderate amount of fear it will fail and that would be fairly bad."

Now quite often the list of stuff that doesn't work is a bit too long, so we have a fixing phase. And that's cool. We just keep testing, until the person who gets to make the call, is happy with the three stories in our PRA (works, doesn't work, don't know). And that's when our Product Risk Analysis really is done, ready and finished: during our final test report.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2013/06/23/why-your-product-risk-analysis-isnt/).*
