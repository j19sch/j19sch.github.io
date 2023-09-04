<!--
.. title: Test cases, can't do 'm no more
.. slug: test-cases-cant-do-m-no-more
.. date: 2013-07-06 20:19:32 UTC+02:00
.. tags: test management, exploratory testing, test cases
.. category: software testing
.. link: 
.. description:
.. type: text
-->

Continuing the style of my previous blog post...

Some days ago I found myself no longer able to think in test cases while testing. Of course, it's not as if I was using test design techniques to generate test cases one day and woke up the next day to find myself unable to do it anymore. But still, about a week ago I figured I had explored enough to be able to write down the test cases I wanted to execute and found myself staring at a blank page (well ok, empty Excel sheet) feeling alienated from what I was planning to do.

So what do I mean when saying "thinking in test cases". Simply put, you take a piece of functionality, let a test design technique loose on it and there you go: a set of test cases to execute. Combine test design techniques over the different pieces of functionality as required and you're all covered test strategy-wise. Or that's the idea.

<!-- TEASER_END -->

The problem with this approach is that it is based on reductive and deductive reasoning. It believes that we can transform a description of some piece of software to a set of actions and checks - with nothing important getting lost in that transformation. How is that ever supposed to work? Systems thinking anyone?

Yet if not test cases, than what? You model, you explore and you investigate. You don't think in test cases; you generate test ideas and work with those. You approach the application as the complex system that it is, with all the different interactions that entails. And yes, during this process you will be using test design techniques. The difference is that they will not give you any guarantee of coverage except in a very trivial way, i.e. that you got the desired coverage for the very specific thing you were testing. That is all.

To answer the question if you tested all the important parts of the application, you do not need test design techniques, you need models. More than one, some may overlap and some may be somewhat contradictory. That's ok. If testing weren't such a messy business, it wouldn't be that much fun.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2013/07/06/test-cases-cant-do-m-no-more/).*
