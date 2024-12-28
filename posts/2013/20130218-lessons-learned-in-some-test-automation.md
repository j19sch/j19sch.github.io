<!--
.. title: Lessons learned in some test automation
.. slug: lessons-learned-in-some-test-automation
.. date: 2013-02-18 21:46:02 UTC+01:00
.. tags: test automation, VBA, programming
.. category: programming & test automation
.. link: 
.. description:
.. type: text
-->

In the past two weeks I built a test tool in VBA (Visual Basic for Applications). I did this, because two weeks ago my fellow tester showed me an important test we have to do at least once for each major release. The test consists of having the application generate three reports in Excel format. On two of these reports you apply a set of filters and take the sum of a few columns, rinse and repeat. Then you add several of those sums together and the results of those calculations should match the numbers in the third report. So basically, the point of the test is to check if the numbers in the three reports add up. And it's a lot of work, i.e. about two days.

After being shown how to perform the test, the first thought that popped into my head, was: "Boring!" The second thought was: "It's automatable!" And since there was little else to do - delivery of the new test environments was delayed - I changed it from automatable to automated.

So now, after two weeks, I have this tool in VBA. For each of the three reports it contains a sheet in which you define the sets of filters and sums. If you click a big button, the report is opened and the filters and sums are applied. There's also a fourth sheet to do the second set of calculations and to do the check if the numbers match. This last part is not done in VBA; it's all formulas in Excel.

<!-- TEASER_END -->

So that's all fine and good, except for this one thing: it took me almost two weeks to build. I think that a proper VBA developer could have built the same tool in about a day. Which raises the question: what value was there in me building the tool?


## Business case value
Well, first of all, the typical test automation business case still stands. I invested eight days and the gain is that a test that used to take two days, now takes about an hour. Run the test five times and we break even. Of course, instead of testing faster (do the same test in less time), we can also choose to test more thoroughly (do more tests in the same amount of time) or a combination of these two. Secondly, the tool I built is quite generic and thus reusable. Not that my current project cares all too much about this, but it is in the interest of my current employer.

With these two reasons, I could end this blog post.

The problem is that those reasons were not my main motiviation to build the tool. To be honest, my real motiviation was that it allowed me to exchange boring work in the future for interesting work now and I knew I could get away with it. Secondly, those reasons only capture part of the value in me building the tool. The part that's missing is that I learned a lot by building the tool.


## Other value: learning
So what did I learn?

### Lesson 1: VBA
Prior to this tool I knew almost nothing about VBA. In previous projects I have used some test tools built in VBA and it always annoyed me that my understanding of the code was limited to "I'm fairly sure you use Dim to initiate a variable..." So those days are gone now.

Morever, I learned I do not like VBA. Performance is quirky. Several times I got an error message that made no sense; closing and reopening the file fixed it. xlDown behaviour is inconsistent: it does something different depending if the cell below the current one is empty or not. And the code that did work on Friday, failed to work on Monday, although it was unchanged...[^1]

Even worse, I don't like the VBA documentation. If you show an error and a Help button, why send me to the main page instead of a page relevant to the error? If you link to the Glossary, why not link to the actual word I just clicked on instead of the top of the glossary? And then there is the information you can find online. Few tutorials and lots of forums with lots of different solutions. For one problem I had, I first found four not-so-good solutions until I ran into a good solution. That made me feel a bit lost as to where to get good information from.

### Lesson 2: Software development
Because of my lack of VBA knowledge, I got to explore the usefulness of incremental building. My first small victory was having code that copied one Excel sheet to anthor sheet. The second was filtering the sheet with hard-coded criteria before copying it. The third was making the code read those criteria from the excel sheet. etc. etc. Not only is this a good development method, it also kept me motivated.

Another thing I learned is that having experience in one programming language both makes it more easy and more difficult to learn a new one. A few years ago I wrote a test tool in Perl. While writing this new tool in VBA, I couldn't help but wanting to write the tool in Perl with VBA. That doesn't really work and even if it would have, that's not how you leverage the strenghts of VBA - if any :-) - to your advantage. So I not only had to learn how to write in VBA, but also how to think in VBA - instead of in Perl in my case[^2]. What did help was knowing about variables, loops, arrays, functions, etc.

Several times I could not resist to implement an ugly solution, because it was easier than figuring out a better solution. There's a very ugly If...Then...Else in the code, because I couldn't get an array to work irrespective of it containing one or many elements. I still feel a bit bad about it, but even after going through plenty of forum posts, I failed to find a solution that made the array work. On the other hand, it works and does not result in performance issues, so who cares it's ugly?

