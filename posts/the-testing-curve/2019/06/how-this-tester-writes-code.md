<html><body><p>A long time ago (March 2015) I wrote a post titled "<a href="https://testingcurve.wordpress.com/2015/03/24/test-automation-five-questions-leading-to-five-heuristics/">Test automation – five questions leading to five heuristics</a>". Later that year <a href="https://twitter.com/richrtesting">Rich Rogers</a> <a href="https://twitter.com/richrtesting/status/667091867549339648">asked for a follow-up</a>. To which I replied I should do a follow-up post (ahum) "soon".<br>Then last Wednesday <a href="https://twitter.com/noahsussman">Noah Sussman</a> said on <a href="https://twitter.com/noahsussman/status/1136288062651142149">twitter</a>: '<em>I don’t know that I’ve *ever* seen “this is how testers write code</em>'. To which I replied "challenge accpeted", so now here we are, me writing a blog post about how I as a tester write code.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The format of this post turned out to be advice based on my experiences, so the usual disclaimers apply. And feel free to leave a comment if you have any feedback!</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>the basics</strong></h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>use an IDE</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>An IDE is not just an advanced text editor. It understands your code - to a degree, since it's not interpreting, compiling or executing the code. So not only allows an IDE you to manipulate your code as text, it also allows you to manipulate your code as code.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The first place people seem to run into this, is when renaming functions or variables. With a basic text editor you do all the renaming yourself. With a more advanced text editor you have several ways to do a find-and-replace. With an IDE, however, you can do a refactor-rename, which means the IDE will figure out all the places it needs to that rename for you.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Realizing this is the power of a good IDE, is an important step. It allows you to interact with code-as-code, with code-as-text as a fall-back option. </p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>using libraries well takes skill</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Using libraries involves several skills. There's the skill of picking a library based on the documentation, the number of recent commits/releases, number of stars, quality of the code, quality of the tests, trying it out. There's the skill of using the library by reading the documentation, looking at examples, reading (parts of) the library code, experimenting with it.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Finding the right library that can do most of the heavy lifting for you and being able to use it to its full potential, will make your life a lot easier. So acquire these skills.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>use version control</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>As the saying goes: "Version control is a great way to do version control." It's definitely better than manually adding version numbers to your source code files (been there, done that).</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>As for version control tools, Git is a great one. It's very popular and probably also complete overkill for what you need. Don't let that discourage you. My own approach to using git consists of:<br>1. basic commands: add, commit, push, pull, checkout, checkout -b, merge, rebase, push -f, stash, stash apply.<br>2. git aliases for some commands I never remember, e.g. "git oops" for "git reset HEAD^" and "git tree" for some ridiculously long command that shows a tree-like view of commits.<br>2. reading whatever git, GitLab and GitHub tell me.<br>3. Googling stuff, which often brings me to <a href="https://sethrobertson.github.io/GitFixUm/fixup.html">this page</a>.<br>4. whatever I remember of a video (can't find it, sorry) about how git works (local vs remote, hashes and trees).</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>One more thing: if you use version control, small commits are the way to go. And don't feel bad if you have to learn that the hard way. I suspect most of us do it that way.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>next steps</strong></h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>mess around with different languages</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Over the years I have written code in Bash, Perl, PHP (if adding a string to an array counts), VBA for Excel, Java, JavaScript, TypeScript, and Python. In some more than others and I must admit that in any of those languages except for Python I'd have trouble writing three lines of correct code without looking something up.<br>And that's ok. There's value in having a little experience in a bunch of different languages, because it gives you an idea in which ways those languages are different, and in which ways they are similar.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>dive deeper into one language</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p><a href="https://twitter.com/dontusethiscode">James Powell</a> his talk <a href="https://www.youtube.com/watch?v=cKPlPJyQrt4">So you want to be a Python expert?</a> was important to my learning in three different ways. First of all, watching it and realizing I understood most of it, made me appreciate how much I had learned already. Secondly, I learned a lot about some more advanced features of Python and more importantly the ideas behind them. Thirdly, I realized that learning that stuff is important to progress beyond basic programming.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>writing good code</strong></h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>readability</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>I was making two big mistakes in this area until a developer showed me the error of my ways. The first mistake is that I used short names for everything, because I didn't realize that IDEs with their auto-completion and refactor-rename make using longer names trivial. The second mistake is that I only used functions and methods to avoid copy-pasting code, never to provide structure to the code.<br>Avoid those two mistakes by giving everything a proper descriptive name and by using functions and methods for structure, and you have two of the three basics of clean code covered. The third one is: refactoring. Getting naming and structure right in your first version is incredibly hard. So iterate a few times until it's good enough.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>As soon as you have a basic grasp of the above, learn more about clean code and design patterns. Some smart people who have written a lot of code, have thought a lot about how to write good code. Learn from their insights.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>separation of concerns</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Separation of concerns is one of the most important design principles. If we should use functions and methods to structure code, then what should be the scope of one function or method? Ideally a function or method does one thing and one thing only. That also makes naming easier: you name it for the one thing it does.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>If you write code this way, you will have separation of concerns on the lowest level. Next you might notice that some pieces of code are more similar than others. There's the code that forms the actual tests, the code that interfaces with the software we are testing, the code that does data setup and teardown, etc. That too is separation of concerns, but one level higher: group functions and methods that do similar things together.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>If this still seems a little abstract, the most widely known example of separation of concerns for test automation is the Page Object Pattern. You separate the code that knows how to interact with the DOM (the page objects) from the code that contains the test steps and asserts.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>logging and debugging</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>In the beginning it's fine to use print statements to get an idea of what your code is doing. At some point however, you'll want to switch to logging. It gives you more flexibility through different log nodes, different log levels, and different log handlers.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>If you find yourself adding more and more print statements and/or logging to figure out why your code is not working, switch to a debugger. Especially with a good IDE the learning curve is not that steep and nothing beats being able to inspect your code while it's doing what it's doing.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>exploring and one-offs</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Your code should allow you to easily add some new tests based on the existing ones, for the times you want to explore some behavior that's not quite covered by the existing tests. Afterwards you can decide to clean up and commit, or to discard these tests.<br>It should also be easy to create one-off scripts based on your tests and framework. For example, a script to do the data setup for an exploratory test session or a script to generate load as part of a crude performance test.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>If your code only allows you to run your tests as they are, you're missing out.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>building good tests</strong></h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3 id="one-thing-only">a test should do one thing and one thing only</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>This is separation of concerns applied to tests: a test should do one thing, not multiple. Of course, depending on the type of test, the size of that one thing will vary. A test on the unit level will be smaller than a test going through the whole stack.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Tests doing one thing only also makes naming easier. Name the test for the thing it is testing. And by this I mean: capture the intention of the test, not the implementation. The implementation I can get by reading the code, the intention I might be able to deduce from the code, but there's a good chance I can't.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Separation of concerns for tests also means having all setup and teardown in separate functions or methods. This makes it a lot clearer what the test is trying to cover. So when you start reading a test, you are reading the actual test immediately, not some preparation steps.<br>Sidenote: ideally your setup and teardown do not have asserts, but will throw exceptions when unexpected things start to happen.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>interfaces should be sufficiently transparent</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>So we have separated our interface code from our test code and most likely we are using some library (e.g. Selenium WebDriver) to do the actual interfacing. Life is easy and code is readable. However... how exactly are we interfacing with the software we're testing? Do we know what our test is actually doing to the thing we're testing?<br>That's why I want interfaces to strike a balance between ease-of-use and transparency. I do want to say "do a GET on this url" without having to worry about the actual HTTP implementation, but I also want to know what my HTTP library puts in the headers of the requests.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3 id="tests-for-your-tests">Do you have to write tests for your tests?</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p><em>(After I accepted Noah's challenge, I asked if there was any topics in particular he wanted me to cover. This is <a href="https://twitter.com/noahsussman/status/1136390636632981504">one of them</a>. Follow the link to read <a href="https://twitter.com/pgonzalezr">Pedro Gonzalez</a>'s response and Noah's reaction.)</em></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>If you feel the need to write tests for your tests, that suggests your tests are too complicated. So no, don't write tests for your tests. I am in favor, however, of testing your tests. This testing can take many forms: a review by you or (even better) someone else, making the test fail through a change in the test or the software under test, mutation testing. You can also consider your tests as implicit tests for your other tests. Do note that how much coverage you get from this implicit testing can vary a lot depending on the kind of tests.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>One thing you should consider writing tests for, is your test framework and utilities. If they're fairly trivial, it might not be needed. As soon as some complexity creeps in, add some simple tests - rather add them a little too soon than a little too late. It will make refactoring your framework and utilities easier.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Can you apply TDD to building tests?</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Thinking about writing tests for your tests, I began to wonder: what would doing TDD for tests look like? (Disclaimer: I'm familiar with the ideas behind TDD, but have never practiced it.)<br>You'd start by writing a meta-test, a test to test your test. You'd run it and it fails, because you haven't written the test yet. So you write the test. You run the meta-test. It passes. (Or not, so you work on the test until the meta-test passes.)<br>Now what would a meta-test look like? It's good test design to have the meta-test not be aware of the implementation details of the test. So the meta-test should only care about what the test returns, which is pass/fail/exception. But isn't that what our test runner already does for us? Then why write a separate meta-test?</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>And that train of thought gave me an idea. Perhaps it could be a good practice to start building a test by giving it a name and writing the asserts you want for that test. If you'd run that test, it would fail horribly, because there's nothing to assert yet. Then you add code to the test until the asserts can evaluate what they need to evaluate.<br>As I said, right now this is only an idea. If you decide to try it out, please let me know how it went.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3 id="conditional-logic">Is it ok to have conditional logic in your tests?</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p><em>(After I accepted Noah's challenge, I asked if there was any topic in particular he wanted me to cover. This is <a href="https://twitter.com/noahsussman/status/1136391367935123457">the other one</a>. He answers this question himself <a href="https://twitter.com/noahsussman/status/1136428406982225926">here</a>.)</em></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Needing conditional logic in your tests suggests to me that you're lacking control somewhere. That your tests are not as deterministic as they should be, so you add conditional logic to remedy that. This really should be a last resort where no other solution is feasible, and the value of the test outweighs it being only half-deterministic.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Conditional logic in setup or teardown is a different matter, by the way. For instance for tests where data creation is expensive, doing a get-or-create can be a good solution.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>knowing what's going on when your test runs</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Testing is investigating to evaluate a product. So you want as much information as possible - assuming it's structured well enough you can navigate it easily. So good test reports and logging are crucial. When a test fails, you want to have more information than the name of the test, the failed assert, and its assert message.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>tests-as-code versus tests-as-tests</strong></h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3 id="two-perspectives">two different perspectives</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>As hinted at by having a section on "writing good code" and one on "building good tests", I approach auto-tests from two different perspectives: tests-as-tests and tests-as code.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Usually these two perspectives align nicely, for example when talking about separation of concerns. Sometimes, however, they do not.<br>The don't-repeat-yourself (DRY) principle is a good example. Even when you apply separation of concerns, auto-tests tend to get a bit repetitive when you want to test different variants of the same scenario. (Test parameterization can help here too.)<br>Let's say you have a bunch of tests expecting the same (or a very similar) error message. Following the DRY principle, it would make sense to put that message in one variable shared across tests. From a tests-as-code perspective this makes perfect sense. From a tests-as-tests perspective, however, it does not, because it makes the test more difficult to read.<br>In cases like this I prefer to have easier to read tests over easier to maintain code.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Another thing is that when you're focused on one of the two perspectives, it sucks to be forced to switch to the other perspective. When you're in tests-as-tests mode, you're thinking about the software you're testing, about the problems it's trying to solve, the capabilities it tries to deliver. In tests-as-code mode, you're thinking about the code you're writing, how to make it do what you need it to and how to keep it maintainable. Switching between the two in a natural rhythm is fine; being forced to switch not so much.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>a programming language is a DSL</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>There are quite some testing tools and libraries that introduce a domain-specific language (DSL) to make writing tests easier. Their claim is that it's easier to learn their domain-specific language than it is to learn a general-purpose programming language.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>In my opinion that's not an entirely fair comparison. I don't need to learn all of Java or Python or ... to be able to build tests in those languages. I only need to learn the part of the language that's relevant to the building I want to do. Hence, a programming language is a domain-specific language.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Now I must admit that most DSLs are easier to learn than the required sub-set of a programming language. Even so, I prefer general-purpose programming languages for two reasons.<br>First of all, a DSL is limited to its domain. If you want to do something it wasn't designed for or something outside of that domain, you'll either need to switch to a different DSL or to a general-purpose language. Since that's bound to happen at some point, I'd rather learn a sub-set of a general-purpose language from the start and expand my knowledge of that language when needed.<br>Secondly, I think there's value for anyone who's part of software development, to have a basic understanding of programming. The best way to do that is to do things in code on a a regular basis - preferably as part of your job. Building tests is a great way for non-programmers to have that experience.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>revisiting my blogpost from 2015</strong></h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>As mentioned in the introduction, in 2015 I wrote a blogpost with the title "<a href="https://testingcurve.wordpress.com/2015/03/24/test-automation-five-questions-leading-to-five-heuristics/">Test automation – five questions leading to five heuristics</a>". So let's see revisit those heuristics more than four years later.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>Heuristic 0: Don’t call it test automation.</strong><br>I don't think I ever stopped calling it test automation. When I wrote the post, I was stricter in using the best possible words. Currently, my position is that if communication is happening, the words we are using are good enough. I do prefer the term "auto-tests" over "automated tests", since the latter still suggests to me that perhaps we might be able to "automate all the testing".<br>(And yes, I snuck six heuristics in my original post by starting with 0.)</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>Heuristic 1: Never trust a test you haven’t seen fail.</strong><br>Yep, see "<a href="#tests-for-your-tests">Do you have to write tests for your tests?</a>".</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>Heuristic 2: Each test should test only one thing.</strong><br>Yep, see "<a href="#one-thing-only">A test should do one thing and one thing only</a>".</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>Heuristic 3: It’s better to have reliable information that doesn’t exactly tell you what you want to know, than unreliable information that does.</strong><br>Not covered in this post, although it is related to having deterministic tests ("<a href="#conditional-logic">Is it ok to have conditional logic in your tests?</a>"). And I still agree: I'd rather have a reliable test that doesn't entirely test what I want to test, than an unreliable test that does (or more precise: tries to).</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>Heuristic 4: Every minute spent debugging test automation code is wasted, because you learn nothing.</strong><br>I was quite amused reading this, since it seems I was finding no joy at all in writing and debugging code. I don't think that was actually the case, but it is true that I enjoy programming more now than I did back then in 2015. The reason is quite simple: I've gotten better at it.<br>Setting aside the tone of that paragraph, I do see a link with what I have written above about <a href="#two-perspectives">tests-as-tests and tests-as-code</a>, and about how being forced to switch between them sucks.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>Heuristic 5: Epistemic testability, epistemic testability, epistemic testability.</strong><br>Revisiting the <a href="https://www.satisfice.com/download/heuristics-of-software-testability">definition of epistemic testability</a>, I don't think I was using the term the way James Bach intended. Be that as it may, I still stand by the point I was making: is your test automation helping you to do better testing? And by extension, helping you to develop and deliver software better?</p>
<!-- /wp:paragraph --></body></html>