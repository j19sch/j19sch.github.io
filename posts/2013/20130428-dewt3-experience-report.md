<!--
.. title: DEWT3 experience report
.. slug: dewt3-experience-report
.. date: 2013-04-28 15:32:02 UTC+02:00
.. tags: DEWT, peer conference, context-driven testing, systems thinking
.. category: conference
.. link: 
.. description:
.. type: text
-->

Last weekend the third Dutch Exploratory Workshop in Testing (DEWT3 for short) took place. The ingredients were: a very nice hotel in the woods, lots of talk about testing, beer, whiskey, a small to moderate amount of sleep, stickies and a group of fun and interesting people (You can see them [here](http://dewt.wordpress.com/2013/04/24/dewt3-experience-reports/).)

On Saturday the talks (and thus discussions) were about systems thinking. A few years ago I did read Jerry Weinberg's "An Introduction to General Systems Thinking" and although a very interesting read, w.r.t. to applying it to testing I never got further then: Software is (part of) a system, so you can apply systems thinking to it. Of course, that's very much true, but it's also quite a vague piece of advice.


## A primer on systems thinking

Enter James Bach, who kicked off DEWT3 with a primer on systems thinking. Systems thinking is just a way of thinking - just like logical thinking, analogical thinking, creative thinking, etc. - in which we approach a situation as being a system. So what's a system? It's a set of things in a meaningful interaction with each other.
This definition raises all sorts of questions relevant in systems thinking:

<!-- TEASER_END -->

- What's part of the set and what's not?
- What do we consider a thing?
- How are we going to name the things?
- What makes an interaction meaningful?
- What kind of interactions are there? Cause and effect? Feedback loops?
- Do these interactions result in a stable system or not?[^1]
- ...

So James's talk was great (at least to me) in demystifying the application of systems thinking. Just as with logical thinking, we all do it often enough, the real trick is being (or becoming) really good at it.


## Saturday

The remainder of the day was filled with discussion on the following four talks.

Rik Marselis talked about software development as a system. This brought us to the question: should we stop or should we start testing? The main point was that we do not want testing to happen in a ‘testing phase' that begins when everyone else thinks they're done. And such a phase should really be called the fixing phase, by the way.

Ruud Cox presented a stakeholder analysis he did for a project building an intelligent luminaire for parking garages. (A luminaire is like a lamp, only more so.) It became quite obvious that by applying systems thinking he managed to identify quite a few additional stakeholders, such as the people transporting the luminaire, the owner of the garage (different person than the one operating it), the people living across the street from the garage, etc.

Derk-Jan de Grood talked about mapping communication channels and fields of influence in an organisation. This lead to a great discussion about the pros and cons of spreading a rumor in an organisation as a kind of test. Evidently, we were able to identify some potential problems, so don't expect to see it on a list of best practices anytime soon.

James Bach talked about a model he and Anne-Marie Charrett are developing about coaching. Apart from being an interesting model as such, it was a bit shocking to see how a limited interaction (coaching) between just two people results in a system that's already quite complex. James also showed us several versions of the model, illustrating how difficult it is to identify the ‘things' in your system and how they interact.

Finally, Markus Gärtner did a short stickies tutorial. This was highly needed as the intuitive way of taking a sticky of a stack is wrong. It creates a curve in the sticky, which means that when you stick a sticky to something, there's a distance between the bottom of the sticky and what you stuck it on. Luckily there are not one, not two, but three ways to properly remove a sticky from the stack correctly. And perhaps there are even more, so to encourage further contributions to this most exciting field of research, I will leave the specifics of these correct methods as an exercise to the reader.

In the evening Markus proposed a Lean Beer session. (It's similar to Lean Coffee, only mental acuity goes down instead of up because of the consumption of beer instead of coffee.) So we had interesting discussions on a variety op topics, such as TMap, model-based testing, the OODA-loop and which books to read. I'm still slightly disappointed we never made it to the topic ‘grizzly bears', though.


## Sunday

On Sunday there were four more talks.

Michael Philips expressed his concern about a tendency in Agile to kill off all human testing and just do automated testing and continuous deployment. One of the reasons for this tendency is the idea that "testers can't keep up in Agile projects". Which is an excellent non-systems thinking way to approach it. As James Bach pointed out, creating code is creating risk. If "the testers are not keeping up", the problem is that your developers are out of control. They are creating more risk than the project as a whole can manage.

Joris Meerts did a talk on how do you know you're a good tester. This lead him to point our attention to a very important and often overlooked testing skill: reading. It rarely seems to pop up in lists of testing skills, yet when you are testing a document (i.e. reviewing) it seems to me to be kind of indispensable. Joris also pointed out that it's hard to find good material on reviewing skills and heuristics. Most seem to talk about the format (such as peer review, walkthrough, inspection) and not about what it is that you exactly do when you are reviewing a document. I hope to get back on this in a later blog post.

James Bach told the story about how a project in which the three other testers were fired and he was not (or rather: he was rehired after being fired). The reason: he had built up credibility within the project. He did not do this by being agreeable, but by doing his job to the best of his abilities, even when this meant arguing with the project manager. Basically he said: you hired me for my expertise, so have faith in my expertise (and by extension your earlier hiring decision) instead of telling me what to do.

Huib Schoots closed the day with a talk on recruiting testers. He stressed that to him the most important thing is personality and enthusiasm. These two things you can't teach; testing skills and (especially) domain knowledge you can.

And that was the end of the weekend. To close off I'd like to thank all the other attendees. Hope to see you again sometime soon!

---

*This post was originally published [here](https://testingcurve.wordpress.com/2013/04/28/dewt3-experience-report/).*

[^1]: Or as I am reading Nassim Nicholas Taleb's "Antifragile": a fragile, robust or antifragile system?