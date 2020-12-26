<html><body><h2>CI/CD pipelines</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>The purpose of a CI/CD pipeline is to allow you to deliver small changes in a fast and controlled way. Without any tests in your pipeline you would gain a lot of speed. You'd also lose a lot control, which is why people in general do run tests in their pipeline. The purpose of these tests is to check if that stage of the pipeline meets the minimum level of acceptable quality for that stage.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>For example, commit stage tests will consist of mostly unit tests, a few integration tests, and even fewer end-to-end tests, because early in the pipeline speed is more important than comprehensiveness. When I commit my changes, I want the results fast enough so that I will wait for them - ready to fix any issue that might occur.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Regression testing</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>There are many definitions of regression testing, as you can read in <a href="https://arborosa.org/2015/07/31/regression-testing/">Arborosa's blog post on the topic</a>. I have always defined regression testing along the lines of "testing the parts that weren't impacted by a change to see if they really weren't impacted." (Which is really weird if you start thinking about it: something is regression testing depending on your knowledge of the system and the change.)</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>The tests in your pipeline are regression tests, ...</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Most of the tests that run in your pipeline are regression tests. Your commits are small and you have a lot of tests, so most of those will cover parts of the system that shouldn't have been impacted by your changes. So yes, regression tests.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The one exception is if your commit contains both changes and new or updated tests related to that change. For that one run of the pipeline those tests are not regression tests. The next commit they are.<br>Or, since you ran those tests before committing, perhaps they already have become regression tests when they are executed by the pipeline?</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><em>Sidenote:</em><br><em>A grey area is when your commit is a pure refactoring, as in: you didn't even have to change any of the tests. On the one hand, you made a change, so the tests covering that change, are not regression tests. On the other hand, at the level these tests are defined, there should be zero impact, they shouldn't detect any changes. So in that sense they are regression tests.</em></p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>..., but that's irrelevant.</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>So sure, the tests run by your pipeline are regression tests. However, they are regression tests incidentally, not essentially. They happen to be regression tests, but that's not really relevant.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>To see why, we need to revisit the start of this blog post.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The purpose of a regression test is to check if unchanged parts of the system are indeed unchanged. It's the testing that got a name, so we could distinguish it from the other testing, which never really got a name. (Progression testing? Feature testing?) It's the testing you do after sufficient testing and fixing, when you're not expecting any more changes and you need to check if all the "other stuff" still works.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The purpose of a test in a CI/CD pipeline is to check the level of quality of a particular stage in the pipeline. The pipeline stages combined with all the practices that surround them, result in a continuous delivery of changes that can be deployed to production. Whether the tests at a particular stage are regression tests or not, doesn't matter. What does matter is if they provide the information required to decide if we should proceed to the next stage or not.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>And that's why I claim that your CI/CD pipeline does not run regression tests. The definition of "regression test" may technically apply to the tests run by your pipeline; the context that comes with the term, does not. So although it might (mostly) be correct to say that your pipeline runs regression tests, doing so is not helpful in how you think about your pipeline or about your tests. It moves your mind towards thinking about changed versus unchanged things - drawing it away from the continuous delivery of a good enough product.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><em>update August 6th</em>:<br>After publishing this post, I got the following question on  twitter: so how does this impact actual decisions? In response, I came  up with four things you might do if you think of the tests in your  pipeline as regression tests:<br>1. Not looking for regressions when exploratory testing because you already have so many regression tests.<br>2. Poorly designing the stages of the pipeline, because all it needs to do is just run those regression tests.<br>3. Doing exploratory testing too early in the pipeline, because you should do feature testing before regression testing.<br>4. Being lenient towards a failed pipeline because they're just regressions, we can fix them later.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>--- --- ---</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>p.s. 1: One thing I'm glossing over is that your CI/CD pipeline can (should) have stages in which the testing involves a human. I don't think it makes a difference for my argument. Yet I'm still conveniently limiting the scope of this post to the literal interpretation of "Your CI/CD pipeline does not run regression tests".</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>p.s. 2: None of the ideas in this blog post are new, which you can see from the replies in <a href="https://twitter.com/j19sch/status/1158294444761731072">the twitter thread</a> that lead me to writing this blog post.</p>
<!-- /wp:paragraph --></body></html>