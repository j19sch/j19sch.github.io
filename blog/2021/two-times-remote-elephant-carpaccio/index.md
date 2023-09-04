<!--
.. title: Two times remote Elephant Carpaccio
.. slug: two-times-remote-elephant-carpaccio
.. date: 2021-10-03 21:28:50 UTC+02:00
.. tags: workshop, elephant carpaccio, small steps, agile, facilitation
.. category: workshops
.. link: 
.. description:
.. type: text
-->

A while ago I asked the teams in my department which parts of agile software development they wanted to learn more about. One of the topics that stood out, was: you have a high-level description of a new feature, then what? That's still quite a wide topic, so the question become on what part of that problem would I focus first.

Quite quickly I settled on feature slicing - for several reasons. First of all, I had noticed teams delivering somewhat big chunks of functionality, split up into development tasks instead of vertical slices. Secondly, a team I had worked with on feature slicing, had gained some valuable planning flexibility because of it. And they continued the practice, breaking up projects vertically. Finally, I was aware that there was a workshop called "Elephant Carpaccio", focused on feature slicing. So I could use that, or build on it, but at least I wouldn't have to come up with something from scratch.


## The Elephant Carpaccio exercise
The Elephant Carpaccio exercise was invented by Alistair Cockburn[^1]. Its purpose is to get people to practice _"nano-incremental"_ development, i.e. slicing something small enough you can program it in 15-30 minutes. The exercise tries to bring home its point through exageration: you are asked to slice a very simple application in 15-20 slices, where you would normally do it in 2-3 slices. Then you get five iterations of 8 minutes to build those slices. To me that's the coolest part of the exercise: you actually get to experience what's it like to work with such small slices. As Alistair Cockburn himself says about the exercise: _"the true learning is the actual programming section"_.

<!-- TEASER_END -->

I am not going to describe the exercise in more detail, since there are some great pages online that do exactly that already:

