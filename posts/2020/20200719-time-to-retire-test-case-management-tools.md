<!--
.. title: It's time to retire our test case management tools
.. slug: its-time-to-retire-our-test-case-management-tools
.. date: 2020-07-19 16:38:17 UTC+02:00
.. tags: test cases, tools, test management, heuristics
.. category: test management
.. link: 
.. description:
.. type: text
-->

Recently the topic of test case management tools popped up a few times in my surroundings. In almost all cases I'd recommend against using these kinds of tools and I found myself able to give a few reasons, but also found that my thoughts lacked the clarity I'd like them to have. Hence this blog post, to force myself to think more deeply and communicate more clearly.

Before I go into that, there are a few things this blog post is not about. I won't be really going into what effect test cases have on test execution, or rather if test cases are a good tool to use when doing actual testing. Personally I don't think they are and I wrote about my inability to use them in [this post from July 2013](link://slug/test-cases-cant-do-m-no-more). For some deeper thoughts on this, I recommend James Bach's and Aaron Hodder's article "[Test cases are not testing: Towards a culture of test performance](https://www.testingcircus.com/documents/TestingTrapeze-2014-February.pdf#page=31)".

What I do want to cover in this post is managing test cases. Having a collection of test cases stored somewhere to re-use across releases and reporting their pass/fail numbers. Both are important use cases for a test case management tool and both are in my opinion a bad idea.

<!-- TEASER_END -->

Finally, thinking this through made me realize how incredibly hard it is to build a good test case management tool (if one would choose to build one). It needs to be super-responsive and fast to not slow down my thinking. However, it also needs to support synchronous collaboration and run on any computer. (On one project I had to execute tests on one machine, then update the test cases on a different machine in a different room afterwards.) It needs to support pictures (drawings?), videos and have loads of searchable fields. Navigating all that data should be easy and fast. I'd want to link releases to user stories, user stories to test case results, test case results to test cases but also user stories to features, and features to test cases. Which means that features and test cases need history because they are persistent, while releases, user stories and test case results relate to a fixed moment in time. Last but not least, it needs to have advanced features for super-users, while remaining welcoming for occassional - and even reluctant - users. In short, it's probably not worth the cost to build a really good one.


## What is a test case?
There seem to be two definitions of test cases floating around.

The first one is the one that matches those given by ISTQB, TMap, the IEEE Standard 610 (1990) and ISO 29119. A test case is a set of conditions, inputs, actions and expected results. The definition does not explicitly state that these test cases are the result of applying test design techniques, but that is how they expect you to specify your test cases.

The second is one I encounter more often: a test case is something you want to test, it's a relatively specific and concrete test idea.

To check my understanding I sent out [this tweet](https://twitter.com/j19sch/status/1282941488847093765):

> *Am working on a blog post and could use your input to check my own definitions and experiences:  
> 1. Do you use test cases in your testing?  
> 2. If so, what do they look like? Can you share an example?  
> 3. And do you record these test cases and their results in a test management tool?*  

It got four replies - which also tells us something, although I'm not sure what - with two people not using test cases, one person sort of using them describing them as "high level titles", and one person using them describing them as "list of steps and their expected results." As to test case management tools, the replies varied from "yes" to documenting in Jira/git/confluence to "No" because "I want people to actually read and review what I write".


## Re-using test cases

### A test case is an intermediate product
Testing requires test design and test execution. So test cases are really an intermediate product, since they are the result of test design. And the thing with intermediary products is that they have a limited shelf life. During exploratory testing design and executiom may be intertwined in a tight feedback loop. On the other end of the spectrum you may be designing your test for a few days before you move on to execution. In either case, however, the intermediary product that is the test case, does not become a final product. It does not become a thing on its own.

That does happen if we store test cases for re-use later, for example for next release's regression test. It reminds me of the days where a new tester would start with doing test execution and then would get "promoted" to doing test design. It suggests that all the thinking happens during design and all the doing happens during execution. In this way re-using test cases discourages thinking.

Of course, you can instruct people to keep thinking while they're executing tests. But why require people to fight the structures you have set up to organize the work? Why not set up a structure that encourages thinking instead?

### Re-use is a legacy of waterfall projects
Re-using test cases feels like a thing for waterfall projects. This big project kicks off for several months (or years). There is no software yet, but there is documentation, so you start writing test cases. The software is delivered and you start executing your test cases. You edit some test cases, add a few more. The software goes back for fixing. There's a second round of testing. Some of the first test cases you execute are the ones with which you found the bugs several weeks ago. There might be a second round of fixing and a third round of testing. Project done and in the final week you get time to edit/clean up your test cases and then they are archived for a potential future project.

If you still work that way, perhaps a test case management tool is a good idea. On the other hand, one time I was the lead of a team inheriting a collection of test cases written by others and I decided to to keep them archived and have my team start over. I figured resurrecting the old test cases would cost as much time as creating them anew. And starting over would result in deeper understanding and more sense of ownership.

If you don't work this way, if you work in a more agile manner, it becomes a wholly different discussion - as illustrated by my comment above about linking releases and user stories etc. If the software keeps changing, so must the test cases, requiring a similar level of agility from your tooling.

### It's like backlogs and defect trackers
Finally, managing a collection of test cases is challenging in the same manner it's challenging to manage a collection of work items in a backlog or a collection of defects in a defect tracker. (I was once part of a project where the new defects had an ID in the 3000s, the oldest open one had an ID of 42. When I brought this up with my test manager, he replied he had a filter to ignore any defect with an ID below 2000.) It takes a ridiculous amount of discipline and effort, and good tooling to manage a collection of test cases well.

### This is not about automation
Finally, note that I am not making the argument that if you want to re-use a test case, the solution is to just automate it. For the argument I am making here, it does not make a difference if the test is executed by a human or by a machine. And I don't think that automating manual test cases is a good approach to test automation. I won't go deeper into that here, but [this blog post of mine](link://slug/your-ci-cd-pipeline-does-not-run-regression-tests) about regression testing and CI/CD pipelines should give you an idea of my thoughts on the matter.


## Reporting test case results

### Test case coverage without formal test design is meaningless
Reporting test cases results (number executed, number passed, number failed) makes some sense if you are using formal test design techniques to create your test cases based on a set of requirements. The reason is that the number of test cases is determined by the techniques and the requirements. Give the same set to two different testers and they should come up with the same test cases. So the approach is: define all test cases as required by the test strategy, execute all the test cases and full coverage (in relation to the test stategy) achieved!

That's not how most software is tested. Informal test design techniques are used, where different testers come up with similar but not entirely the same set of test cases. You do some exploratory testing, where you usually don't identify individual test cases. Or perhaps the most common, your definition of test case is not the first one mentioned above, but the second one: "something I want to test".

Even with formally designed test cases, saying we have executed 73 of the 114 test cases has limited and only highly contextual meaning. When what a test case is becomes significantly vaguer, the same thing happens to a statement about how many of the (current) total you have executed.

### What about CI/CD pipeline results?
If you have a CI/CD pipeline running auto-tests, how do you report those results? You could import their results into your test case management tool, but that seems opposite to the intention of a CI/CD pipeline. The pipeline should be the single source of truth, not some other tool. It makes more sense to refer to the test case results in the pipeline. And even then, for the pipeline a green job is a green job. Do you need that reference in your pipeline - except for audit purposes?

### Pass/fail numbers are a poor converstation starter
Continuing the track of counting test cases, reporting pass/fail numbers of test cases is probably even worse. (One day a consultant showed me the test result dashboard of the test case management tool he was involved in rolling out. I said: "Oh yeah, I don't care about those kinds of dashboards." To which he replied: "That's curious. Usually people are excited about these dashboards, but I got the exact same response from you as I got from your manager.")

The problem with these numbers and counts and graphs is that it feels like they tell us something, it feels like we get a good overview of the current status, but in reality they don't. Now you might argue that these numbers can be a good way to start a conversation. A 90% pass rate will lead to a different conversation than a 60% pass rate. But you don't need those numbers to start the conversation. Michael Bolton writes in [this blog post](https://www.developsense.com/blog/2018/02/how-is-the-testing-going/), the question "How is the testing going?" requires an answer with three strands: a story about the product and its status, a story about the testing, and a story about how good the testing is. A pass/fail ratio is an incredibly narrow entryway to those three stories.

For a further exploration of this topic, I recommend watching Rikard Edgren's talk "[Curing Our Binary Disease](https://vimeo.com/41977011)".

### Test cases encourage management-by-test-case
Test case management tools invite managers to manage by (number of) test cases. (A former colleague of mine told me she was part of a project where the total number of test cases was determined at the start and each tester was expected to execute a certain number of test cases per day. The solution was to create a number of dummy test cases. When you came up with a test idea during testing, you could fill in a dummy test case. When you were not making your number for they day, you could pass a few dummy test cases.) Managing by test case is as bad as idea as managing programmers by lines of code or number of commits. A programmer's job is not writing lines of code, even though that is a means he/she uses to achieve their goal. Same for a tester, their job is not executing test cases, but providing information about the quality of the product.

Which leads to a second question: why would you want to manage testing separately from all the other activities? If your testers are in the same team as the programmers, manage the quality and timeliness of the output of the team. If either are not where you want them to be, better testing might be part of the solution and it might not be. In any case, focusing on testing in the hope of testing quality in, is at best going to improve things by accident.

If your testers are in a separate team, you do have to manage testing separately - at least to some degree. Then we're back to the question: what's the mission of your test team? And my bet is that test cases are not going to help you to tell if they are achieving their mission or not, because of the reasons mentioned in the paragraphs above.


## But what about audits?
The final argument in favor of test case management seems to be audits. The thing is that in my experience the people who claim the most strict requirements for audit, are also the ones who have never spoken to their auditors about what exactly it is they require. Auditors require traceability, but not that you use test cases to achieve that traceability. (In one of my previous jobs we achieved traceability by linking a release to user stories and each user story to one test case each. The test case on its own would contain no information, but attached to it was an Excel sheet documenting the testing we had done. Traceability solved and we could continue doing our jobs the way we wanted to.)


## An alternative
So if not test case management tools, what then? Which is two questions: what to document and in which tool to do it?

For what to document I propose a combination of two things: models of the product and heuristics for test ideas.

Models can take many shapes, forms and sizes: architecture diagrams (aka boxes-and-arrows), sequence diagrams, an [SFDIPOT model](https://www.satisfice.com/download/heuristic-test-strategy-model), an ACC (Attribute - Component - Capability) table, ... Or as something smaller and more concrete, a list of the different types of users: anonymous, logged in, company admin, platform admin.

Some good heuristics for test ideas can be found in Elisabeth Hendrickson's [Test Heuristics Cheat Sheet](https://web.archive.org/web/20150217124452/http://testobsessed.com/wp-content/uploads/2011/04/testheuristicscheatsheetv1.pdf) and Rikard Edgren's [The Little Black Book On Test Design](http://www.thetesteye.com/papers/TheLittleBlackBookOnTestDesign.pdf). Ideally you also have some heuristics specifically for your product based on your team's experiences.

The advantage of this approach is that it encourages you to think every time about what and how you are testing. In addition to that, the models can also be used during refinement and programming.

A third advantage to documenting models and heuristics is that it gives you a wider choice in which tool to use. Since you are not managing test cases, you don't have to limit yourself to test case management tools. You can use any information management tool and that's significantly less of a niche market than the test case management tool. And that might sneakily be one of the bigger advantages of not managing test cases. At the start of this post I mentioned how difficult it would be to build a good test case management tool. By stopping to manage test cases, you'll have a way better chance to find a tool that will enable your testing instead of hindering it.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2020/07/19/its-time-to-retire-our-test-case-management-tools/).*
