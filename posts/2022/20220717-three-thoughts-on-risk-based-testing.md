<!--
.. title: Three thoughts on risk-based testing
.. slug: three-thoughts-on-risk-based-testing
.. date: 2022-07-17 11:56:30 UTC+02:00
.. tags: coverage, software testing, test management, test strategy, risk
.. category: test strategy
.. link: 
.. description: 
.. type: text
-->

The past month I've been thinking about risk-based testing. This post collects three thoughts on risk-based testing I kept returning to.


# If not based on risks, then based on what?

About a month ago I [tweeted](https://twitter.com/j19sch/status/1533760354647523330):

> What are the alternatives to risk-based testing?  
Requirements-based? I'd argue that's a subset of risk-based.  
Unguided? That's either a bad idea ("we hope to get lucky") or aimed at the risk of unknown unknowns.  
Any other options? Because something about the term is bothering me.

My question was inspired by the ["opposite" heuristic](https://smallsheds.garden/slides/rtc2019-testing-types.html#/15/0/1) from my talk about [testing types](https://smallsheds.garden/slides/rtc2019-testing-types.html#/): if we have some kind of category, what's the name for the things not in that category? Applied to risk-based testing: what's the name for testing that's not risk-based?

<!-- TEASER_END -->

From the responses to my tweet it became clear I was not the only one bothered by the term. My plan was to write a blog post inspired by these responses. However, one of the people who replied, [James Thomas](http://twitter.com/qahiccupps), beat me to it. He wrote a great blog post titled ["Risk-Based Testing Averse"](https://qahiccupps.blogspot.com/2022/06/risk-based-testing-averse.html). In it he accepts [the point](https://twitter.com/StooCrock/status/1533769843572453378) made by [Stu Crock](https://twitter.com/StooCrock) that everything is risk-based. If that's all there is to it, however, "risk-based testing" becomes a meaningless term:

> "If risk is endemic then it loses any explanatory value."

And that's not how James uses the term "risk" in relation to his work:

>  "I want conversations about [the risk of what, to who, and when](https://qahiccupps.blogspot.com/2019/09/of-what-to-who-when.html). If I'm doing (what I would call) risk-based testing I'm operating at this lower level."

I'm still not sure if I'll actually start using the term "risk-based testing" any time soon, but the usage as described by James does make sense to me.



# Different forms of risk-based testing

Recently I was asked to guide teams towards risk-based testing. I responded by asking which of the four following forms of risk-based testing they were interested in.

**1. prioritize test case execution based on risk**  
You add a "risk level" to each test case and after you have selected the test cases you want to execute, you sort them on "risk level" to determine the order of execution.

**2. test approach for stories and/or epics based on risks**  
Based on your understanding[^1] of a story or epic, you come up with risks, i.e. scenarios that you either want to happen or want to avoid from happening. You then design your tests based on those risks or scenarios.

**3. (pre-)refinement of stories and/or epics based on risks**  
Instead of waiting until you almost need to start testing as in the previous form, you come up with the risks during (pre-)refinement. The risks are then not only input for testing, but also for design and development.

**4. test strategy for a project based on risks**  
This is similar to option 2, but with a larger scope: the whole project instead of a story or an epic. As a result the risks will also be more high-level. This makes this form of risk analysis less useful as input for test design. It can be useful to direct the testing effort as a whole based on risks.



# More to it than impact times likelihood
A long time ago I was taught to determine the risk level by thinking about impact and likelihood[^2]. Impact was the impact on the user or on the business. Likelihood could be split into chance of failure and frequency of usage.

Thinking about risk-based testing made me remember this lesson and made me realize I've been using a more fine-grained list to think about how big and bad a risk is:

- impact
	- impact on the user and/or customer
	- impact on the company
	- ease/speed of discovery when something goes wrong
	- ease/speed of recovery after something went wrong
	- ease/speed of putting a workaround in place
	- ease/speed of fixing the underlying issue
- chance of failure
	- level of complexity of the process
	- level of complexity of the code
	- number of dependencies in the code
	- number of recent code changes in this area
	- amount of technical debt
- frequency of usage or of occurrence

Without a doubt this list is far from complete. It does illustrate, however, that if you discuss risk only at the level of impact and likelihood, you are going to miss things.


[^1]: A good understanding requires a variety of perspectives.

[^2]: Sometimes people assign numerical values to both and multiply these to determine the risk level. I think that's problematic, but won't go into that today.