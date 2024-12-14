<!--
.. title: The nine skills of exploratory testing
.. slug: the-nine-skills-of-exploratory-testing
.. date: 2024-12-08
.. category: exploratory testing
.. tags: exploratory testing, quality engineering, software development, software testing
.. type: text
.. description: Exploratory testing is a learned skill. Which skills? These nine!
-->

TODO:

- NINE skills
- add link to this post on being intentional about ET post
- check title, slug, filename
- add description
- layout of list of skills can be better
- every question should fit on a single line
- improve phrasing of key elements

---


Exploratory testing is a learned skill, as I claimed in my previous post *["Being intentional about exploratory testing"](link://slug/being-intentional-about-exploratory-testing)*. In that post I mentioned the importance of two skills: noticing what there is to notice and deciding what to do next.

Turns out it's not the first time I mentioned that pair of skills. In a post about [how to teach Agile](link://slug/an-approach-to-teaching-agile-20-years-after-the-agile-manifesto#noticing-options-principles), I quoted from John Mason's *"Researching Your Own Practice, The Discipline of Noticing"*

> All professional development could be described as changes in sensitivity to notice and accumulation of alternative actions to initiate. (p. 147)

That does raise the question if the skills of exploratory testing can't be made a little more specific. So I've come up with seven additional skills, making a total of nine. For some reasons they ended up as questions rather than nouns. I like how that makes this post less of a checklist and more of a tool for self-reflection. Each skill could be its own blog post, so I'm going to focus on one key element of each skill.

<!-- TEASER_END -->

# The nine skills of exploratory testing

1. What do you notice while testing?
	- key element: internal and external noticing
1. How do you decide what to do next?
	- key element: good decisions do not guarantee good outcomes
1. How many alternatives can you imagine?
	- key element: a thing is never a single thing
1. How do you model the different aspects of what you're testing?
	- key element: model what you can see and what you can infer
1. How rich an varied are the oracles you use for evaluating what you discover?
	- key element: there are many oracles besides requirements and acceptance criteria
1. How do you record what you notice and decide and do while testing?
	- key element: it all starts from note-taking
1. What tools do you use that support, extend and/or amplify your testing?
	- key element: there's always more to learn, choose wisely, always be learning, always on the lookout to add a new tool to your kit
1. How do you communicate your test results?
	- key element: many different opportunities, except not sharing at all; testing is only as valuable as its report; testing is only as good as its report
1. What do you leave behind for future use?
	- key element: test automation is a great thing to leave behind


## What do you notice while testing?

The skill of noticing is the foundation of many of the other skills of exploratory testing. What you don't notice, is gone. There are two aspects to this skills: external noticing and internal noticing.

External noticing is noticing what's going on with the thing you are testing. Are you noticing what's there? All the different elements presented to you? Or were you quickly filling in fields and clicking buttons? And are noticing things that happen? Did the screen just refresh in an odd way?

Internal noticing is noticing what's going on with you as you test. It's being aware of your thoughts, your feelings, your decisions. Do you feel bored? Surprised? Do you feel your attention slipping? Are you aware of making a decision or did you just do a thing? Are you focusing and going deep? Or are you defocusing and going wide? Is it time to switch from one to the other?

Of course, it is not possible to notice everything all the time, internally and externally. Awareness is key to good exploratory testing, though. You need to be paying attention.


## How do you decide what to do next?

You can't test everything. You have to make decisions on what to explore further and what to let be (at least for now). [Heuristics](link://slug/being-intentional-about-exploratory-testing#learned-skill) are the tools to make these decisions. The trick with heuristics is that they are fallible. They're like looking for you lost keys at the last place you saw them. You might find your keys in that place, or when you get there you might remember where they are, or you might not find them at all. It's still a good thing to try, though.

This means that (as with any non-trivial decision) you might make the right decision, apply a good heuristic for the situation at hand, but not get a good outcome. You are doing exploratory testing after all, you're looking for surprises. You can be looking in all the right places, but the surprises just aren't there. That's just the way it goes sometimes. You did some excellent testing, but unfortunately don't have that much to show for it.


## How many alternatives can you imagine?

There's an exercise that's sometimes used when interviewing test engineers. The interviewer shows a brick and asks the candidate: *"What can you do with this?"* Ideally, the candidate just does not stop coming up with new ideas, until the interviewer says that's enough, thank you.

Coming with an endless range of alternatives is a key testing skill. Things to observe, things to try, things that might happen. I think it's the skill that gets testers to be called "creative". They come at things from different angles. Some of them contradicting each other. Some of them challenging boundaries, assumptions and constrains. (For example: *"Does the brick need to stay whole?"*)

A thing is never a single thing, it contains multitudes.


## How do you model the different aspects of what you're testing?

A model is a simplified representation. It's a choice to amplify some aspects and mute others. To bring some things to the forefront and to hide others.

A classical example of a model is a map. It hides and simplifies many things so that it can better show you what it wants you to show. Whether that's a tourist map, a road atlas, or a map with election results. They were made with a purpose in mind and that purpose determines how useful that particular map is for certain things. (While you could use [this map](/images/2024/waterkaart_Rdam_klein.jpg) to navigate the streets of Rotterdam, it's more useful when you're on a boat.)

When it comes to testing, some of the most common models are input/output, state, and flowcharts. Notice that as with maps, they are not mutually exclusive. They complement each other. There are also some collections of models, such as the "Product Factors" (SFDIPOT) of the [Heuristic Test Strategy Model](https://www.satisfice.com/download/heuristic-test-strategy-model). Or the [quality characteristics](https://thetesteye.com/posters/TheTestEye_SoftwareQualityCharacteristics.pdf) of the [The Little Black Book on Test Design](https://thetesteye.com/blog/2011/09/the-little-black-book-on-test-design/).

A key part of modeling is being able to model what you can't directly see. As you explore, as you try things and notice how what you're testing responds, you build a model of how something might work[^1]. Part of that overall model are the smaller models mentioned earlier.


[^1]: This kind of reasoning is called [abduction](https://plato.stanford.edu/entries/abduction/) or abductive reasoning.



## How rich and varied are the oracles you use for evaluating what you discover?

Exploratory testing is not just about exploration and discovery. It's also about evaluation. You found some interesting behavior. Is it good? Is it bad? Maybe you haven't decided yet? The things we use to make this decision, are traditionally called "oracles" in testing[^2].

[^2]: "Oracle" may just be my least favorite term in testing. One day I should do some research into how we adopted this term.

An excellent list of oracles is Michael Bolton's [FEW HICCUPS](https://developsense.com/blog/2012/07/few-hiccupps). It does a great job showing that if we're only testing against requirements or acceptance criteria, we'll be missing a lot. For another and quite different list of oracles, there's the [transcript](https://associationforsoftwaretesting.org/2023/01/10/the-often-overlooked-test-oracle/) of Doug Hoffman's webinar *"The Often Overlooked Test Oracle"*.

All this to say that applying oracles to evaluate what you find as you test, is a lot more involved than checking things off a list.


## How do you record what you notice and decide and do while testing?

The only way I know how to keep track of my testing and to do it well, is by taking notes. Screenshots and videos are great supporting materials, but they don't capture your thoughts, your feelings, your decisions. And if you're going to watch a narrated video of a test session, you might as well do the testing yourself.

So how do you take good notes? Some basic markup goes a long way. Label the page with a title and a date. Make notes as you test. Use a system to mark things: "?" for a question, "!" for something remarkable, "B" for a bug, a light bulb for an idea for further testing, a check mark if something seems to be working, a "+" for something good you want to share with the developer(s). It's easy and quick to add these marks when you test. And it helps you a great deal when navigating your notes.

Secondly, embrace that the notes are for you and just for you. If you decide to share your raw notes and someone finds them useful, great. If they find them inscrutable, what did they expect? That's not their purpose. Transforming your notes to something more widely useful, is a different skill.


## What tools do you use that support, extend and/or amplify your testing?

"Tools" is a broad category. Some people say their favorite testing tool is their brain. Or you could say that a pen and paper to take notes with, are a tool. Both are fair points, but here I'd like to treat those kinds of tools as a given.

Rather, the question is: Beyond sitting behind a computer with pen and paper and with your brain engaged, what more tools do you use while testing? Tools like the dev tools in your browser, the features of your IDE, a script you wrote that does something useful, a diffing tool, some test automation, a data visualization tool, or just a spreadsheet.

Using tools, lets you do so much more and better and faster than without tools. So learn to use the appropriate tools for the situation at hand. There are so many, that arguably you should always be learning.


## How do you communicate your test results?

Once you've done some testing and made notes of your testing, you still don't have much. You have information in your head and your notes to support your memory. If you stop there, you might as well not have done any testing at all.

So what do you do with that information? How do you report about your testing? When? In what format?

The good (and the bad) news is that are many different ways to report on your testing. It might be a full-blown test report. It might be a message in chat. It might be a fix for the bug you found. Or a branch with a failing test. It might be an update in your daily standup meeting.

Even if your team doesn't expect much more than a list of bugs you found, it's valuable to share more. Tell the [three-part testing story](https://developsense.com/blog/2018/02/how-is-the-testing-going) of what you learned about the product, what you did to learn those things, and what made that learning easier or harder.


## What do you leave behind for the future?

<!-- nor for future use, what do you leave behind that's useful in the future -->

Once you've done your testing and your reporting, there's still the question of what you leave behind that will be useful in the future.

A lot of the useful stuff comes from your notes. If you've made a model while testing, make a cleaned-up version of the model. If you've come up with test ideas, put them in a list. If you've found a really convenient way to do something, document it. If you discovered a risky area of the application or certain bugs that keep popping up, write those down somewhere. And crucially, share these things. Don't keep them for yourself.

Perhaps more useful than any of those, is leaving behind test automation. What better way to capture the important things you learned, in something that anyone on the team (and your pipeline) can run. So it's not that you're automating the (exploratory) testing. Rather it's that [test automation is an output of exploratory testing](link://slug/being-intentional-about-exploratory-testing#exploratory-and-prescribed-testing).

---

What do you think of these nine skills? Do you recognize them? Do you feel confident in all nine?  Is there a tenth skill that I missed?
