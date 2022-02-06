<!--
.. title: An approach to teaching Agile 20 years after the Agile Manifesto
.. slug: an-approach-to-teaching-agile-20-years-after-the-agile-manifesto
.. date: 2021-04-26 16:54:34 UTC+02:00
.. tags: agile, ci/cd, devops, lean, teaching
.. category: agile
.. link: 
.. description: 
.. type: text
-->

For a few weeks I've been thinking about how I would teach Agile[^1] in 2021, 20 years after the [Agile Manifesto](https://agilemanifesto.org/) was published. After sharing my thoughts at [CitCon Europe 2021 Virtual](https://citconf.com/virtual2021/) and having an interesting conversation about the state of Agile and how to teach it, I feel it's time to share my thoughts here as well.

## Why I started thinking about this

As Allan Kelly stated in a [2018 blog post](https://www.allankellyassociates.co.uk/archives/2762/agile-won-the-war-but-lost-the-peace/):

> "Agile won the war but lost the peace."

Everyone is doing Agile, even though very few people are living the dream promised by Agile. This makes it very difficult to use "Agile" as a label, as a name for something. When someone says "Agile", are they referring to what you're already doing or to something they think you should be doing?

Additionally, the [Agile Manifesto](https://agilemanifesto.org/) was [written in 2001](https://agilemanifesto.org/history.html), based on what its authors were doing in the 1990s in response to the common ways of doing software development of that time. And since the Manifesto we've seen the introduction of Lean, of DevOps, and of CI/CD. So the amount of history that comes with Agile is large and it raises the question how much (if any) we should teach - especially since a lot of it is folklore instead of history[^2]. Doing Agile's history justice would probably cost more time than makes sense if your goal is to teach people how to develop software in an Agile way[^3]. And a lot of that history was a relatively long time ago, which is why I titled my CitCon session "Teaching Agile to people younger than the Manifesto".

<!-- TEASER_END -->

This leads us to the core question: if for as long as you've been in software development, everyone has been doing Agile, if you're not a blank slate and neither is your organization, what would you be interested in learning? What would you want to be taught? Or more importantly, how would you want to be taught?


## Three pillars: noticing - options - principles

The approach I envision is built around three pillars: noticing, options, and principles. The first two pillars, noticing and options, are heavily influenced by John Mason's book *"Researching Your Own Practice, The Discipline of Noticing"*. In this book he places these at the center of professional development:

> "All professional development could be described as changes in sensitivity to notice and accumulation of alternative actions to initiate." (p. 147)

The third pillar is principles of good software development. Not necessarily **the** principles of good software development, as the ultimate guide on how to do software, but a clear set of principles that clarify why you'd want to notice certain things or try out certain options.  And it's probably worth adding that by "software development" I mean software development in the broad sense, covering all of these five areas: collaboration, software engineering, work management, product, and reflect & experiment.

### Noticing
To be able to respond differently than on auto-pilot, to have a different response to a situation than our habitual one, we need to notice. As the quote often misattributed to Viktor Frankl[^4] says: 

> "Between stimulus and response there is a space. In that space is our power to choose our response. In our response lies our growth and our freedom."

Often we are unaware of that space. Response follows stimulus. The pause passes us by and with it our opportunity to choose. The *"discipline of noticing"* as Mason calls it, is what allows us to create that pause, by realizing that there is something worth noticing in the moment. This takes work and practice. At first, you'll probably only notice something in retrospect and then through practice be able to notice things earlier:

> "The real work in noticing is to draw the moment of awakening from the retrospective into the present, closer and closer to the point at which a choice can be made." (p. 76)

### Options
When we have created a moment of decision through noticing, we need to be aware of what options are available to us. If no options come to mind, the moment passes and we either do nothing, or fall back to our habitual response. As Virginia Satir is quoted in *"The Satir Model"*:

> "[...] to have one choice is no choice; to have two choices is a dilemma; and to have three choices offers new possibilities." (p. 143)

### Principles
The third and last thing we need, are guiding principles. A belief and value system that gives direction. It won't be perfect and it will need amending, but at least it will make explicit what to aim for. That helps us to figure out what is worth noticing, which options could make things better, and what that "better" means. So in short, principles that tell us what good software development is and what isn't.

### An example: applying the three pillars to the daily standup
Let's say you are doing your daily standups based on the three questions: (1) what did you do yesterday?, (2) what will you do today?, (3) are there any impediments in your way? One thing that would be good to notice is if decisions are being made during the daily standup. These could be decisions about priority, how to handle some unplanned work, or who will pair with whom. Let's say you notice very few decisions are being made. An option would then be to replace answering the three questions during the daily standup with walking the board. You start with the right-most column on the board, discuss the work items in that column and then move a column to the left. One of the principles we can link to this noticing (few decisions) and this option (walking the board) is to optimize for flow efficiency over resource efficiency. Which is to say, optimize for getting work items done over keeping team members busy with work at all times.


## My hopes for this approach
With this approach built on noticing, options, and principles, I hope to provide something that's concrete enough to be accessible while avoiding the rigidity of prescribing what exactly to do. Principles provide a clear perspective on what it means to do software development well, while noticing and options give you next steps from where you are now to making those principles come to life.

I accept that I might be a little too hopeful here. Software development is not an easy problem to solve, let alone teaching the skills that enable you to solve it. But I do believe this approach has a good chance of helping people to acquire that skill set and to deal confidently and comfortably with whatever situation, team, and organization they find themselves in.



[^1]: I'm going to ignore the Agile vs agile vs agility discussion in this blog post and stick with "Agile".

[^2]: Laurent Bossavit's [The Leprechauns of Software Engineering](https://leanpub.com/leprechauns/) is a great starting point.

[^3]: To be clear, I do value knowing and understanding the history of software development. It's the reason I started [this project](https://context-of-agile.org/).

[^4]: According to Quote Investigator the [most likely source](https://quoteinvestigator.com/2018/02/18/response/) is Stephen R. Covey paraphrasing a 1963 article by psychologist Rollo May without attribution, because he did not note the author's name.