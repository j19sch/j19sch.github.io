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
 -->



 You ran the tests[^1] - or a pipeline did it for you - and some of them failed. Time to fix the tests! But what is it that needs fixing?

[^1]: I'm using the word test here in the way developers tend to use it: a test is a piece of code. In a different context I might use it in the way any good tester can relate to and say: a test is a performance. It would be [nice to have more bridges](link://slug/a-good-tester-is-all-over-the-place#building-bridges) between these communities.

 # The things that can make a test go red {.small}

 go red != fail

There are quite a few things that might make a test fail:

- an issue with the build (inc. compiler/interpreter bugs)
- an issue with the pipeline (if applicable)
- an issue in the environment the code under test us running on
- an issue in the environment the test code is running on
- a bug in the code under test
- a mistake in the test code
- a mistake in the test design, in what the test should test

Arguably, on the last three describe a test that fails. The test did its job detecting a problem. In the first four we didn't even get that far. The issues prevented the test from doing its job.





# The challenge of fixing the test {.small}

optimize for readability / understandability, enough in my head without having to also model test code
how-this-tester-writes-code/ -> Tests-as-code versus tests-as-tests

challenge when test interface != human interface, e.g. rendered page vs DOM

 Programming as theory building
 reading in papers book club