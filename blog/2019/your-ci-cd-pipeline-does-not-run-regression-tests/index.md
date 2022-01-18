<!--
.. title: Your CI/CD pipeline does not run regression tests
.. slug: your-ci-cd-pipeline-does-not-run-regression-tests
.. date: 2019-08-05 23:47:51 UTC+02:00
.. tags: devops, ci/cd, regression testing, semantics, test automation
.. category: ci\/cd
.. link: 
.. description:
.. type: text
-->

## CI/CD pipelines
The purpose of a CI/CD pipeline is to allow you to deliver small changes in a fast and controlled way. Without any tests in your pipeline you would gain a lot of speed. You'd also lose a lot control, which is why people in general do run tests in their pipeline. The purpose of these tests is to check if that stage of the pipeline meets the minimum level of acceptable quality for that stage.

For example, commit stage tests will consist of mostly unit tests, a few integration tests, and even fewer end-to-end tests, because early in the pipeline speed is more important than comprehensiveness. When I commit my changes, I want the results fast enough so that I will wait for them - ready to fix any issue that might occur.


## Regression testing
There are many definitions of regression testing, as you can read in [Arborosa's blog post on the topic](https://arborosa.org/2015/07/31/regression-testing/). I have always defined regression testing along the lines of "testing the parts that weren't impacted by a change to see if they really weren't impacted." (Which is really weird if you start thinking about it: something is regression testing depending on your knowledge of the system and the change.)


## The tests in your pipeline are regression tests, …
Most of the tests that run in your pipeline are regression tests. Your commits are small and you have a lot of tests, so most of those will cover parts of the system that shouldn't have been impacted by your changes. So yes, regression tests.

<!-- TEASER_END -->

The one exception is if your commit contains both changes and new or updated tests related to that change. For that one run of the pipeline those tests are not regression tests. The next commit they are.
Or, since you ran those tests before committing, perhaps they already have become regression tests when they are executed by the pipeline?

*Sidenote:
A grey area is when your commit is a pure refactoring, as in: you didn't even have to change any of the tests. On the one hand, you made a change, so the tests covering that change, are not regression tests. On the other hand, at the level these tests are defined, there should be zero impact, they shouldn't detect any changes. So in that sense they are regression tests.*

## ..., but that's irrelevant.
So sure, the tests run by your pipeline are regression tests. However, they are regression tests incidentally, not essentially. They happen to be regression tests, but that's not really relevant.

To see why, we need to revisit the start of this blog post.

The purpose of a regression test is to check if unchanged parts of the system are indeed unchanged. It's the testing that got a name, so we could distinguish it from the other testing, which never really got a name. (Progression testing? Feature testing?) It's the testing you do after sufficient testing and fixing, when you're not expecting any more changes and you need to check if all the "other stuff" still works.

The purpose of a test in a CI/CD pipeline is to check the level of quality of a particular stage in the pipeline. The pipeline stages combined with all the practices that surround them, result in a continuous delivery of changes that can be deployed to production. Whether the tests at a particular stage are regression tests or not, doesn't matter. What does matter is if they provide the information required to decide if we should proceed to the next stage or not.

And that's why I claim that your CI/CD pipeline does not run regression tests. The definition of "regression test" may technically apply to the tests run by your pipeline; the context that comes with the term, does not. So although it might (mostly) be correct to say that your pipeline runs regression tests, doing so is not helpful in how you think about your pipeline or about your tests. It moves your mind towards thinking about changed versus unchanged things - drawing it away from the continuous delivery of a good enough product.

---

*update August 6th:*
After publishing this post, I got the following question on twitter: so how does this impact actual decisions? In response, I came up with four things you might do if you think of the tests in your pipeline as regression tests:

1. Not looking for regressions when exploratory testing because you already have so many regression tests.
2. Poorly designing the stages of the pipeline, because all it needs to do is just run those regression tests.
3. Doing exploratory testing too early in the pipeline, because you should do feature testing before regression testing.
4. Being lenient towards a failed pipeline because they're just regressions, we can fix them later.

---

p.s. 1: One thing I'm glossing over is that your CI/CD pipeline can (should) have stages in which the testing involves a human. I don't think it makes a difference for my argument. Yet I'm still conveniently limiting the scope of this post to the literal interpretation of "Your CI/CD pipeline does not run regression tests".

p.s. 2: None of the ideas in this blog post are new, which you can see from the replies in [the twitter thread](https://twitter.com/j19sch/status/1158294444761731072) that lead me to writing this blog post.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2019/08/05/your-ci-cd-pipeline-does-not-run-regression-tests/).*
