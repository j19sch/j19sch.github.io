<!--
.. title: Reflections after writing a release advice
.. slug: reflections-after-writing-a-release-advice
.. date: 2026-02-08
.. category: software testing
.. tags: test reporting, test management, communication, software testing
.. type: text
.. description: Or was it rather a release intention document?
-->

Recently I had to write a release advice. My first thought was: *"I have close to two decades of experience in testing. I got this!"* My second thought was: *"I haven't written a release advice in over ten years, how do I do this again?"*

Luckily the first thought reflected reality a lot better than the second one. And after reviews by my team members, my project lead, and my manager, I'm proud of the end result. Even though in some ways the document has ended up more like a release decision, than a release advice. (More on that later.)


# Lead with the actual advice {.small}

Initially I was going to start the document with a management summary, then an introduction, an overview of the testing that was done, the relevant known issues and remaining risks, then the actual release advice and finally some ideas on how to improve our testing further. Quite soon I realized that didn't make sense.

<!-- TEASER_END -->

Why bury the most important part, the actual advice, at the end, while also summarizing it at the start? Why not start with the most important part, then the next most important, etc.? Precede all that with a table of contents, so people can decide to either follow along or pick their own order of reading.

So instead of that initial convoluted order, I ended up with: advice, known limitations, fallback plan, overview of the testing done, ideas on how to improve the testing. Arguably those ideas for improvement are more important than the overview of the testing, but the overview provides useful context. And also, those ideas are not relevant for the current release like the rest of the document, only for the next one.

<!-- As they say in journalism: *"Don't bury the lede."* Don't start with context, with fluff, with information building up to a conclusion you haven't even introduced yet. Start with the main point.[^1] In the case of a release advice the main point is the answer to the questions: *"Is it good enough?"* and *"Why might it not be good enough?"*

[^1]: For some great advice on how to use different structures for different kinds of communication, see Elizabeth Zagroba's ["Communicate Using Three Layers of Information"](https://elizabethzagroba.com/posts/2022/05_12_give_them_just_enough/).
 -->

# No alarms and no surprises {.small}

If your release advice contains major surprises for your readers, you have a communication problem. Not that they need to be so well-informed, they could have written the thing for you, but they should be familiar with the gist of it in advance.

I forgot where I got this from (please let me know if you know), but there's this idea, I think from control theory, that you need at least two iterations for feedback to be meaningful. You do a thing, you get feedback, you adapt to the feedback, you get feedback on how you adapted. If the first time that your stakeholders hear about the results of your testing, is all the way at the end, from a document, then their opportunity to steer or influence the testing has evaporated. All they can do, is hope their feedback makes a difference for the next release.


# Document the decisions already made {.small}

In the introduction of this post I mentioned the document ended up being more of a release decision than a release advice. In general I'm very wary of test engineers being asked (usually implicitly) to decide to release or not. They don't have the authority, nor get a large enough paycheck to make that decision.

In this case, that's not what happened. The release advice was reviewed by my team mates, my project lead, and my manager (head of the IT department). So even though I was the main author of the document, the end result was very similar to the software produced by my team. It may start out as my code or your code, but once we've reviewed and tested it as a team, it's our code.

The result of all of this was a document that was more like *"We intend to release this."*[^3] than *"Can we release this?"* We did still need approval from my manager's manager, but he was presented with a document that said *"It's good enough to release. Here's how we will mitigate three relevant limitations. And this is our fallback plan."* Not with a document that said: *"Here's why you should decide it's good enough. Good luck mitigating the limitations and organizing a fallback plan."* Not only would that have been a lot less helpful, it wouldn't be an honest reflection of how we do our work.

[^3]: See ["Turn the Ship Around!"](https://davidmarquet.com/books/turn-the-ship-around-book/) by L. David Marquet for more on intent-based leadership.


# No defects count, no test cases count, no code coverage percentage {.small}

The release advice does not report any numbers. Not number of defects found, not number of test cases executed, not percentage of code coverage. The first two numbers, defects and tests cases, we don't even track[^2]. And while we do track code coverage, providing enough context to make it a meaningful number, would take up more space in the release advice than that piece of information is worth.

[^2]: We have a [zero ~~defect~~ bug policy](https://smallsheds.garden/slides/testbash25-peculiar-quality.html#/24), so what exactly would we be counting? Our testing is either exploratory or through test automation, so again, what would we be counting?

When people do ask for these kinds of numbers, my favorite heuristic is: *"If I gave you a randomly generated number, would you be able to tell?"* In practice I prefer to use kinder versions: *"What ranges would you expect these numbers to be in?"* or *"What kinds of decisions would these numbers inform for you?"* Because I do believe there is a valid, genuine need behind the request for these kinds of numbers. I just don't believe that in most cases these numbers are the best way to satisfy that need.

While I was ready to have the conversation about these numbers, the request to include them never came. And based on older release advices in the organization and on what I hear from people online, I kind of was expecting the question. So it goes to show yet again: you can imagine all kinds of things about what people expect, you won't really know until you talk with them.

---

*If you can read Dutch (or are willing to parse (pass?) it through a translation tool), the [full release advice](https://github.com/kiesraad/abacus/blob/af935ce1919de4eaef8e5c785e624d515d84f32e/documentatie/vrijgaveadviezen/Vrijgaveadvies-Abacus-v1.0.1.md) is available on GitHub.*
