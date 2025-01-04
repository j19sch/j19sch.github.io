<!--
.. title: My five favorite testing questions
.. slug: my-five-favorite-testing-questions
.. date: 2023-05-03 08:57:25 UTC+02:00
.. tags: software testing, exploratory testing, heuristics
.. category: software testing
.. link: 
.. description: 
.. type: text
-->

Recently I realized there are a few testing questions I use a lot. They lie at the top of my testing toolbox, so to speak. Together they shape my testing style, making it easier for me to discover certain things, but probably also harder to find other kinds of things. So here are my five favorite testing questions, in no particular order.


# What if there are zero, one, many, lots of this thing?<a id="zero-ony-many-lots-oops" />

Last year I expressed my surprise [on Mastodon](https://chaos.social/@joeposaurus/109427704814392787) how many times I've found bugs by asking the question: *"What if there are 0 / 1 / several / lots of this thing?"* And if you're working closely enough to the code, you should also ask about "null".

Quite a few people responded to my message. Turns out it's a [very](https://www.qwan.eu/2021/07/09/tdd-0-1-n.html) [common](http://blog.wingman-sw.com/tdd-guided-by-zombies) [pattern](https://mas.to/@zebulon/109428667658139893) in TDD. And Brian Marick[^1] remembered it [standing out](https://mstdn.social/@marick/109428042023981110) when he was looking into fixed bugs in the Linux kernel they used in the '80s. Personally I learned it from Elisabeth Hendrickson's ["Test Heuristics Cheat Sheet"](https://web.archive.org/web/20150217124452/http://testobsessed.com/wp-content/uploads/2011/04/testheuristicscheatsheetv1.pdf), which found a [new home](https://www.ministryoftesting.com/articles/ab1cd85c?s_id=14715206) last year at the Ministry of Testing.

[^1]: If you're not yet listening to his podcast [Oddly Influenced](https://podcast.oddly-influenced.dev/), you should!


<!-- TEASER_END -->


# How would this work for the user?

Often there's a large distance between discovery (discovering what users need) and implementation. Not just in time, but also in who's involved. Information from discovery becomes an initiative, becomes an epic, which gets broken down into work items and often those again in tasks. Somewhere along the way - where exactly varies - developers get involved. However, despite their access to the results of discovery, the day-to-day work of developers is very much focused around a single work item with acceptance criteria or requirements. And that's a [problem](link://slug/our-work-management-tools-are-limiting-our-imagination). Working this way nudges developers towards limiting themselves to just delivering single work items according to spec, losing sight of the bigger picture.

To counteract this nudge, I like to ask: *"How would this work for the user?"* What problem is the user trying to solve? What are they trying to achieve? And can I imagine how the user gets their thing done, step-by-step, using the software? Often enough, there are gaps. Or some things are presented in a way or expected to be done in a way that would not make sense to a user.

The great thing about this question is that you can start asking it early, during refinement or even before that. A rephrasing of this question for that stage is: *"Can I imagine myself demoing this feature?"*


# What about time?

For some reason, people seem to default to a functional programming-like perspective when thinking about software. There's input, the input gets transformed one or multiple times, until we get output. This makes us overlook that stuff changes over time. And keeping track of time, also means having date and time as input. Hence the testing question: *"What about time?"*

## Time data as input

Time data as input is tricky, as illustrated so well by Noah Sussman's ["Falsehoods programmers believe about time"](https://infiniteundo.com/post/25326999628/falsehoods-programmers-believe-about-time).

It gets even trickier when time data is input without you fully realizing it. A few months ago I found a bug where a web application took midnight current day in the user's time zone, converted it to UTC and then used the date part of that UTC timestamp to determine the date. So for people in time zones ahead of UTC (basically the whole Eastern hemisphere) the application had an incorrect date[^2].

[^2]: I investigated if we could fix the data, based on the assumption that there's no overlap between time zones ahead of UTC and those behind of UTC. That assumption turned out to be wrong. Samoa Standard Time is at UTC-11, while West Samoa Time and New Zealand Daylight Time are on UTC+13. So they are on the same time, but on a different date.

## Stuff happens in time

As Ray Cummings wrote: *"Time is what keeps everything from happening at once."*[^3] Unfortunately we work with computers, so we not only have to deal with things changing over time, but also with several things that do happen all at once, i.e. concurrency. Things can be fast or slow (like internet connections). Sometimes one thing is slower than usual and another faster, i.e. a race condition. (I once "fixed" a race condition by adding a single line of logging.)

[^3]: [https://quoteinvestigator.com/2019/07/06/time/](https://quoteinvestigator.com/2019/07/06/time/)

Sometimes things also stay the same over time. Decisions have an effect far after they were made. The most extreme example I have come across was around 2010. Noticing that the data model was odd, I asked why that was the case. The answer was that when the mainframe was implemented in 1974, they had retained the data model of the punch card system that was being replaced by the mainframe. And there also was some really old data in there, since the product it supported was life insurance policies. 

I learned this heuristic of thinking about time from [Rapid Software Testing](https://rapid-software-testing.com/)'s ["Heuristic Test Strategy Model"](https://www.satisfice.com/download/heuristic-test-strategy-model). It has a great mnemonic for product elements, SFDIPOT, where the "T" stands for time.


# What can I discover by interacting with it?

Basically, exploratory testing. You can't come up with everything you want to test beforehand.[^4] You also can't come up with everything you want to test based solely on acceptance criteria, requirements, domain knowledge, etc. Some things you can only discover through interacting with the software. And a lot of things can be discovered a lot more easily through exploratory testing than in any other way. Instead of testing based on what you can imagine about the software in your head, you use the software itself as your "external imagination"[^5].

And do note that *"What can I discover by interacting with it?"* is not limited to interacting with the software in the same way as a user would. If there's something to interact with (a UI, an API, a database, a configuration file, a line of code), you can do exploratory testing.

[^4]: If you could, waterfall would work. Write your test cases, rename them to requirements. Provide them to the devs. Have the devs build the software and the automated test cases in parallel. Done.

[^5]: *"Exploratory testing is an approach to testing that centers learning. Test design and test execution form an inseparable pair where the application and feature we are testing is our external imagination."* - ["Exploratory Testing Foundations"](https://dev.to/maaretp/exploratory-testing-foundations-4lb3) by [Maaret Pyhäjärvi](https://maaretp.com/) 

I learned how to do exploratory testing by participating in [James Lyndsay](https://www.workroom-productions.com/)'s excellent workshop "Getting a Grip on Exploratory Testing". I wrote about that experience in [this post from 2012](link://slug/some-thoughts-after-attending-the-getting-a-grip-on-exploratory-testing-workshop).


# What do you mean by &lt;some term&gt;?

Usually people understand each other just fine. They use the same term and even though there will never be a perfect 100% overlap in meaning, there is sufficient overlap that for all practical purposes, they are using the same term in the same way. Sometimes, however, there is a shallow agreement. People think they agree on what a term means, but in at least one important aspect, they don't. When you suspect that's the case, it's time to ask: *"What do you mean by &lt;some term&gt;?"*

One of the biggest bugs I ever found was when I asked: *"What exactly do you mean by 'buffering'?"* One party thought it meant they needed to buffer the first 100 undeliverable messages and could discard the rest. The other party thought that during their downtime every undeliverable message would be buffered for later delivery. My simple question in preparing the end-to-end test got the whole project sent back to the architect.

I think I learned to do this as part of getting my degree in philosophy. Having a good idea of what a philosopher means with a specific term and how that fits into their world view, is a crucial part of understanding what a philosopher wrote.

---

Enough about my favorite testing questions. What are your favorite one? Are some of them the same as mine? Which other ones do you use? What things are easier to find thanks to your favorite questions? And what things might you overlook?
