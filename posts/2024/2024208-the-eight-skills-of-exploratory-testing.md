<!--
.. title: The eight skills of exploratory testing
.. slug: the-eight-skills-of-exploratory-testing
.. date: 2024-12-08
.. category: exploratory testing
.. tags: exploratory testing, quality engineering, software development, software testing
.. type: text
.. description: Exploratory testing is a learned skill. Which skills? These eight!
-->

TODO:

- add link to this post on being intentional about ET post
- check title, slug, filename
- add description

---


Exploratory testing is a learned skill, as I claimed in my previous post *["Being intentional about exploratory testing"](link://slug/being-intentional-about-exploratory-testing)*. In that post I mentioned the importance of two skills: noticing what there is to notice and deciding what to do next.

Turns out it's not the first time I mentioned that pair of skills. In a post about [how to teach Agile](link://slug/an-approach-to-teaching-agile-20-years-after-the-agile-manifesto#noticing-options-principles), I quoted from John Mason's *"Researching Your Own Practice, The Discipline of Noticing"*

> All professional development could be described as changes in sensitivity to notice and accumulation of alternative actions to initiate. (p. 147)

That does raise the question if the skills of exploratory testing can't be made a little more specific. So I've come up with six additional skills, making a total of eight. For some reasons they ended up as questions rather than verbs. I like how that makes this post less of a checklist and more of a tool for self-reflection. Each skill could be its own blog post, so I'm going to focus on one key element of each skill.

<!-- TEASER_END -->

# The eight skills {.small}

1. What do you notice while testing?
1. How do you decide what to do next?
1. How many alternatives can you imagine?
1. How do you model the different aspects of what you're testing?
1. How rich an varied are the oracles you use for evaluating what you discover?
1. How do you record what you notice and decide and do while testing?
1. What tools do you use that support, extend and/or amplify your testing?
1. What do you leave behind for future use?


# What do you notice while testing? {.small}

The skill of noticing is the foundation of many of the other skills of exploratory testing. What you don't notice, is gone.

There are two aspects to this skills: external noticing and internal noticing.

External noticing is noticing what's going on with the thing you are testing. Do you notice everything that's there? All the elements presented to you? Or were you quickly filling in fields and clicking buttons? And do you notice everything that's happening? Did the screen just refresh in an odd way?

Internal noticing is noticing what's going on with you as you test. It's being aware of your thoughts, your feelings, your decisions. Do you feel bored? Surprised? Do you feel your attention slipping? Are you aware of making a decision or did it just happen? Are you focusing and going deep? Or defocusing and going wide? Is it time to switch from the one to the other?

Of course I'm not going to claim it's possible to notice everything all the time, internally and externally. Awareness of both is key to good exploratory testing, though.


# How do you decide what to do next? {.small}

You can't test everything. You have to make decisions on what to explore further and what to let be (at least for now). [Heuristics](link://slug/being-intentional-about-exploratory-testing#learned-skill) are the tools to make these decisions. The trick with heuristics is that they are fallible. They're like looking for you lost keys at the last place you saw them. You might find your keys in that place, or when you get there you might remember where they are, or you might not find them at all. It's still a good thing to try, though.

This means that (as with any non-trivial decision) you might make the right decision, apply a good heuristic for the situation at hand, but not get a good outcome. You are doing exploratory testing after all, you're looking for surprises. You can be looking in all the right places, but the surprises just aren't there. That's just the way it goes sometimes. Doing excellent testing and not having that much to show for it.


# How many alternatives can you imagine? {.small}

There's an exercise that's sometimes used when interviewing test engineers. The interviewer shows a brick and asks the candidate: "What can you do with this?" Ideally, the candidate keeps coming up with new ideas and after a few minutes the interviewer has to stop them.

Coming with an endless range of alternatives is a key testing skill. Things to observe, things to try, things that might happen. I think it's the skill that gets testers to be called "creative". They come at things from different angles. Some of them contradicting each other. Some of them challenging boundaries, assumptions and constrains. (For example: "Does the brick need to stay whole?")

A thing is never a single thing, it contains multitudes.


# How do you model the different aspects of what you're testing? {.small}

A model is a simplified representation. It's a choice to amplify some aspects and mute others. To bring some aspects to the forefront and to hide others.

A classical example of a model is a map. It hides and simplifies many things so that it can better show you what it wants you to show. Whether it's a tourist map, a road atlas, or a map with election results. They were made with a purpose in mind and that purpose determines how useful that particular map is for certain things. (While you could use [this map](/images/2024/waterkaart_Rdam_klein.jpg) to navigate the streets of Rotterdam, it's more useful when you're on a boat.)

When it comes to testing, some of the most common models are input/output, state, and flowcharts. Notice that as with maps, they are not mutually exclusive. They complement each other. There are also some collections of models, such as the "Product Factors" (SFDIPOT) of the [Heuristic Test Strategy Model](https://www.satisfice.com/download/heuristic-test-strategy-model). Or the [quality characteristics](https://thetesteye.com/posters/TheTestEye_SoftwareQualityCharacteristics.pdf) of the [The Little Black Book on Test Design](https://thetesteye.com/blog/2011/09/the-little-black-book-on-test-design/).

A key part of modeling is being able to model what you can't directly see. As you explore, as you try things and notice how what you're testing responds, you build a model of how things/it might work[^1]. Part of that overall model are the smaller models mentioned earlier.


[^1]: This kind of reasoning is called [abduction](https://plato.stanford.edu/entries/abduction/) or abductive reasoning.



# How rich an varied are the oracles you use for evaluating what you discover? {.small}

Exploratory testing is not just about exploration and discovery. It's also about evaluation. You found some interesting behavior. Is it good? Is it bad? Maybe you haven't decided yet? The things we use to make this decision, are traditionally called "oracles"[^2] in testing.

[^2]: "Oracle" may just be my least favorite term in testing. One day I should do some research into how we adopted this term.

An excellent list of oracles is Michael Bolton's [FEW HICCUPS](https://developsense.com/blog/2012/07/few-hiccupps). It does a great job at showing if we're only testing against requirements or acceptance criteria, we'll be missing a lot.

For another and quite different list of oracles, there's the [transcript](https://associationforsoftwaretesting.org/2023/01/10/the-often-overlooked-test-oracle/) of Doug Hoffman's webinar "The Often Overlooked Test Oracle".

All this to say that applying oracles to evaluate what you find as you test, is a lot more involved than checking things off a list.


# How do you record what you notice and decide and do while testing? {.small}

The only way I know how to do this and do it well, is by taking good notes. Screenshots and videos are great supporting materials, but they don't capture your thoughts, your feelings, your decisions. And if you're going to watch a narrated video of a test session, you might as well do the testing yourself.

So how do you take good notes? Some basic markup goes a long way. Label the page with a title and a date. Make notes as you test. Use a system to mark things: "?" for a question, "!" for something remarkable, "B" for a bug, a light bulb for an idea for further testing, "OK" if something looks good, a "+" for something good you want to share with the developer(s). It's easy and quick to add these marks when you test. And it helps you to find the key points of your testing.

Secondly, embrace that the notes are for you and just for you. If you decide to share your raw notes and someone finds them useful, great. If they find them inscrutable, what did they expect? Transforming your notes to something more widely useful, is a different skill.




# What tools do you use that support, extend and/or amplify your testing? {.small}


# What do you leave behind for future use? {.small}
test reports, test guides, test automation? test scripts


---

# notes

## skills mentioned in previous post

heuristics, noticing, deciding

Having these lists of heuristics is a great start, but applying them hinges on two skills: noticing what there is to notice, and choosing the right heuristic to apply. Neither can be done perfectly. You can't notice everything. You can't know upfront what the exact right heuristic is.

But you can do these (noticing and deciding) rather well or rather poorly. And that's the invisible skill of exploratory testing. Invisible, because it's all in the mind of the person doing the exploratory testing. And as any other skill, exploratory testing can be practiced and refined. It's not something some people just happen to do well, while others don't.

## learning needs doing

What's crucial to me in that list, is that the skill in exploratory testing is in doing the exploratory testing. So the best way to learn, is to pair up or ensemble with others, preferably including someone who already has built up quite some skills. And as you test, reflect on what you're doing and discuss it with each other.