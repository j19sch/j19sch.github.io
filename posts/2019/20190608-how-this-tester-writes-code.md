<!--
.. title: How this tester writes code
.. slug: how-this-tester-writes-code
.. date: 2019-06-08 18:21:38 UTC+02:00
.. tags: python, programming
.. category: programming
.. link: 
.. description:
.. type: text
-->

A long time ago (March 2015) I wrote a post titled "[Test automation - five questions leading to five heuristics](https://testingcurve.wordpress.com/2015/03/24/test-automation-five-questions-leading-to-five-heuristics/)". Later that year [Rich Rogers](https://twitter.com/richrtesting) asked for a follow-up. To which I replied I should do a follow-up post (ahum) "soon".
Then last Wednesday [Noah Sussman](https://twitter.com/noahsussman) said on [twitter](https://twitter.com/noahsussman/status/1136288062651142149): *'I don't know that I've \*ever\* seen "this is how testers write code"'*. To which I replied "challenge accepted", so now here we are, me writing a blog post about how I as a tester write code.

The format of this post turned out to be advice based on my experiences, so the usual disclaimers apply. And feel free to leave a comment if you have any feedback!


## The basics

### use an IDE
An IDE is not just an advanced text editor. It understands your code - to a degree, since it's not interpreting, compiling or executing the code. So not only allows an IDE you to manipulate your code as text, it also allows you to manipulate your code as code.

<!-- TEASER_END -->

The first place people seem to run into this, is when renaming functions or variables. With a basic text editor you do all the renaming yourself. With a more advanced text editor you have several ways to do a find-and-replace. With an IDE, however, you can do a refactor-rename, which means the IDE will figure out all the places it needs to that rename for you.

Realizing this is the power of a good IDE, is an important step. It allows you to interact with code-as-code, with code-as-text as a fall-back option.

### using libraries well takes skill
Using libraries involves several skills. There's the skill of picking a library based on the documentation, the number of recent commits/releases, number of stars, quality of the code, quality of the tests, trying it out. There's the skill of using the library by reading the documentation, looking at examples, reading (parts of) the library code, experimenting with it.

Finding the right library that can do most of the heavy lifting for you and being able to use it to its full potential, will make your life a lot easier. So acquire these skills.

### use version control
As the saying goes: "Version control is a great way to do version control." It's definitely better than manually adding version numbers to your source code files (been there, done that).

As for version control tools, Git is a great one. It's very popular and probably also complete overkill for what you need. Don't let that discourage you. My own approach to using git consists of:

1. basic commands: add, commit, push, pull, checkout, checkout -b, merge, rebase, push -f, stash, stash apply.
2. git aliases for some commands I never remember, e.g. "git oops" for "git reset HEAD^" and "git tree" for some ridiculously long command that shows a tree-like view of commits.
2. reading whatever git, GitLab and GitHub tell me.
3. Googling stuff, which often brings me to [this page](https://sethrobertson.github.io/GitFixUm/fixup.html).
4. whatever I remember of a video (can't find it, sorry) about how git works (local vs remote, hashes and trees).

One more thing: if you use version control, small commits are the way to go. And don't feel bad if you have to learn that the hard way. I suspect most of us do it that way.


## Next steps

### mess around with different languages
Over the years I have written code in Bash, Perl, PHP (if adding a string to an array counts), VBA for Excel, Java, JavaScript, TypeScript, and Python. In some more than others and I must admit that in any of those languages except for Python I'd have trouble writing three lines of correct code without looking something up.
And that's ok. There's value in having a little experience in a bunch of different languages, because it gives you an idea in which ways those languages are different, and in which ways they are similar.

### dive deeper into one language
[James Powell](https://twitter.com/dontusethiscode) his talk [So you want to be a Python expert?](https://www.youtube.com/watch?v=cKPlPJyQrt4) was important to my learning in three different ways. First of all, watching it and realizing I understood most of it, made me appreciate how much I had learned already. Secondly, I learned a lot about some more advanced features of Python and more importantly the ideas behind them. Thirdly, I realized that learning that stuff is important to progress beyond basic programming.


## Writing good code

### readability
I was making two big mistakes in this area until a developer showed me the error of my ways. The first mistake is that I used short names for everything, because I didn't realize that IDEs with their auto-completion and refactor-rename make using longer names trivial. The second mistake is that I only used functions and methods to avoid copy-pasting code, never to provide structure to the code.
Avoid those two mistakes by giving everything a proper descriptive name and by using functions and methods for structure, and you have two of the three basics of clean code covered. The third one is: refactoring. Getting naming and structure right in your first version is incredibly hard. So iterate a few times until it's good enough.

As soon as you have a basic grasp of the above, learn more about clean code and design patterns. Some smart people who have written a lot of code, have thought a lot about how to write good code. Learn from their insights.

### separation of concerns
Separation of concerns is one of the most important design principles. If we should use functions and methods to structure code, then what should be the scope of one function or method? Ideally a function or method does one thing and one thing only. That also makes naming easier: you name it for the one thing it does.

If you write code this way, you will have separation of concerns on the lowest level. Next you might notice that some pieces of code are more similar than others. There's the code that forms the actual tests, the code that interfaces with the software we are testing, the code that does data setup and teardown, etc. That too is separation of concerns, but one level higher: group functions and methods that do similar things together.

If this still seems a little abstract, the most widely known example of separation of concerns for test automation is the Page Object Pattern. You separate the code that knows how to interact with the DOM (the page objects) from the code that contains the test steps and asserts.

### logging and debugging
In the beginning it's fine to use print statements to get an idea of what your code is doing. At some point however, you'll want to switch to logging. It gives you more flexibility through different log nodes, different log levels, and different log handlers.

If you find yourself adding more and more print statements and/or logging to figure out why your code is not working, switch to a debugger. Especially with a good IDE the learning curve is not that steep and nothing beats being able to inspect your code while it's doing what it's doing.

### exploring and one-offs
Your code should allow you to easily add some new tests based on the existing ones, for the times you want to explore some behavior that's not quite covered by the existing tests. Afterwards you can decide to clean up and commit, or to discard these tests.
It should also be easy to create one-off scripts based on your tests and framework. For example, a script to do the data setup for an exploratory test session or a script to generate load as part of a crude performance test.

If your code only allows you to run your tests as they are, you're missing out.


## Building good tests

### <a name="test-should-do-one-thing"></a>a test should do one thing and one thing only
This is separation of concerns applied to tests: a test should do one thing, not multiple. Of course, depending on the type of test, the size of that one thing will vary. A test on the unit level will be smaller than a test going through the whole stack.

Tests doing one thing only also makes naming easier. Name the test for the thing it is testing. And by this I mean: capture the intention of the test, not the implementation. The implementation I can get by reading the code, the intention I might be able to deduce from the code, but there's a good chance I can't.

Separation of concerns for tests also means having all setup and teardown in separate functions or methods. This makes it a lot clearer what the test is trying to cover. So when you start reading a test, you are reading the actual test immediately, not some preparation steps.
Sidenote: ideally your setup and teardown do not have asserts, but will throw exceptions when unexpected things start to happen.

### interfaces should be sufficiently transparent
So we have separated our interface code from our test code and most likely we are using some library (e.g. Selenium WebDriver) to do the actual interfacing. Life is easy and code is readable. However… how exactly are we interfacing with the software we're testing? Do we know what our test is actually doing to the thing we're testing?
That's why I want interfaces to strike a balance between ease-of-use and transparency. I do want to say "do a GET on this url" without having to worry about the actual HTTP implementation, but I also want to know what my HTTP library puts in the headers of the requests.

### <a name="write-tests-for-tests"></a>do you have to write tests for your tests?
*(After I accepted Noah's challenge, I asked if there was any topics in particular he wanted me to cover. This is [one of them](https://twitter.com/noahsussman/status/1136390636632981504). Follow [this link](https://twitter.com/pgonzalezr/status/1136391331217993728) to read [Pedro Gonzalez](https://twitter.com/pgonzalezr)‘s response and Noah's reaction.)*

If you feel the need to write tests for your tests, that suggests your tests are too complicated. So no, don't write tests for your tests. I am in favor, however, of testing your tests. This testing can take many forms: a review by you or (even better) someone else, making the test fail through a change in the test or the software under test, mutation testing. You can also consider your tests as implicit tests for your other tests. Do note that how much coverage you get from this implicit testing can vary a lot depending on the kind of tests.

One thing you should consider writing tests for, is your test framework and utilities. If they're fairly trivial, it might not be needed. As soon as some complexity creeps in, add some simple tests - rather add them a little too soon than a little too late. It will make refactoring your framework and utilities easier.

### can you apply TDD to building tests?
Thinking about writing tests for your tests, I began to wonder: what would doing TDD for tests look like? (Disclaimer: I'm familiar with the ideas behind TDD, but have never practiced it.)
You'd start by writing a meta-test, a test to test your test. You'd run it and it fails, because you haven't written the test yet. So you write the test. You run the meta-test. It passes. (Or not, so you work on the test until the meta-test passes.)
Now what would a meta-test look like? It's good test design to have the meta-test not be aware of the implementation details of the test. So the meta-test should only care about what the test returns, which is pass/fail/exception. But isn't that what our test runner already does for us? Then why write a separate meta-test?

And that train of thought gave me an idea. Perhaps it could be a good practice to start building a test by giving it a name and writing the asserts you want for that test. If you'd run that test, it would fail horribly, because there's nothing to assert yet. Then you add code to the test until the asserts can evaluate what they need to evaluate.
As I said, right now this is only an idea. If you decide to try it out, please let me know how it went.

### <a name="ok-to-have-conditional-logic"></a>is it ok to have conditional logic in your tests?
*(After I accepted Noah's challenge, I asked if there was any topic in particular he wanted me to cover. This is [the other one](https://twitter.com/noahsussman/status/1136391367935123457). He answers this question himself [here](https://twitter.com/noahsussman/status/1136428406982225926).)*

Needing conditional logic in your tests suggests to me that you're lacking control somewhere. That your tests are not as deterministic as they should be, so you add conditional logic to remedy that. This really should be a last resort where no other solution is feasible, and the value of the test outweighs it being only half-deterministic.

Conditional logic in setup or teardown is a different matter, by the way. For instance for tests where data creation is expensive, doing a get-or-create can be a good solution.

### knowing what's going on when your test runs
Testing is investigating to evaluate a product. So you want as much information as possible - assuming it's structured well enough you can navigate it easily. So good test reports and logging are crucial. When a test fails, you want to have more information than the name of the test, the failed assert, and its assert message.


## Tests-as-code versus tests-as-tests

### two different perspectives
As hinted at by having a section on "writing good code" and one on "building good tests", I approach auto-tests from two different perspectives: tests-as-tests and tests-as code.

Usually these two perspectives align nicely, for example when talking about separation of concerns. Sometimes, however, they do not.
The don't-repeat-yourself (DRY) principle is a good example. Even when you apply separation of concerns, auto-tests tend to get a bit repetitive when you want to test different variants of the same scenario. (Test parameterization can help here too.)
Let's say you have a bunch of tests expecting the same (or a very similar) error message. Following the DRY principle, it would make sense to put that message in one variable shared across tests. From a tests-as-code perspective this makes perfect sense. From a tests-as-tests perspective, however, it does not, because it makes the test more difficult to read.
In cases like this I prefer to have easier to read tests over easier to maintain code.

Another thing is that when you're focused on one of the two perspectives, it sucks to be forced to switch to the other perspective. When you're in tests-as-tests mode, you're thinking about the software you're testing, about the problems it's trying to solve, the capabilities it tries to deliver. In tests-as-code mode, you're thinking about the code you're writing, how to make it do what you need it to and how to keep it maintainable. Switching between the two in a natural rhythm is fine; being forced to switch not so much.

### a programming language is a DSL
There are quite some testing tools and libraries that introduce a domain-specific language (DSL) to make writing tests easier. Their claim is that it's easier to learn their domain-specific language than it is to learn a general-purpose programming language.

In my opinion that's not an entirely fair comparison. I don't need to learn all of Java or Python or … to be able to build tests in those languages. I only need to learn the part of the language that's relevant to the building I want to do. Hence, a programming language is a domain-specific language.

Now I must admit that most DSLs are easier to learn than the required sub-set of a programming language. Even so, I prefer general-purpose programming languages for two reasons.
First of all, a DSL is limited to its domain. If you want to do something it wasn't designed for or something outside of that domain, you'll either need to switch to a different DSL or to a general-purpose language. Since that's bound to happen at some point, I'd rather learn a sub-set of a general-purpose language from the start and expand my knowledge of that language when needed.
Secondly, I think there's value for anyone who's part of software development, to have a basic understanding of programming. The best way to do that is to do things in code on a a regular basis - preferably as part of your job. Building tests is a great way for non-programmers to have that experience.


## Revisiting my blogpost from 2015
As mentioned in the introduction, in 2015 I wrote a blogpost with the title "[Test automation - five questions leading to five heuristics](https://testingcurve.wordpress.com/2015/03/24/test-automation-five-questions-leading-to-five-heuristics/)". So let's see revisit those heuristics more than four years later.

**Heuristic 0: Don't call it test automation.**  
I don't think I ever stopped calling it test automation. When I wrote the post, I was stricter in using the best possible words. Currently, my position is that if communication is happening, the words we are using are good enough. I do prefer the term "auto-tests" over "automated tests", since the latter still suggests to me that perhaps we might be able to "automate all the testing".
(And yes, I snuck six heuristics in my original post by starting with 0.)

**Heuristic 1: Never trust a test you haven't seen fail.**  
Yep, see "[Do you have to write tests for your tests?](#write-tests-for-tests)".

**Heuristic 2: Each test should test only one thing.**  
Yep, see "[A test should do one thing and one thing only](#test-should-do-one-thing)".

**Heuristic 3: It's better to have reliable information that doesn't exactly tell you what you want to know, than unreliable information that does.**  
Not covered in this post, although it is related to having deterministic tests ("[Is it ok to have conditional logic in your tests?](#ok-to-have-conditional-logic)"). And I still agree: I'd rather have a reliable test that doesn't entirely test what I want to test, than an unreliable test that does (or more precise: tries to).

**Heuristic 4: Every minute spent debugging test automation code is wasted, because you learn nothing.**  
I was quite amused reading this, since it seems I was finding no joy at all in writing and debugging code. I don't think that was actually the case, but it is true that I enjoy programming more now than I did back then in 2015. The reason is quite simple: I've gotten better at it.
Setting aside the tone of that paragraph, I do see a link with what I have written above about tests-as-tests and tests-as-code, and about how being forced to switch between them sucks.

**Heuristic 5: Epistemic testability, epistemic testability, epistemic testability.**  
Revisiting the [definition of epistemic testability](https://www.satisfice.com/download/heuristics-of-software-testability), I don't think I was using the term the way James Bach intended. Be that as it may, I still stand by the point I was making: is your test automation helping you to do better testing? And by extension, helping you to develop and deliver software better?

---

*This post was originally published [here](https://testingcurve.wordpress.com/2019/06/08/how-this-tester-writes-code/).*
