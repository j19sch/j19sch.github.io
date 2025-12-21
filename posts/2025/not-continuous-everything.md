<!--
.. title: Not continuous everything!
.. slug: not-continuous-everything
.. date: 2025-12-21
.. category: ci\/cd
.. tags: ci/cd, quality engineering, risk
.. type: text
.. description: CI/CD is about risk, not speed.
-->

In Chapter 18 of "Taking Testing Seriously" (I skipped ahead, sue me), [Keith Klain](https://qualityremarks.com/) says:

> So much today is about "continuous everything" - continuous deployment, continuous integration - and speed. The pace at which people are doing things is really, really disruptive to thinking deeply about problems. Then the goal gets displaced from getting good products and services to customers quickly, and turns into, "How do we back something out quickly when we inevitably screw up?" It's continuous everything - except continuous thinking.  
> *- Taking Testing Seriously, Bach, Bolton et al., 2025, p. 424*

He has a point. But I got there by first kind of disagreeing with what he said. Because "continuous everything" is not about speed. It's about risk. Or rather, about managing certain risks: the risk of (code) integration and the risks of delivery/deployment. And how fast you go, should not just be determined by those two specific risks. (Or even worse, by the fact that you just think it's really cool that you can release every commit to your users.) It should be determined by your overall risk appetite, which is a much broader perspective.


<!-- TEASER_END -->


# Not all software is the same

Not all software is created equally. [We do not all have the same job.](link://slug/we-do-not-all-have-the-same-job) Building a medical device is not quite the same as building a web app for your startup. Building a unified front-end across several backend systems, including a 40-year-old mainframe with life insurance policies, is different from building a video game.

The required level of safety is different. The complexity of the domain is different. The number and types of systems you need to integrate with is different. So are the types of systems and devices. The amount of experience within your team with the domain, the technologies, etc. probably is also different. The pressure from the market to release often is different. And so on and so on.

So many differences, all leading to different kinds of risk and different levels of risk. And to different levels of risk appetite. That risk appetite is what should inform how fast you're comfortable to go, not your technical capabilities.

Before elaborating further, however, I should probably clarify what I mean by "continuous integration" and friends.


# What is CI/CD?

__Continuous integration__ is developers integrating their code at least once a day. (Because merge conflicts are the worst.)  
__Continuous delivery__ is building the thing you will deploy with every (code) integration. (And do test the thing by deploying it somewhere.)  
__Continuous deployment__ is deploying the thing to production with every (code) integration. (A deploy doesn't also have to be a release.)  
__Releasing__ is making a piece of functionality available to your users. (Big bang or in steps, your choice.)

Continuous integration is at least as old as Extreme Programming (XP), where it is one of the primary practices. There it does include continuous delivery, though:

> Integrate and build a complete product. If the goal is to burn a CD, burn a CD. If the goal is to deploy a web site, deploy a web site, even if it is to a test environment. Continuous integration should be complete enough that the eventual first deployment of the system is no big deal.  
> *- Extreme Programming Explained 2nd ed., Kent Beck with Cynthia Andres, 2005, p. 50*

David Farley and Jez Humble extended that line of thought to deployment:

> Following the motto of Extreme Programming - if it hurts, do it more often - the logical extreme is to deploy every change that passes your automated tests to production. This technique is known as continuous deployment, [a term popularized by Timothy Fitz](http://timothyfitz.com/2009/02/08/continuous-deployment/). Of course it's not just continuous deployment (I can continuously deploy to UAT all I like: no big deal). The crucial point is that it is continuous deployment *to production*.  
> *- Continuous Delivery, Jez Humble and David Farley, 2011, p.266*

It's worth to note here that Timothy Fitz frames his blog post with a fictional story inspired by what he sees at *"most startups I know"*. As said previously, not all software is the same. And Humble and Farley are aware of this. They include *"manual test stages"* in their description of a deployment pipeline: *"These [manual test] stages might typically include exploratory testing environments, integration environments, and UAT (user acceptance testing)." (p. 110)* The goal is not to automate the whole process, but that *"error-prone and complex steps [to deliver software] are automated, reliable, and repeatable in execution." (p. 110)*


# So CI/CD does imply speed...

Doing both continuous integration and continuous deployment does imply speed. If developers integrate their changes on a shared branch at least once a day, and if every commit on that branch gets either deployed or reverted based on the quality gates in the CI/CD-pipeline, you are moving fast. [Charity Majors](https://charity.wtf/) has described this as: you write code in the morning and observe its behavior on production in the afternoon.[^1]

[^1]: If anyone has a source for this, I'll take it.

That might sound scary and that's fine, because continuous deployment is not always the right choice:

> Continuous deployment isn't for everyone. Sometimes, you don't want to release new features into production immediately. In companies with constraints on compliance, approvals are required for deployments to production. Product companies usually have to support every release they put out. However, it certainly has the potential to work in a great many places.  
> *- Continuous Delivery, Jez Humble and David Farley, 2011, p.267*

So what if we just did continuous integration and continuous delivery? We integrate code often, because the longer we wait with that, the riskier it gets. And when we integrate, we deploy to a test environment, because just as you're releasing a hotfix, is not the time you want to find out your deployments are horribly broken. That sounds sensible rather than scary, no?

And it moves the focus of "continuous everything" away from speed and towards risk again.


# but the main point is risk

Framing CI/CD in terms of risk instead of speed, is also exactly what James Shore does in his book "The Art of Agile Development" (note that he uses "continuous integration" in the XP-sense of including delivery):

> The ultimate goal of continuous integration is to make releasing a *business* decision, not a *technical* decision. When on-site customers are ready to release, you push a button and release.
> *- The Art of Agile Development 2nd ed., James Shore, 2021, p. 344*

It's the development team saying: *"We can release what we have built at any time. Do you want us to?"* It's about mitigating as much of the technical risks as possible, leaving the business risks. Hence it's the "on-site customer" that gets to decide if they're ready to release. And that way CI/CD does become a valuable tool for (in Keith's words) *"getting good products and services to customers quickly"*.

---

# Postscript {.small}

Originally I was planning to also address the "continuous thinking" Keith mentions, but it became a distraction from the main point. I can't help dropping some brief notes here, though.

The wonderful Thierry de Pauw has identified [16 practices that make continuous integration](https://thinkinglabs.io/articles/2022/06/14/the-practices-that-make-continuous-integration.html). And the book "Continuous Delivery" by Jez Humble and David Farley is over 400 pages long. So yeah, one does not simply do CI/CD.

There's more to it than that, though. As [Thierry points out](https://thinkinglabs.io/articles/2024/09/15/the-practices-that-make-continuous-integration-make-the-build-self-testing.html):

> Note, that I say those automated tests prevent regressions, not bugs. __Tests do not prove the absence of bugs.__ In the end, those automated tests are only checks. They check the things we know about our IT systems. They do not tell us anything about the things we do not know. The __bugs lie in the unknowns.__ We can try to find them with Exploratory Testing in a staging environment or better in production with features turned off for users.

And Humble and Farley agree, mentioning exploratory testing as part of establishing effective feedback loops for the naturally iterative process that is software development. (p.89-90)

So there has to be thinking at or near the end of your CI/CD pipeline. Through exploratory testing and through other means.

However, and I feel this rarely gets mentioned, there also needs to be thinking before your CI/CD pipeline. A development team that understands the domain, their mission, and how their current work contributes to that mission, will be delivering a lot more value than a team that continuously deploys to production just to see what sticks.
