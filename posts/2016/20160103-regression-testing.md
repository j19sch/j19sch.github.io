<!--
.. title: Regression testing, it means less than you think
.. slug: regression-testing-it-means-less-than-you-think
.. date: 2016-01-03 19:42:26 UTC+01:00
.. tags: regression testing, semantics, test strategy, test management
.. category: test strategy
.. link: 
.. description:
.. type: text
-->

The past weeks I have made several attempts at a blog post about regression testing. About how we use it to refer to different things: tests running on a CI server, people executing test scripts, etc. And about how often the term really doesn't mean much at all, yet nobody questions you when you use it: "What are you doing?" "Regression testing." "Oh good, carry on." The point of the post would be to argue we should use the term 'regression testing' a lot less, because most of the time we can be more specific without having to be more verbose.

However, the more I thought about (what I would qualify as) proper regression testing, the more I felt that regression versus progression (or progressive) testing is a distinction without difference. One interesting observation in this regard is that "regression testing" returns 30 times more results on Google than "progression testing" and "progressive testing" combined. So what's going on here if we have a dichotomy with one member producing so much more discussion than the other? And there's more: regression testing is commonly contrasted with test types like functional testing and usability testing. But how then should I categorize a regression test focusing on functionality[^1]?

<!-- TEASER_END -->

Anyhow, more thinking followed and the result is what you are reading here. A blog post describing four different things you could call regression testing. The first two I don't consider to be regression testing, the third one I find confusing and in the fourth I am reluctant to use the term at all.

Oh wait, I do have to provide a definition of regression testing for within this blog post, so here you go: Regression testing is testing the things you don't expect to observe any changes in.

### Regression testing as part of continuous integration
Situation: your regression test is a bunch of automated checks running on your CI server.

Although I see great value in this, it's debatable if this qualifies as testing. You commit your code and check if the build is green or red. If it goes red, you know there is a problem somewhere. If it stays green, you know the checks did not detect anything alarming and you move on. This is why people refer to these checks as change detectors[^2]. Because so far, no real testing is going on. On the other hand, you likely will do testing when you are investigating why the build went red. And testing was involved when you wrote the checks, and arguably when people decided how to run which checks on the CI server. So whether running these checks should be considered testing or not strongly depends on your choice of perspective.

More important for this blog post and referring back to the definition, the decision which checks to run has no relation to where we don't expect to see any changes. The checks that are run are simply the checks that the CI server has been configured to run. And some of those checks are checks you changed or created because of the code changes in your commit. So there really is no consideration for changed versus unchanged areas here, which means there is no good reason to call running these checks regression testing.

(Not directly relevant, but related and interesting: for a critique of the fully automated approach to regression testing, watch this short Whiteboard Testing video "[Regression Testing, the F.A.R.T Model](https://www.youtube.com/watch?v=P2PUXqasvGI)".)

*(edit 3 May 2023)* I revisited this topic in 2019: [*"Your CI/CD pipeline does not run regression tests"*](link://slug/your-ci-cd-pipeline-does-not-run-regression-tests)

### Regression testing with a suite of regression test scripts
Situation: you have a suite of test scripts you execute every time you perform a regression test.

The problem here is that you have the worst of two worlds: people trying to be like CI servers, executing the same test scripts every time, while that's not what people are good at. So it's time to make a choice: either go machine-centric and automate it all, or go human-centric and give them more freedom[^3]. In any case, what's going on here, is not regression testing. It's slow, error-prone change detection, again with no consideration what has and what hasn't been changed.

### Regression testing by doing actual testing
Situation: you identify the things you don't expect to observe any changes in and you test those.

This is the part where my thoughts become a little messy. Let's start with some questions:

- How do you decide that something is a thing[^4]?
- When deciding what is a thing and what isn't, why do we so strongly prefer modules and interfaces as things[^5]?
- How do we decide that a change in thing A should not have any effect on thing B?
- How do we know which observations are needed to decide that thing B is not affected by a change in thing A?

The answer to all of these questions is: a model. You need a model for all three activities: mapping out the application, deciding the impact of a change, and designing your tests. However, if my model predicts there are no changes, how can that same model inform my test design? It provides me with no information whatsoever about what to focus my testing on. Wich shows that we should not be using the same model for all three activities. Even more, we should be using different models within all three activities.

However, that does not solve the problem of 'regression testing', the definition of which largely depends on the second activity: deciding where you don't expect any changes. And this decision is fully dependent on which model you use. What is regression testing according to one model, might be progression testing to a different model. So actually the distinction between regression and progression testing is based on our lack of knowledge and/or imagination to predict a change.

And this is where my understanding of 'regression testing' starts to break down. If you are testing a refactored feature, are you regression testing or progression testing? The code changed, so that's progression testing, but the behaviour of the feature hasn't, so you're regression testing. If you are testing a feature and you find no bugs in the feature as such, but you do find a regression bug related to the feature, would you say the feature works? If so, how does that even make sense? If one part of a workflow changes and I am testing the whole workflow, am I progression or regression testing? Or does that depend on where I find a bug, if any?

Ok, enough questions. Let's go over this one more time. A change was made in area A and none of my models predict an impact on area B. Why would I want to regression test area B? Two possible reasons: either I do not sufficiently trust my judgement, or Area B is so important, my judgement doesn't matter. So what I am acutally saying when I want to regression test area B, is that I have identified a low-risk area that's important enough that I want to test it. But then... how is this different from testing in general? Why would it need a separate term? Well, that's why we have a fourth and last section in this blog post.

### Regression testing without regression testing
Situation: whenever you test something, you consider what needs testing and you test it. Which is to say: you're testing a feature, a release, or a whatever, and you decide what testing will give you the information you're looking for.

This is what in my opinion we should be doing: test the things that are important enough to test. The notion 'regression testing' is not relevant in that discussion.

Does this mean that the term 'regression testing' is meaningless within this approach? No, it doesn't. It does mean that 'regression testing' is a lot less important as a concept. You might be testing a feature, focusing on usability. And you might not expect to find any issues, because it's a regression test, i.e. you don't expect the changes that were made, to have had any impact. Then it makes perfect sense to use the term, but at best 'regression test' is the fourth thing you mention, because only in the context of those other three things, it has any meaning.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2016/01/03/regression-testing-it-means-less-than-you-think/).*



[^1]: I'm definitely not the first one to notice this peculiarity, see e.g. [Arborosa's blog post about regression testing](http://arborosa.org/2015/07/31/regression-testing/): "such a definition [...] only provides the intention of this type, or should I say activity, of testing. Regression testing could still encompass any other testing type in practice."

[^2]: I am not sure who first used the term 'change detector' in this way. The oldest reference I could find is from 2005: Regression testing by Cem Kaner and James Bach.

[^3]: Just to be clear: machine-centric will involve humans and human-centric will involve machines. The question is: what's the focus? Humans supporting machines (i.e. machine-centric) or machines supporting humans (i.e. human-centric). And of course, until our robotic overlords are here, at the highest level what you do will be human-centric. (Afterwards too, actually, I hope.)

[^4]: Some further explanation for the less philosophically inclined: according to a city map, streets and buildings are things, but people and the weather are not. If your application is a city, what kind of map would you draw? What elements would it include and which would it omit?

[^5]: There's a more general blog post hidden in this question, expanding into the philosophical: why are most Western ontologies focused on things instead of processes?