- Alistair Cockburn's pages about [Elephant Carpaccio](https://web.archive.org/web/20171001172011/http://alistair.cockburn.us/Elephant+Carpaccio), the [Elephant Carpaccio exercise](https://web.archive.org/web/20171114154855/http://alistair.cockburn.us/Elephant+Carpaccio+exercise), and [Laminating not slicing](https://web.archive.org/web/20170621090707/http://alistair.cockburn.us/Laminating+not+slicing)
- Henrik Kniberg's and Alistair Cockburn's [Elephant Carpaccio exercise Facilitation guide](https://docs.google.com/document/d/1TCuuu-8Mm14oxsOnlk8DqfZAA1cvtYu9WGv67Yj_sSk/pub)
- Oliver Spann's [experience report](https://medium.com/@olivercecilspann/elephant-carpaccio-exercise-an-experience-report-207f0cc79c34) of facilitating the exercise

These pages are also the ones I used to prepare my workshops. I ended up running the workshop twice, each time with 9 participants, both times remotely. In the rest of this blog post I will describe my experiences running the workshops, what changes I made between the first and second workshop, and how that played out.


## Preparation
To prepare facilitating the first workshop, I read the resources I shared above. I also did the exercise on my own: first slicing the application, then building it in Python. It's a shame  I did not keep track of time. Time management turned out to be an issue in both workshops, so knowing how much time I took to do the exericse on my own, would have helped. Another thing I did, is search for other people's solutions to the slicing. I found this [slide deck](https://elizabeth-mckellar-6gje.squarespace.com/s/Elephant-Carpaccio_november2017_chapter-presentation-wdm5.pdf) by Michael Wallace, which both confirmed what I had done and gave me some new ideas.

The most important part of my preparation was deciding how to adapt the exercise to a remote setting. The facilitation guide says the exercise takes 90-120 minutes, so I scheduled 2 hours - because doing this remote definitely would not be faster than doing it in person. To save some time I asked the participants to do a few things in advance: split up in pairs or trios, pick a programming language, and set up a development environment on at least one machine.

As for the workshop itself, I dropped the shouting of "slice!" whenever a team finishes developing a slice. With every group in their own breakout room shouting wouldn't really work; having participants post in a dedicated Slack channel felt like too much of a distraction. For the same reason, I did not ask groups to demo to one other group, but had them post a screenshot or gif on the workshop Miro board. Thirdly, to further reduce distraction,  I decided not to visit the breakout rooms during either the slicing or the implementation.


## The first workshop

The first workshop went well in many ways. I had a clear picture of the exercise and how should it go. My choice of tools (Zoom, Miro and Slack) worked well. However, two things did not go well and it was clear I would have to address those in the second workshop.

First of all, I ran out of time. I remember looking at the clock when we were about to start slicing and thinking "Where did the time go already?" So I cut short both the slicing and the developing in the hope of saving enough time for the review and the debrief. That turned out to be not good enough. I ended up skipping most of the review to have time for a minimal debrief.

Secondly, I kept myself too far from what the groups were doing. To avoid groups looking at each other's slices, I asked them to not put those on the shared Miro board. To avoid me being a distraction, I stayed in the main room while everyone was busy in the breakout rooms. This prevented me both from giving a group a nudge in the right direction if they needed it and it prevented me from gathering valuable input for the debrief.


## Changes to the plan for the second workshop

Because I ran out of time in the first workshop, I needed to cut something from the schedule. Cutting from the slicing, development, review or debrief would make the workshop worse, not better, so I had to cut from the introduction. Instead of having a 15 minute discussion on slicing, I asked the participants to add stickies to the Miro board before the workshop about why you'd want to slice small. We covered those stickies in a 5 minute discussion during the workshop. The 10 minutes I saved this way, I added to the slicing exercise.

Additionally, I changed my approach to the slicing exercise. In the first workshop I gave instructions, had the groups slice, got everyone back together to discuss, then had everyone do more slicing. I still think that can be a good aproach if you have enough time, but after the first workshop I knew I couldn't count on that. In the second workshop I gave instructions, then facilitated a discussion on what the first slice should be and on slicing techniques, and finally asked everyone to split into groups to do the actual slicing. This also helped to prevent groups from getting too far off track from defining good vertical slices.

The second change I wanted to make was to be more aware of what the groups were doing. So I asked the groups to do the slicing on the shared Miro board. And I hopped between the breakout rooms, after giving very clear instructions that it would be perfectly fine to ignore me if I showed up in a breakout room.


## The second workshop
Luckily, the changes I made resulted in a better workshop. Hopping between the breakout rooms allowed me to nudge participants in the right direction and to share some observations during the debrief. The discussion on slicing techniques helped the groups to come up with good vertical slices.

However, I still ran out of time. It wasn't as dramatic as during the first workshop, but I still would have liked some more time for the debrief. I did have a really good conversation with one of the participants right after the workshop about in which contexts feature slicing would work better or worse. And one participant mentioned they have started applying it immediately to a new initiative.

So while I had rather mixed feelings after the first workshop, I felt good after the second workshop - while also having some ideas of making a potential third one even better. I'll cover those ideas in the next two blog posts. One will contain some [more general thoughts on facilitating](link://slug/lessons-learned-after-facilitating-elephant-carpaccio) a remote experiential workshop. The [other one](link://slug/how-to-run-a-remote-elephant-carpaccio) will describe how I will run remote Elephant Carpaccio the next time I get the opportunity.


[^1]: I'm not sure when exactly. In October 2008 he published a blog post about the [concept](https://web.archive.org/web/20081017032508/http://alistair.cockburn.us/Elephant+Carpaccio) of Elephant Carpaccio.  And in February 2010 this blog post about the [exercise](https://web.archive.org/web/20140329203352/http://alistair.cockburn.us/Elephant+Carpaccio+exercise).
