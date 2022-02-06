<!--
.. title: VIPT - how to teach software testing
.. slug: vipt-how-to-teach-software-testing
.. date: 2012-07-29 16:24:51 UTC+02:00
.. tags: VIPT, context-driven testing, models, teaching
.. category: philosophy of testing
.. link: 
.. description:
.. type: text
-->

In this final post on VIPT (Value-Information-Processes-Tools) it's time to take a look at teaching software testing. My previous posts on VIPT can be found [here](link://slug/yet-another-testing-model-value-information-processes-value), [here](link://slug/vipt-intermezzo-models-and-the-unix-philosophy) and [here](link://slug/vipt-bottom-up-or-top-down).


## A typical software testing course

A typical traditional software testing course (at least in the way I have taught them) has three elements: theory, stories and exercises.

The first element is all about definitions (testing, test cases, defects, etc.), process descriptions and testing techniques (mostly test design). So basically what happens is that students get a brief introduction about testing in general and then we move on to the main part: teaching a specifc testing method.

The second element of the course are the stories. These are mostly stories aobut how testing in the real world does not work as described in the theory. At best they are stories containing all four elements of VIPT. Most of the time, however, they are just real-world examples of a certain definition or technique.

Finally, there are exercises. As with the techniques, these are mostly about test design. Unfortunately they are also very linear. There is only one correct answer and often only one correct way to get to that answer. So the main gist seems to be: "I taught you a trick, now show me you can perform the trick." But shouldn't learning about testing be more than learning to jump through a hoop on command?

<!-- TEASER_END -->

### Applying VIPT to a typical software testing course

How does this relate to the VIPT-model? Does this way of teaching cover all four elements of the model? Or does it focus on some elements at the cost of others?

I don't think it's hard to see that this way of teaching testing is heavily tool-focussed. It's main purpose is to transfer knowledge about a specific testing method. In the VIPT-model this kind of knowledge is a tool. (During the course this knowledge is of course information, but in testing knowledge about a testing methodology is a tool. No one really cares how much you know about testing, they do care about what you can tell them about the quality of the product.)

At least during the exercises the student also experiences a process, but as I said earlier: the value of these exercises lays in demonstrating you can apply a certain test design technique, when asked to do so. That's actually quite bizarre. It suggests that the hard part about testing is creating test scripts. Executing them correctly and making the problem-or-no-problem decision based on the result, is apparently such a banal task any idiot can do it, no training required.

To some degree this focus on tools makes sense: teaching a skill set has very much to do with giving people a good set of tools. However, that's not all there is to it. If I give you a set of carpenter tools and teach you how to use them, you'll still have a hard time to build decent cabinet. Because you still have to figure out how to combine your new skills into a series of actions that will result in a decent cabinet. You don't just need to know how to use your tools, you also need when to apply which one with what purpose. You need to know in what circumstances a tool can create a certain value and in what circumstances it can't.

### Test framing

In testing, an important part of this is - as Michael Bolton and James Bach call it - [test framing](http://www.developsense.com/resources/TestFraming.pdf):

> "the capacity to follow and express, at any time, a direct line of logic that connects the mission to the tests."

Or put differently, being able to answer the question of how the tool you are using, produces what value.

### Explaining the value of testing

Another aspect is being able to express what value testing in a general sense can provide - without simply reciting the definition of testing you memorized. And preferable this explanation touches on the typical problems testers face in their line of work. For instance, recently I was asked: "To you, how much quality is enough?" I looked puzzled by the question and got the following clarification: "Would you say that only 100% can be enough? Or is 80% ok too?" So I answered it's not up to me decide how much quality is enough. That's up to the stakeholders or their representative, the project manager. And if the decision is made that 60% quality is good enough[^1], I might inform them there is some pretty important stuff in the missing 40%, but still it's not my decision. The only decision I get to make is to quit the job or to stay, I guess. However, the thing that amazes me the most about this question is that most of the time this person apparently does get an actual percentage as a reply.[^2]

It's just one of many examples that show we are failing at teaching testers to think about testing. Plenty of testers seem quite good in applying the framework they were taught in thoughtful and critical manner, but they never seem to go beyond that and apply their intelligence to questioning that framework. And more importantly, wonder whether there is a different framework in which they could provide more value.


## So how do we fix this?

For starters, as James Bach keeps saying, let's have the students test an actual piece of software! Then coach them along the way: tell them what they did right and show them where they went wrong. At least then the students will have exerpienced how the process of applying a set of testing tools can result in information about the quality of a product. Let them move through VIPT in relation to software testing.

But why stop there? Don't just tell students testing is a sampling problem, let them experience it. Have them make decisions about how to test and then let them run into an unkown unknown. Have their tools fail on them: hand them a set of tools that poorly fits the situation and see if they figure that out and create their own tools.

So instead of giving new testers a bag full of tools and a vague notion of what to do with it, have them go through all four layers of VIPT. The reason is very simple: even as beginning testers, they need to own their craft - if only at a very basic level.

<br />

*p.s.* One other thing I would like to see added to testing education is the history of software testing. People have little appreciation of how things were before they learned about it. For some testers, Agile has always existed in the same way as for some people there always have been mobile phones and the internet.
For an excellent start on the history of testing, see [http://www.testingreferences.com/testinghistory.php](http://www.testingreferences.com/testinghistory.php) by Joris Meerts and Dorothy Graham.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2012/07/29/vipt-how-to-teach-software-testing/).*

[^1]: But how do you express quality in a single percentage anyhow? Perhaps ‘fairly good' would make more sens as it doesn't imply a calculation of some sort to get to the reply.

[^2]: On the other hand, I could argue that the correct answer is 80%. Anything lower and you are too easy-going, anything higher and you're too much of a perfectionist. Of course, if that's the intention of the question, one might as well ask: "What's your stance on quality? Anything goes, good enough is good enough, or only perfection counts?"