Finally, I encountered 'scope creep' - or 'discovering requirements as you go' depening on your perspective. The original plan was to just make a tool that did the filtering and the sums for each report. When I got there, I had the idea to make the tool do its work from one master Excel sheet. That's what the tool does now, but the formulas on the fourth sheet (to check report 1 and 2 against report 3) are just Excel formulas. It would be easy to write some code that would make this fourth sheet easy to change. And without a doubt, as soon as I get the tool to do that, I will have thought of something else I can add...

A second example of 'scope creep' is how I developed the tool with part of the test script for the reports, assuming it was representative for the rest. It wasn't, of course. For example, thinking I was smart, I took a complex case: multiple filters, multiple criteria and multiple sums, only later to discover my code failed in the case of a single filter, criterium or sum. Apparently, having the complex work, is no guarantee the simple will work as well. And that was just one of a handful examples of the actual test script being different from the part I was developing against.

Now, none of the things above are great new insights in software development, but seeing their usefulness unfold right before your eyes does not compare to reading about them and thinking "Yeah, I can see how that would work." I believe they call that experiential learning. :-)

In that regard the biggest thing I learned concerns testing: I do not consider my test tool tested.

Of course, I did plenty of tests while developping, but those were focused on the happy flow, on making the tool do what I need it to do. And as a developer I am very happy, because that's exactly what it does! What it does, is simply amazing compared to the nothing it did when I started development! So yeah, I'm sure any half-decent can tear it to shreds, but my focus is on all the cool things the tool can do. Not on problems that may or not may be there.

To discover this change of focus within me, was a bit weird. I consider myself to be a tester, not a developer at all, but because of my pride in what I have accomplished, I find it very difficult to get into a mindset that will allow me to tease out all the small (and big) problems in what I built.


### Lesson 3: Test automation
One thing I really like about the test tool is that the test script, the test tool and the test results are one. You can use the test tool to do the test automatically (well duh). You can also read the test tool, see what filters and sums need to be done and then perform these manually. And the test results end up in the same file that contains the test script/tool. So in this respect it really is a white box test tool - or glass box test tool, as glass is more transparent than white.

The code is also accessible to everyone, so that's white box too. However, two weeks ago I couldn't read VBA and it would have been a black box tool to me. And that would be a bad thing. Because the code is not really robust and perhaps one day the test script will need to be changed in a way that conflicts with the code. (Deselecting multiple filter criteria, for instance.) Or perhaps one day VBA has one if its quirks again and throws a 80010105 automation error.

And this is where test automation gets tricky. The more complex and useful your test tool becomes, the more likely it is you will need a tester (or perhaps even developer) with the suitable skills to support the tool. (A tool everyone can understand, is probably so simple, it is of little use.) In most cases getting this support is not much of a problem, but somewhere along the way you did cross the line between having an easily hackable tool and having a software testing application, which are two very different things. A tool can be used, modified and discarded easily. An application not so. Pen and paper are a tool; a word processor is an application.

Unfortunately, you move quite quickly outside of the tool territory. When I started building the tool, I thought the tool as such had value to the project. And as long as the tool doesn't need an update, that's true. Yet as soon as it does, it requires someone with knowledge of VBA and preferrably of the tool. Worst case scenario is that someone needs to learn and VBA and the tool to be able to do the update.

So what started with the thought "Hey, I can build a really cool tool to automate this test script." did result in a test tool, but also in a maintainability risk. And I'm not sure how to solve that. Investing the time to create proper documentation feels like overkill. (The code is commented, of course.) Simply trusting that when needed, someone with VBA skills will be available, feels uninvolved.


## Meta-lesson: quantifying the other value
The value in me having learned these things is hard to quantify. I can't say I am now able to do something in an hour instead of two weeks, because I learned these things.

On the other hand, if my employer expects me to develop myself (and supports me e.g. by paying course fees) and I manged to do so without it costing him anything (assuming we will run the test at least five times), why would I need to quantify it? It's all profit.

More importantly, however, why would I want to quantify it? Quantifying learning in this way means that you know beforehand what you need to learn, what it will cost you and what it will gain you. It implies a complete focus on the 'fully known unknown', being uncomfortable with the 'partially known unkown' and being completely oblivious to the 'unknown unknown'. And that's not what learning (or testing for that matter) is about.


---

*This post was originally published on my old blog.*


[^1]: And no, dear reader, the code does not refer to the current date or anything.

[^2]: Am still annoyed I have to tell VBA the length of an array before I can put something in it, though.
