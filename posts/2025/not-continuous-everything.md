<!--
.. title: Not continuous everything!
.. slug: not-continuous-everything
.. date: 2025-12-21
.. category:
.. tags:
.. type: text
.. description: CI/CD is about risk, not speed
-->

In Chapter 18 of "Taking Testing Seriously" (I skipped ahead, sue me), [Keith Klain](https://qualityremarks.com/) says:

> So much today is about "continuous everything" - continuous deployment, continuous integration - and speed. The pace at which people are doing things is really, really disruptive to thinking deeply about problems. Then the goal gets displaced from getting good products and services to customers quickly, and turns into, "How do we back something out quickly when we inevitably screw up?" It's continuous everything - except continuous thinking. (Taking Testing Seriously, Bach, Bolton et al., 2025, p. 424)

He has a point. But I got there by first kind of disagreeing with his statement. Because "continous everything" is not about speed. It's about risk. Or rather, about managing certain risks: the risk of integration and the risks of delivery/deployment. And how fast you go, should not just be determined by those two specific risks. Or even worse, by the fact that you think it's really cool that you can release every commit to your users. It should be determined by your overall risk appetite, which is a much wider view.

Moreover, the focus on speed hides all the thinking and practices that need to be in place to actually do continuous integration and continious deployment, and do it well.

<!-- TEASER_END -->

# Overall risk appetite
Not all software is created equally. We do not all have the same job. Building a medical device is not quite the same as building a web app for your startup. Building a unified front-end across several backend systems, including a 40-year-old mainframe with life insurance policies, is different from building a video game.

The required level of safety is different. The complexity of the domain is different. The number and types of systems you need to integrate with is different. So are the types of devices. The amount of experience within your team with that particular system probably is also different. The pressure from the market to release often is different. Etc. etc.

So many differences, all leading to different kinds of risk and different levels of risk. And to different levels of risk appetite. That's what should inform how fast you're comfortable to go.


# But what is CI/CD?

Before highlighting the thinking and practices required for continuous integration and continuous deployment, I should probably clarify what I mean by those terms.

Continuous integration is developers integrating their code at least once a day. (Because merge conflicts are the worst.)
Continuous delivery is building the thing you will deploy. (And do test the thing by deploying it somwhere.)
Continous deployment is deploying the thing to production. (A deploy doesn't also have to be a release, though.)
Releasing is making a piece of functionality available to your users. (Big bang or in steps, your choice.)

Continous integration is at least as old as Extreme Programming, where it is one of the primary practices. There it does include continuous delivery, though:

> Integrate and build a complete product. If the goal is to burn a CD, burn a CD. If the goal is to deploy a web site, deploy a web site, even if it is to a test environment. Continuous integration should be complete enough that the eventual first deployment of the system is no big deal. (Extreme Programming Explained 2nd ed., Kent Beck with Cynthia Andres, 2005, p. 50)

And to wrap back to the goal of CI/CD, James Shore uses this same definition when he states:

> The ultimate goal of continuous integration is to make releasing a *business* decision, not a *technical* decision. When on-site customers are ready to release, you push a button and release. (The Art of Agile Development 2nd ed., James Shore, 2021, p. 344) [continous integration in the XP sense, so deploy to test environment]

Which brings us back to risks and to the *"getting good products and services to customers quickly"* Keith mentions, and away from *"How do we back something out quickly when we inevitably screw up?"*

Which is something the authors of "Continuous Delivery" agree with:

> Deployment pipelines are all about creating a repeatable, reliable, automated system for getting changes into production as fast as possible. It is about creating the highest quality software using the highest quality process, massively reducing the risks of the release process along the way. (Continuous Delivery, Jez Humble and David Farley, 2011, p.267)


# Thinking before

The Practices That Make Continuous Integration
Thierry de Pauw
https://thinkinglabs.io/articles/2022/06/14/the-practices-that-make-continuous-integration.html
16 practices that can be split into three categories


# Thinking after


# Conclusion
Doing CI/CD has become like Agile: something you do for legitimacy, not for the benefits. You need to be able to point to a CI/CD pipeline, even though you do neither CI, nor CD. Because doing it for the benefits, actually is a lot of hard work.

---




Continuous Integration

> Integrate and test changes after no more than a couple hours. Team programming isn't a divide and conquer problem. It is a divide, conquer, and integrate problem. The integration step in unpredictable, but can easiliy take more time than the original programming. The longer you wait to integrate, the more it costs and the more unpredictable the cost becomes. (Extreme Programming Explained 2nd ed., Kent Beck with Cynthia Andres, 2005, p. 49-50)

> Integrate and build a complete product. If the goal is to burn a CD, burn a CD. If the goal is to deploy a web site, deploy a web site, even if it is to a test environment. Continuous integration should be complete enough that the eventual first deployment of the system is no big deal. (Extreme Programming Explained 2nd ed., Kent Beck with Cynthia Andres, 2005, p. 50)

---

> Following the motto of Extreme Programming - if it hurts, do it more often - the logical extreme is to deploy every change that passes your automated tests to production. This technique is known as continous deployment, a term popularized by Timothy Fitz. Of course it's not just continuous deployment (I can continuously deploy to UAT all I like: no big deal). The crucial point is that it is continuous deployment *to production*. (Continuous Delivery, Jez Humble and David Farley, 2011, p.266)

mention of canary releases on p. 267

> You have to write all your tests - including acceptance tests - first, so that only when a story is complete will check-ins pass the acceptance tests. (Continuous Delivery, Jez Humble and David Farley, 2011, p.266)

> Continuous deployment isn't for everyone. Sometimes, you don't want to release new features into production immediately. In companies with constraints on compliance, approvals are required for deployments to production. Product companies usually have to support every release they put out. However, it certainly has the potential to work in a great many places. (Continuous Delivery, Jez Humble and David Farley, 2011, p.267)

> Deployment pipelines are all about creating a repeatable, reliable, automated system for getting changes into production as fast as possible. It is about creating the highest quality software using the highest quality process, massively reducing the risks of the release process along the way. (Continuous Delivery, Jez Humble and David Farley, 2011, p.267)

---

> The ultimate goal of continuous integration is to make releasing a *business* decision, not a *technical* decision. When on-site customers are ready to release, you push a button and release. (The Art of Agile Development 2nd ed., James Shore, 2021, p. 344) [continous integration in the XP sense, so deploy to test environment]