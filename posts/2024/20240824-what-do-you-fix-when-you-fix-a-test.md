<!--
.. title: What do you fix when you fix a test?
.. slug: what-do-you-fix-when-you-fix-a-test
.. date: 2024-08024
.. category:
.. tags:
.. type: text
-->


<!-- 

not tech debt, just chores not done -> link!
https://twtext.com/article/1376628481878990852
Yvonne Lam

> My theory of tech debt is that housework is the correct metaphor for the thing we call tech debt, but we can't use it because tech has been made up of people who don't do housework, or manage housework being done. 
 -->



 You ran the tests[^1] - or a pipeline did it for you - and some of them failed. Time to fix the tests! But what is it exactly that needs fixing?

[^1]: I'm using the word test here in the way developers tend to use it: a test is a piece of code. In a different context I might use it in the way any good tester can relate to and say: a test is a performance. It would be [nice to have more bridges](link://slug/a-good-tester-is-all-over-the-place#building-bridges) between these communities.


 # The things that can make a test go red {.small}

There are quite a few things that might make a test fail:

- an issue with the build (inc. compiler/interpreter bugs)
- an issue with the pipeline (if applicable)
- an issue in the environment the code under test us running on
- an issue in the environment the test code is running on
- a bug in the code under test
- a mistake in the test code
- a mistake in what the test should test

Arguably, on the last three describe a test that fails. The test did its job detecting a problem. In the first four we didn't even get that far. The issues prevented the test from doing its job. So in those cases, it's not the test(s) as such that need fixing.

Which leaves with the last three in the list. If a test finds a bug in the code under test, great! Fix the bug. If there's a programming mistake in the test, great! Fix the mistake.

But what if the test isn't testing what it should be testing? What if there's a problem with the test design? Simple, fix the test!


# The challenge of fixing the test design {.small}

Ideally, that is indeed what happens. You read the failing test. You understand why it exists and what it is supposed to test. So you update the test based on that understanding, and make it pass again. And perhaps you even look at the surrounding tests and make some changes in those as well. You might even add a few more tests.

Unfortunately, often enough that's not what happens. Especially when tests fail at an inconvenient time.

You think you're done. You've written the code. You've written the tests. Those pass. You've done some exploratory testing. And then either on your local machine or in the pipeline, you run all the tests. And some of them fail. You thought you were done, but turns out you're not.

At that time it's very tempting to look at the failing tests and fix the assertion that's failing. Because it is tempting when you look at the actual result reported by the test runner, think "yeah that looks right" and update the test to assert on the actual result. And often enough, that's fine. That is the correct way to handle it.

But sometimes it's not. The test loses something: some coverage, some clarity of intention. The test has lost some of its value. And after that has happened a few times, it's really not that good a test anymore. It still provides enough value that you don't want to delete it, but it's not very clear anymore either what the test is supposed to be testing. And how in combination with its surrounding tests, provides sufficient coverage of the thing being tested.

Those tests are not legacy tests.


# Avoiding the trap of legacy tests

In my experience, an important factor is if you're engaging with the tests-as-code or as the tests-as-tests.


> If you're engaging with the tests-as-code, it's very tempting to look at the actual result reported by the test runner, think "yeah that looks right" and update the test to assert on the actual result. And often enough that's fine. But sometimes it's not. And over time it can lead to a test losing a lot of its value. It provides enough value not to delete it, but it's no longer a focused test. It's not very clear anymore what one thing it's testing. Or how in combination with the surrounding tests, provides sufficient coverage of the thing being tested.

> They are legacy tests. Tests do not escape the problem of legacy code.

---

importance of tests expressing their design, their reason for existing as much as possible

optimize for readability / understandability, enough in my head without having to also model test code
2019-06-08 how-this-tester-writes-code/ -> Tests-as-code versus tests-as-tests

challenge when test interface != human interface, e.g. rendered page vs DOM

 Programming as theory building
 reading in papers book club
 https://gwern.net/doc/cs/algorithm/1985-naur.pdf
 https://pablo.rauzy.name/dev/naur1985programming.pdf
