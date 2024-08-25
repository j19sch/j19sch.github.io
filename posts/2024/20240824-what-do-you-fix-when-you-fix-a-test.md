<!--
.. title: What do you fix when you fix a test?
.. slug: what-do-you-fix-when-you-fix-a-test
.. date: 2024-08024
.. category:
.. tags:
.. type: text
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

That test is now a legacy test.


# Legacy tests {.small}

Legacy tests are a sub-set of legacy code: code that you can't throw away, but wish would be different. Or as [Ángel Siendones Sillero](https://www.linkedin.com/in/angel-siendones-sillero) has put it:

> Legacy code is often defined as "code that makes more design decisions than the team working on it".[^2]

[^2]: Which to be fair, was only the lead up to [their actual point](https://www.linkedin.com/posts/angel-siendones-sillero_legacy-code-is-often-defined-as-code-that-activity-7145457617526538240-nvRS/): Could we define a legacy process as "one that makes more decisions on how a team functions than the team itself"? 🤔

Translated to legacy tests, this means that the existing tests are making more decisions about what and how things are tested, than the team working on them.

# Avoiding the trap of legacy tests {.small}

So how do you avoid this trap of legacy tests? I'm not going to claim I have the full answer, but I do have three suggestions.

First of all, it's helpful to [distinguish tests-as-code and tests-as-tests](link://slug/how-this-tester-writes-code#tests-as-code-vs-tests-as-tests). When you're thinking about tests as tests-as-tests, you're thinking about the information the tests can give you about the code or application under test. When you're thinking about tests as tests-as-code, you're thinking about how you can get the test code to do what you want it to do. Especially when tests fail at an incoventient time, it's tempting to only treat them as code. How can you change the code of the test so that it passes? That's when it's time to take a step back and look at the test from the other perspective: what information is this test supposed to provide and how do I make sure it keeps doing so?

Asking (and answering) that question is a lot easier when your tests clearly express their intention. What exactly is each test trying to test. You do this by giving tests clear names, separating setup and teardown code from the actual test, and by being deliberare in how you group tests together. It might also mean being a little less smart in your code, making it as easy as possible to read - even if it's at the expense of a little maintainability.

Last but not least, you need to have an ongoing conversation with your team about your [testing strategy](link://slug/test-strategy-primer). What do you want to test, why, where, and how? Even though you want to make your test code as expressive as possible, it can never express itself fully. As Peter Naur wrote in his article "Programming as Theory Building" (1985)[^3]:

*"In terms of Ryle’s notion of theory, what has to be built by the programmer is a theory of how certain affairs of the world will be handled by, or supported by, a computer program. On the Theory Building View of programming the theory built by the programmers has primacy over such other products as program texts, user documentation, and additional documentation such as specifications."*

[^3]: I only discovered this article because Alistair Cockburn included it in [Appendix B](https://gwern.net/doc/cs/algorithm/1985-naur.pdf) of his excellent book "Agile Software Development".

The only way to have a true shared understanding about the tests, is to have conversations about the tests. So that when there's a mistake in what the test should test, you don't only fix the test code, you fox the test design as well.

---

Have you encountered legacy tests? What are some of the signs you look out for? And what are your favorite ways to deal with legacy tests?
