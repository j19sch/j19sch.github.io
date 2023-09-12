<!--
.. title: Test automation - five questions leading to five heuristics
.. slug: test-automation-five-questions-leading-to-five-heuristics
.. date: 2015-03-24 20:53:24 UTC+01:00
.. tags: test automation, testing and checking, programming, heuristics
.. category: programming & test automation
.. link: 
.. description:
.. type: text
-->

*I wrote a [follow-up](link://slug/how-this-tester-writes-code) to this post in June 2019 in which I [revisit the heuristics](link://slug/how-this-tester-writes-code#revisiting-my-blogpost-from-2105) from this post.*


In 1984 Abelson and Sussman said in the Preface to '[Structure and Interpretation of Computer Programs](https://mitpress.mit.edu/sicp/)':

> Our design of this introductory computer-science subject reflects two major concerns. First, we want to establish the idea that a computer language is not just a way of getting a computer to perform operations but rather that it is a novel formal medium for expressing ideas about methodology. **Thus, programs must be written for people to read, and only incidentally for machines to execute.** Second, we believe that the essential material to be addressed by a subject at this level is not the syntax of particular programming-language constructs, nor clever algorithms for computing particular functions efficiently, nor even the mathematical analysis of algorithms and the foundations of computing, but rather the techniques used to control the intellectual complexity of large software systems. [emphasis mine]

This oft-quoted sentence I emphasized, is even more true if the purpose of our programs is test automation[^1]. So let's say you run your test automation program and the result is a list of passes and fails.  The purpose of testing is to produce information. You could say that this list of results qualifies as information and I would disagree. I would say it is data, data in need of interpretation. When we attempt this interpretation, we should consider the following five questions.

<!-- TEASER_END -->

## Five questions

### Question 1: What exactly is this list of results as such telling you?
Picture the list of test results. All it contains are the names of the test cases and whether they passed or failed. With just that list in front of you, how much do you know? How easy is it to identify potential problems? To identify where you need to start investigating? Are you able to do that based on the list as such? Or will you have to dive into the details of each test case to be able to do this? I certainly hope not...

### Question 2: How do you tell false negatives from true ones?
Going through the list of passes and fails, you'll probably feel good about the passes and bad about the fails.[^2] So you set out to investigate the failed test cases. However, some will be true negatives (the test exposed a bug) and some will be false negatives (the test is wrong). How will you be able to tell the difference?

### Question 3: How do you tell false positives from true ones?
Not only can we have false negatives in our test results, we might also have false positives. Test cases that pass, although they shouldn't have. How will you be able to tell the difference here? And more poignantly, where will you find the motivation to even start looking for the false positives? Why can't we just be happy all those tests passed?

### Question 4: How do you find the thing that's broken? Or even more fun, the things that are broken?
So you have at least one test that doesn't return the result you want to have. That means the result is a either a fail or a false positive. (So yes, of the four possible outcomes, three require further action.) For your investigation there are basically four areas to focus on:

- The product under test. You found a bug. Good job!
- Test design. You designed a test to identify a potential problem, but it turns out that problem isn't actually a problem.
- Test execution. You made a mistake in how you translated your test designs into test automation code.
- Test tooling. Your tool (this includes the test environment) had a 'hiccup' or a 'glitch'.

These four areas are relevant whether you're investigating automated tests or other tests. However, a major problem with automated tests is that this investigation is more difficult because two of the four areas are bigger. First of all there's the test execution area. Your translated test designs will be interpreted by a computer, which has a lot less interpretative flexibility than a human being. So your translation needs to be of a higher quality than if you were translating for another human being. Secondly, the test tooling area is bigger, simply because you have more tooling.

### Question 5 (bonus meta-question): What understanding are you losing by automating?
Toyota is not unfamiliar with automation. And last year, they decided to replace a number of robots in their factories with human workers. Why? As project lead Mitsuru Kawai says:

> We cannot simply depend on the machines that only repeat the same task over and over again. To be the master of the machine, you have to have the knowledge and the skills to teach the machine. (source: [Bloomberg](http://www.bloomberg.com/news/articles/2014-04-06/humans-replacing-robots-herald-toyota-s-vision-of-future))

Toyota realized that by fully automating the car manufacturing process, they were losing important knowledge and skills about how to build cars. So no, they're not replacing all robots with humans, but they are putting humans back into the manufacturing process so that learning and improvement can happen. The same applies to test automation. If it is keeping you from interacting with the product, from actually testing yourself, it's time to rethink your approach.

## Epistemic testability
In the end it all boils down to one question: is your test automation increasing our decreasing your [epistemic testability](http://www.satisfice.com/tools/testable.pdf)? Does it make it easier or harder to bridge the gap between what we know and what we need to know about the status of the product? Test automation is excellent in providing you with the illusion of increased epsitemic testability: "Every night we run 10,000 tests in less than an hour!" While actually decreasing it: "Alice and Bob spend four hours every day processing the results!"

Having thought about those questions, I have gathered the following set of heuristics on test automation. Time and experience will tell if they're any good...

## Five heuristics
Having thought about those questions, I have gathered the following set of heuristics on test automation. Time and experience will tell if they're any good…

### Heuristic 0: Don't call it test automation.
As James Bach pointed out at Tasting Let's Test Benelux, developers used to talk about "[automatic programming](http://en.wikipedia.org/wiki/Automatic_programming)". The meaning of the term has changed over time, but at no point in time did developers think that when you do automatic programming (e.g. use a compiler), all of programming has been automated. So either we change the meaning of 'test automation' in a similar way (which fails to account for the testing-checking distinction), or we come up with a better term. I'm still looking for a better term, all suggestions are welcome.

### Heuristic 1: Never trust a test you haven't seen fail.  
*(source: Colin Vipur via [Rob Fletcher](https://github.com/robfletcher/idiomatic-spock/blob/master/README.md))*  
It will help you avoid false positives. But we should actually takes this several steps further, as you can read in this blog post by Richard Bradshaw: [Who tests the checks?](http://www.thefriendlytester.co.uk/2014/03/who-tests-checks.html) Do go read the whole post, but one excellent thing he proposes is to test if a failing test gives sufficient information about why it fails.

### Heuristic 2: Each test should test only one thing.
*(s/test/check, of course)*  
This will reduce the complexity of your investigation when your test needs investigating. If it fails, you can begin looking at the one thing your test is testing. Also, if each test tests only one thing, you will have several quite similar tests. Looking at all of them, seeing which passed and which failed, will give you useful clues in your investigation.

### Heuristic 3: It's better to have reliable information that doesn't exactly tell you what you want to know, than unreliable information that does.
With reliable I mean: Does it run all the tests every time with a minimal risk of false positives or negatives? If to get that reliability, my tests don't run on the level I would like to run them (e.g. the GUI-level), I'm more than happy to make that trade-off. The additional interpretative step I need to make, is less of a risk than the extra effort it takes to deal with a flaky, unreliable test set that doesn't require that step.

### Heuristic 4: Every minute spent debugging test automation code is wasted, because you learn nothing.
Going back to the four areas to investigate, the first three (product, test design, test execution) are interesting from a tester's perspective. Investigating these will provide you with opportunities to learn about the product or about testing. Not so with a failure in your test tooling. It's an impediment that needs to be solved quickly. In this respect there is no difference between a failure in your test automation tool and a failure of your keyboard.

### Heuristic 5: Epistemic testability, epistemic testability, epistemic testability.
Repeating this because it is so important. It is the litmus test of your test automation. Consider it when choosing your tools, when deciding on abstraction layers, when designing your tests, when composing your test set, when writing your test automation code, when testing your tests, when documenting your tests, when interpreting the results. Because when you have your first test results, your first list of passes and fails, it's the epistemic testability that will decide for a large part how useful that list will be.

*(This post was deeply influenced by the ideas James Bach, Micheal Bolton, Alan Richardson, Pascal Dufour, Richard Bradshaw and the BBST Bug Advocacy Course. Thank you to all.)*

---

*This post was originally published [here](https://testingcurve.wordpress.com/2015/03/24/test-automation-five-questions-leading-to-five-heuristics/).*

[^1]: Or, instead of test automation, a better term would be 'check execution automation'. Although this is an important distinction, I'm not going to pursue it today. If you do want to, this post is a good starting point: [Testing and Checking Refined](http://www.satisfice.com/blog/archives/856) by James Bach and Michael Bolton.

[^2]: Be wary of the binary disease! Luckily there's a cure: [Curing Our Binary Disease](https://vimeo.com/41977011) by Rikard Edgren at Øredev 2011.
