<!--
.. title: How to run a remote Elephant Carpaccio
.. slug: how-to-run-a-remote-elephant-carpaccio
.. date: 2021-11-28 13:35:16 UTC+01:00
.. tags: workshop, elephant carpaccio, slices, agile, facilitation
.. category: workshop
.. link: 
.. description: Advice on how to run the the Elephant Carpaccio workshop remotely based on my experiences of running it three times.
.. type: text
-->


In a [previous post](link://slug/two-times-remote-elephant-carpaccio) I promised to write a blog post on how I would run remote [Elephant Carpaccio](https://web.archive.org/web/20171114154855/http://alistair.cockburn.us/Elephant+Carpaccio+exercise) if I get the opportunity to run it a third time. This is that post, but not exactly. In the mean time I got the opportunity to run the workshop one more time, so in the advice below I was able to incorporate what I learned by running the workshop once more.

And that's also the scope of this post: advice. It's not a full remote facilitation guide, but by reading the official(?) [facilitation guide](https://docs.google.com/document/d/1TCuuu-8Mm14oxsOnlk8DqfZAA1cvtYu9WGv67Yj_sSk/pub) and this blog post, you should have a solid base to run the Elephant Carpaccio exercise remotely.


## The preparation
Take your time to prep. Taking [as much time as the duration](link://slug/lessons-learned-after-facilitating-elephant-carpaccio#take-your-time-for-the-before-and-after) of the workshop is a good start. (That's assuming you are already familiar with the Elephant Carpaccio exercise, though. So if you're not, do that first.) Get a clear picture in your head what you want to achieve with the workshop. Run through it in your mind in detail. Decide which options you have in which parts of the workshop to make changes to the workshop on the fly.

Last but not least, set up all the practical stuff: the invite, the conference link, the virtual whiteboard link. How early you do this, depends on how much you expect participants to do before the actual workshop. Since it's a remote workshop my advice is to have them to do as much in advance as possible. I've had good experiences with asking participants to do two things in advance.

<!-- TEASER_END -->  

Firstly, to form into groups, decide on a programming language and set up a dev environment. To be fair, I've been running the workshop with people all working in the same department, so I simply asked them to do this. If people don't know each other that well, you probably should facilitate this more.

Secondly, I asked them to think about why you'd want to slice your features small and to add their thoughts to the workshop's virtual whiteboard. This gives the participants the freedom to do this when and how they want. More importantly it saves time, which is especially important in my opinion for anything that happens remotely. If it doesn't have to happen during the video call, then don't do it during the video call.


## The agenda
Although the [facilitation guide](https://docs.google.com/document/d/1TCuuu-8Mm14oxsOnlk8DqfZAA1cvtYu9WGv67Yj_sSk/pub) by  Henrik Kniberg and Alistair Cockburn suggests scheduling two hours for the workshop, in my experience the following 2.5-hour schedule works better:

- Walk-in & Intro (10 mins)
- Why slice small? (10 mins)
- Backlog breakdown (40 mins)
- Short break (10 mins)
- Development (45 mins)
- Short break (5 mins)
- Review (10 mins)
- Debrief (20 mins)


## Walk-in & Intro
During the Intro you set the tone for the rest of the workshop. If you give simple, clear, and concise instructions, everyone will be on the same page and you can proceed together. Accidentally introduce some confusion somewhere, then hopefully it will come to your attention and you'll be able to address it. If not, there will be some friction, some wobbliness.

The main things to cover in the Intro are the purpose of the workshop, the agenda, and the practical stuff. At the end of the Intro each participant should have a clear enough picture of what will happen when during the workshop. Which parts are with everyone and which are in breakout rooms? What goes where on the virtual whiteboard? How do the breaks work? (I would say: video off, mic muted, walk away from your desk.)

One thing to address that's specific to Elephant Carpaccio is whether it's two exercises or one exercise. The intention is for it to be one exercise: break down the backlog and build the stuff. Hence, there's only a debrief after the build/development-part. However, it is an exercise in two parts - the "and" in the description was a good clue, so make that explicit to the participants. In the debrief at the end it might be a good question to ask if this was one or two exercises, but during the exercise itself the question is an unwanted distraction.

A second thing to address is that this is an experiential workshop. Consider how familiar your participants are with these kinds of workshops and provide [guidance](link://slug/lessons-learned-after-facilitating-elephant-carpaccio#guidance-on-experiential-workshops) accordingly.


## Why slice small?
The goal of the "Why slice small?"-section is not to fully explore that question. Rather, it's short reminder of the value of slicing small, since it would be odd to do full workshop on slicing small without addressing the question at all.

What has worked for me is to ask the participants to add their thoughts to the virtual whiteboard in advance. During the workshop we cluster their stickies and discuss any sticky that warrants discussion, e.g. because it's not entirely clear or because another participant has a question about it.

Since it's not a deep dive into the reasons of slicing small, I don't think it's imortant to get an exhaustive list of reasons on the whiteboard. What I do think is important is there are at least one or two stickies for every category of reasons. For myself I've come up with the following four: better quality, sooner feedback, easier planning, delivering more often. This is certainly not the ultimate list, so I expect to keep adjusting it. For that same reason, I would encourage you to come up with your own. Where it has helped me in facilitating this part of the workshop, is that it allowed me to scan the stickies and decide if each of the four categories was sufficiently covered. If not, I would resolve that with some coaching questions.


## Backlog breakdown
The Backlog breakdown starts with an explanation of what features the participants will need to be build. Before having the participants split into their groups and create their backlogs, I like to discuss two questions with the whole group. The first question is: what is the first slice? And the second one: how can you slice the VAT feature?

This puts the participants on track to create a good enough backlog for the development part of the exercise. An alternative approach would be to first let the groups work on their backlog for a bit and then discuss the questions. However, in my experience this takes too much time, especially if one of the groups has gotten further off track.

One thing to keep in mind as the groups work on their separate backlogs, is how active you want to be as a facilitator. It can be tempting to try and help the groups to create the best possible backlog. I don't think that should be the goal¸ however. The goal is to have a good enough backlog with the groups feeling they created that backlog. Then they get to experience what it's like to develop the slices in that backlog, to finally reflect on the whole exerpience. Intervening to heavily will diminish that experience, as groups would be developing the slices from a backlog 'fixed' by the facilitator. Which is not to say, of course, that you as a facilitator should not redirect groups if they start making backlog decisions that go against the purpose of the workshop.


## Development
The main challenge of the Development part of the exercise are the demos. In-person each group is expected to demo to one other group at the end of each of the five iterations. I don't see that working remotely, because it's too much hassle moving between breakout-rooms. What I've been doing remotely is to have the groups post a screenshot or gif of their application on the shared virtual whiteboard at the end of each iteration.

The last time I ran the workshop, one group started posting a screenshot after each slice. As a result, they did not have to scramble to produce a screenshot at the end of each iteration. To the other groups, that scramble felt to me more like a disctraction than as something useful. So next time I run the workshop, I might ask all groups to their demo in this way.

These changes to how the demo works, does raise an important question about how important the iterations are in the exercise. If groups demo each slice when it's done by posting a screenshot, the iterations become meaningless. (Apart perhaps from keeping track of the progression of time.) Without a stakeholder to inspect the current product at the end of each of the five 8-minute iterations, you might as well have one block of 40 minutes of development time. And perhaps that does make more sense if the participants are used to deliver each story through CI/CD. Of if they don't have a stakeholder that needs to see finished work at the end of each iteration.


## The review
not sure what the purpose is of the acceptance test: interesting there are differences but no time for follow-up
have each group demo and include the acceptance test?several questions about out-of-scope stuff


## The debrief

What was it like? is goed begin, maar dan wat?
	splitsen in Breakdown en Development?
huidige structuur is wel: What? So what? Now what? maar ben niet helemaal tevreden

good conversation after
needs longer debrief or follow-up with participants
people have lots of questions still, need to discuss more



## More notes

- Stuff I mentioned in the previous posts I would try
	- time
	- Miro
	- how to slice discussion
	- hopping around breakout rooms


- Ask how well people are slicing currently during why slice small?
	- Then what?
	- Will that lead to meaningful answers?