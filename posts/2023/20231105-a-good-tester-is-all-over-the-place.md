<!--
.. title: A good tester is all over the place
.. slug: a-good-tester-is-all-over-the-place
.. date: 2023-11-25
.. tags: quality engineering
.. category: quality engineering, management, software development, software testing, test management
.. link: 
.. description: 
.. type: text
-->

Posts I kind of want to link to:
- [agile tester or quality engineer](link://slug/agile-tester-or-quality-engineer-whos-to-say)
- [tester as overload variable](link://slug/tester-is-an-overloaded-variable) -> done


---

This post has become quite a long reflection on testers and testing-related roles, such as quality engineers. And each section could have been its own post, each as long as this one, with more details and nuance. I guess it just proves the point of my conclusion: testing-related roles are still an unsolved problem in software development. In the mean time, anyone in such a role will have to "be all over the place", in a good way.

intro should say something about working inside and outside (around) existing structures

```
--> Before I start this post, I shoud say that we use "tester" in [so many different ways](link://slug/tester-is-an-overloaded-variable), that there are so many different views about what good testing is, let alone what good software development looks like, that either I had to cut a lot of the nuance from this post, or I had to write an extremely long post with nuances stacked on top of nuances. I chose for the former approach.*

--> Since I took on a job as quality engineer about six months ago, I've been thinking more about the different testing-related roles I've had in the past 15+ years. I've been a tester in a separate testing team, a tester in an Agile team while reporting to either a test manager or an engineering manager, a principal test engineer, and since recently a quality engineer.*
```

<!-- TEASER_END -->

# Testers do testing

Let's start with a straightforward statement: a tester tests. Then what is testing? I [still like](link://slug/reflections-on-my-testing-manifesto) the definition *"Testing is investigating in order to evaluate a product."* The most obvious thing to investigate, to test, is the code that is being written. The best way to do this, in my opinion, is through the combination of exploratory testing and test automation, i.e. what [Maaret Pyhäjärvi](https://maaretp.com/) has named "[contemporary exploratory testing](https://www.youtube.com/watch?v=T_67oQrPZhQ)". And to be clear, while the execution part tends to be the most visible, effective testing also needs good test strategy, design, and reporting.

```
[^1]: Which can take different forms: from investigating the code as code, to investigating (part of) the code as it runs, to investigating the code as a product.
```

There's more to do as a tester, though, than testing the code that is being written. Testers should also be involved in monitoring production, in attending to CI/CD pipelines, in maintaining test data and test environments. And they should participate in refinement, design, and architecture.[^2]

[^2]: And even that list is too short and generic, see [Maaret Pyhäjärvi](https://maaretp.com/)'s ["Testers roles and services"](https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html).

So that's quite a wide range of activities, even when I leave out activities related to being a member of the development team (e.g. retropsectives) and to being an employee (e.g. all-hands meetings). Luckily, testers are not the only ones doing testing. Unluckily, this also creates some challenges.


## But they're not the only ones testing

Other roles - programmers is the clearest example - seem to have a good overlap of what their focus is (programming) and what their domain is (only we do the programming). A curious thing about testing is, that that's very much not the case. Testers are not the only ones doing testing.

Developers should test their own work. It cannot be the case that when you ask a developer *"Is the code you wrote good enough?"*, the reply is *"I have no clue, that's not my job. Ask a tester."* And the same applies to the other testing-related activities I mentioned - monitoring, pipelines, design - it's hard to imagine developers not being involved in those.

So based on a high-level list of activities, there doesn't seem to be anything that distinguishes a tester from a programmer. This raises an important question for any tester:

```
- if you do everything a programmer does, except for programming, what added value do you bring?
- how do as a tester bring more value than the average developer?
- how your testing brings more value than the average developer's?
```

A cynical conclusion from that could be that testers are programmers who aren't good enough at programming. So they get to be second-tier developers, focusing on the stuff that needs to happen, but that is not programming and that the programmers shouldn't be bothered with.

I don't accept that cynical conclusion. Testers bring great value to their teams, because they don't have to focus on the programming. It allows them to bring something different.

```
It's not because anyone can cook, that all cooking is equal. Cooking skills, like testing skills, vary widely across and within professions.
```

## Yet they bring something different

The unique thing a tester brings, is not in the fact that they do testing. Others should be testing too. It's that they bring something different to that testing.

```
It is in how they perform that testing.
```

By being "a tester", they have the space to focus on testing. First of all, they can focus their professional development skills on this area. They can build and deepen their testing skills beyond a level that would make sense for non-testers. Secondly, throughout the development process, testers can take a testing perspective. They can keep the question *"How might this work? And how might it not?"* front of mind, leaving the question *"How can I build this?"* more in the background and to the other team members.

To be very clear, "being a tester" doesn't have to be a long-term role. You can have a team of programmers, where each sprint one team member takes the tester-role for that sprint. What you lose in having a dedicated specialist, you gain in raising the skill level of all team members.

```
[^2]: If you're not getting that from your testers, there's an interesting conversation to be had.

*--> That is not to say that all of that testing will be great or even adequate. Some of it will be too shallow, or poorly done, or the best you could get from someone who lacks certain skills, has a bad day, or isn't provided with an environment to support their best.*
```

## Please point at where the testing happens

All of this means, that it's hard to point in a meaningful way to where testing happens. There's no single activity in which all the testing is concentrated. There isn't a single role either. Testing - investigating in order to evaluate a product - happens everywhere, all the time, by everyone.[^4]

[^4]: My favorite far-fetched example is a programmer's proprioception telling them if they are hitting the right keys while writing code.

As such, testers needs to be all over the place, all over software development, because that's where testing happens. There's more to it than that, though.

```

As such, testers needs to be all over the place, all over software development, because that's where testing happens. It's not only that, though. They also need to decide, situation-by-situation, where they want to stand on the following three axes:
- do testing themselves or support testing by others
- be embedded in a team or be part of a separate team
- do their job or improve the system

*--> And it is to say that testers both need to claim and not claim ownership of testing. -> doing vs support testing*
*--> they need to adjust their stance as they do so. As they engage with different parts of software development, they have to choose to*
*--> The different ~~stances~~ of a tester*

```

# Three axes to move around on

Next to being active all across the software development process, testers also need to decide, situation-by-situation, where they want to stand on three different axes:

- do testing yourself or support testing by others
- be embedded in a team or be part of a separate team
- do your job or improve the system

While I'll be focusing in this post on the dynamic aspect of these axes, there is a static aspect to them. The job you got hired to do, gives you a kind of 'neutral' position on these axes. For example, when I was a [quality engineer](link://slug/im-a-quality-engineer-and-im-not-sure-how-i-feel-about-that), I was expected to support testing by others, while embedded in two teams, and to do my job. To be effective though, I did have to do testing myself, team up with the other quality engineers, and improve the system. That dynamic, this continuous movement along these three axes, is in my experience essential to be effective as a tester.

```
--> And this continuous movement is not a balancing act. It's not about finding a spot that's dynamically stable for each of these three axes. It's deciding - often multiple times a day - where to position yourself on those three axes, depending on the people you're working with, the activity you're engaging in, and the goal(s) of that activity.*
```

## Doing testing yourself versus supporting testing by others

Doing testing yourself means that you do testing and share the results of your testing. A big risk here is that you become the sole owner of the kind of testing you do. It's your domain and others leave it for you to do. Having a dedicated "testing" column on your board is one sign that this happening - at least to some degree.

Supporting testing by others means that you enable others to do testing. You talk with developers before they test, debrief with them after, and you test in a pair and/or ensemble. The big challenge here is that by not doing any testing yourself, but only supporting others, it becomes very hard to build a deep understanding of the product and technology. And that limits how well you can support the testing. You want to be specific and concrete in your support, not only hand out generic testing wisdom.

The middle ground between doing and supporting is often called whole-team testing. However, it's not really a middle ground, a balancing act between two extremes. Rather, you need to continuously decide how much doing and how much supporting makes sense in that particular moment, for that particular activity, with those particial team members. And you can't leave your team members guessing about those decisions, so it requires an ongoing dialogue with them about what you do versus what you support.

```
*--> As I said in a [previous blog post](link://slug/agile-tester-or-quality-engineer-whos-to-say):
 Ironically, an important challenge for an agile tester is to not do too much testing.
[...] the difference between an agile tester and a quality engineer becomes rather moot. In practice they will be doing very similar things: avoiding to become a quality safety blanket for the team, and working in a supportive and collaborative way with their team on quality.*

*--> This continuous movement and dialogue can get quite taxing for everyone involved.*

*--> This ongoing dialogue and the changes that come with it, however, are quite taxing for the team. The team's way of working isn't a stable base to work from. It's in a constant state of flux, both potentially and in reality. Now, in a way this is an ideal scenario, with a team that keeps adapting and improving. However, often enough there are enough sources of instability and change around the team already and a team can only cope with so much of it.*
```

## Being embedded in a team versus being in a separate team
One of the many good things Agile has done, is pull testers into the development team. Instead of having the testers do their work only after the programmers are done writing their code, they get to collaborate. Shorter feedback loops FTW!

Unfortunately, with agile teams being relatively small (as they should), this leaves the tester in a somewhat lonely spot. There's probably only one tester on the team. So you don't have peers inside your team to run ideas by. As a junior tester, you don't have a more experienced tester to learn from. And your manager is more likely to have a programming than a testing background, so there's a limit to the kind of support and mentoring you can get from them.

```
*--> Those disadvantages do not mean, however, that you should set up an org structure that separates development from testing.*

*-->, with all the unproductive incentives that comes with it. For more on the pitfalls of this setup, I recommend [Elisabeth Hendrickson](https://ruby.social/@testobsessed)'s [*"Better Testing, Worse Quality?"*](https://web.archive.org/web/20041001003124/http://www.qualitytree.com/feature/btwq.pdf). One thing that becomes very clear from it, is that even if you have a well-functioning setup with an independent test team, the managing of quality needs to happen on a higher level. It needs to cover requirements analysis and developer and independent testing and defect prevention.*

*-->Even when you manage to avoid those pitfalls, having two separate teams will create some amount of siloisation, so more friction in hand-overs, less collaboration, and the transfer of problems to the other team.*
```

Those disadvantages do not mean, however, that we should return to org structures that separate programming from testing. The solution is to have on the one hand a cross-functional team, all reporting to the same manager, who is responsible for the results of the team, and on the other hand, create incentives and structures for the testers to connect with one another. That structure can be a test guild, a community of practice, a [regular ensembling session](https://ezagroba.github.io/mob-testing/#/), or just an informal catchup meeting every week.

*--> The advantage of getting the testers to connect with each other goes beyond them feeling they have a group of peers within the company. A good tester looks at a bigger picture, beyond the scope and focus of their team. They can do this a lot more effectively if they're sharing information with each other. This then becomes a basis for collaborating with each other, whenever that's useful. And if you're lucky, they'll bring their team along with them. So in this way testers become important in linking teams together and creating aligninment on what they deliver.*


## Doing your job versus improving the system

```
*--> It’s important to do your job, but to do a good job you discover you first have to change the organization a little (or a lot).*
```

As a tester your job is to test things. To uncover interesting information about the product.  Ideally you do this throughout the software development lifecycle: from ideation to production. Ideally you have access to the code and to the necessary tools. Ideally your other team members are involved in testing and ideally they involve you in what they are doing.

Unfortunately, things very often aren't ideal. And sometimes they are very far from it. Doing your job then means doing your best with whatever is available to you. Even if that means your testing is a lot less effective than it could be.

Things not being ideal is also an opportunity for change. You can try to improve the system. On some level that's expected of any team member. 

Testers, however, often seem to need to do more than that. Few organizations are set up in a way that enables good testing. Changing that is more of a manager's job, though.[^5] As a tester, without a manager's authority and without a manager's access to higher management, getting things to change will be a challenge at best and an impossible task at worst.

[^5]: [Maaret Pyhäjärvi](https://maaretp.com/) and I made an [incomplete model](https://www.linkedin.com/feed/update/urn:li:activity:7021181214204080128/) about this a year ago.

This makes this axis the hardest of the three. If you try to change the system too little, you'll struggle to do a good job testing. Try to change the system too much, you get hit by blowback and resistance. Both are demotivating and can have you heading towards a burn-out.

It's better to work in more suble ways, picking the right opportunities to improve the system. That work, however, the work you do just so you can do good testing, often remains invisible. Most people don't have an eye for it. And even if someone does, the testing work you do, will remain a more visible than your testing-enabling work.


# A good tester is all over the place

A good tester is all over the place. Roles and processes provide structure, a starting point. You can't limit yourself to those though. Testing happens across roles, throughout the software development process. So you also need to be comfortable working oustide (and around) that structure. Testing happens everywhere all the time, so that's where a tester needs to be.

That brings us to the three axes. You can't be everywhere at once. You need to make choices. Is this testing something you need to do or something you only need to support? Are you sufficiently connected to your team and to your fellow testers? Is it time to get some work done or is it time to work on the system?

As a tester, you need to find where the gaps are and decide which to fill. Or to use a metaphor: you need to be like water, flowing around the rocks, but also know when to become solid like ice. (And very rarely, you get to be the water that creeps into the cracks of a rock, turns to ice, and shatters it from within.)

And this is not just true for testers. All of the testing and testing-related roles I've had the past decade, were unstable to some degree. They required me to adapt, to keep re-inventing what my job was. I guess this partially explains why we keep coming up with new titles for what we do: quality assurance analyst, test engineer, software development engineer in test, quality engineer, etc. As an industry, we're just not sure what exactly to do with testing. None of the solutions seem to be very stable.


# Do we have to be, though?

If no solution to "the testing role" is stable, I want to start with a hat tip to everyone, testers and non-testers, who do their best to make it work regardless. Because I do believe that it's an of the bigger unsolved problems in our industry.

I wish I had at least a clear direction for a solution. I'm afraid the best I can do is identifying three elements that I think should be part of the solution.

## Activities instead of roles

Roles, like "developer" and "tester", have value to HR. While I can imagine different solutions to the problems that roles solve for HR, those are not going to be easy to implement. So let's keep roles, but leave them to HR.

```
Roles are for HR. While I can imagine different solutions to the problems that roles solve for HR, those are not going to be easy to implement.

So let's keep roles, but leave them to HR.
```

At a team-level, those roles are incredibly limiting and thus damaging. People with all their richness of skills, knowledge, and experience, are reduced to "developer", "tester", "ux designer", etc. And we pretend that single label covers what they do: developing, testing, designing, etc.

This [confusion](link://slug/tester-is-an-overloaded-variable) of people, roles, and process steps means we rarely talk about what we do in a smart way. What are the different activities that need doing? What perspectives are needed for those activities? Who on our team can contribute?

```
- problem of specialization
- gap between devs and testers
- why do we have different kinds of developers, each with their specialization, but tester isn't a developer (because they don't program and historical reasons and ...)

## Smarter ways to talk about what needs doing
- we need smarter ways to talk about what needs doing
	- e.g. test automation in CI/CD context vs automate the manual stuff
```


## Building bridges between communities

Testers are the most adjacent to programmers, without being programmers. And yet, there are very few bridges between the communities. A tester at a developer conference and a developer at a tester conference will feel the same way: as the odd one out.[^7] While both communities need spaces where they can have deep conversations about their specializations, we also need spaces where these communities come together. And more than just those two communities. Business analysts, scrum masters, product owners, SREs, engineering managers, etc. Where is the space where we all together can have a conversation about software development?

[^7]: One of the goals of [FroGS conf](https://frogsconf.nl/), an open space conference I co-organize, is to be such a bridge.


## Knowing what can be dreamt of

Some things you need to experience to know that they're possible. Or if that's not an option, you need to hear the stories of that that have experienced that thing. Before you can dream, you need to know what you can dream of. You need to know how big your dreams can be - and how wild.


---

How are you looking at your current role? Can you relate to the three axes?

Can you relate to this balancing act? Do you move more across some dimensions than others? Do you move across different ones? Would making your balancing act(s) explicit improve your collaboration with others?



---

---


---

# Working inside and outside existing structures

The main thing these three axes share, is that each requires you to work both inside and outside the existing structures. Your job description, your place in the org chart, the existing processes, those will put you somewhere on each of the three axes. And you will have to do the work matching those positions, to be successful. But more likely than not, that won't be enough. You'll have to move to other positions on those axes, working outside the existing structures.

-> a good tester is all over the place: whole SDLC and three axes





So even though your official job description puts you clearly on one end of each axis - for example my quality engineering role was supporting testing by others, being embedded in a team, and doing my job -, you can only make that work by constantly observing and adjusting your actual position on these three axes. You need to work as much inside the existing structures, as around them. That makes these roles challenging and interesting, but often enough also frustrating. And yet, I wouldn’t want it any other way.

whatever structure is in place, you have to work around it -> workflowy note
	and thus you change it

Again, not about unfairness of having to adapt. About unfairness of not having a clear, stable base.

Not a lamentation. Also makes the work interesting. (check my privilege though)

Hence, fundamental problem, "just keep adapting" is not a solution.

I don't have a solution. I have some more thoughts on related aspects.


*--> This continuous movement and dialogue can get quite taxing for everyone involved.*

---


# questions for the reader

How are you looking at your current role? Can you relate to the three axes?

Can you relate to this balancing act? Do you move more across some dimensions than others? Do you move across different ones? Would making your balancing act(s) explicit improve your collaboration with others?

---

# So what to do?
- ways to look at the three axes
	- screwed if always/mostly on either side; screwed if you do screwed if you don't
	- means to evaluate what you are doing, what is needed of you
	- explain the struggle, the burnouts, etc
		- https://www.simplermachines.com/work-is-trying-to-own-your-soul/
		- Burnout is common in tech because...
			- https://twitter.com/nota_bennett/status/1400116552024793095
		- we build invisible stuff for people we never meet.
			- https://twitter.com/j19sch/status/1400204677447364614
- we need smarter ways to talk about what we do
	- Maaret's overview
	- no test engineers, no scrum masters
	- roles are for HR -> my post about tester as overloaded variable
- we need smarter ways to talk about what needs doing
	- testing: automated or manual/exploratory
	- what about refinement? what about monitoring and analytics? stategy? deciding what's important? where to focus?

The too big solution: stop outsourcing a large chunk of quality to specific roles (inc Head of Quality). Or stop doing that, while separating people. Sports teams and infantry squads don't. Or sports teams have a goalie, team member yet different. Specialization is needed. We say we want to build quality in, but we keep separating out building from testing. Big gap in paradigms / communities / ... between devs and testers.
Quality does not work that way (oursourcing). It's emergent. So it should be throughout your management chain.
Since that won't happen anytime soon, I'll keep my job and the challenge.


# what does this mean for the role of tester?

position of testers is an unsolved problem in the industry
hat tip to everyone, testers and non-testers, who make it work regardless

personnaly changed my perception of myself
one way to look at myself is: tester
the other: developer who doesn't specialize in programming
claiming my place as a developer who doesn't specialize in programming
does require showing results / impact

I'm a developer who doesn't specialize in programming
I'm a developer who 'just' happens not to specialize in programming

unsolved problem in software development

programmer who 'just' happens not to specialize in testing. BUT still also proud to call themselves tester



---

# what testers do

testing throughout the sw dev cycle
uniqueness is not in what testers do, but in their expertise / skill-level
	refinement, exploratory testing, test automation, monitoring
	next to skill, also critical mindset, critical distance => allowed to focus on "investigating in order to evaluate"

Programmers write code, business analyists gather requirements, product owners set priorities, ux designers design. Others might help out here and there, but it's clear who's in the lead. Yet, when you ask: "Who tests?" The answer should be: "Hopefully not just the tester!"

uniqueness is not in what testers do, but in their expertise / skill-level
	next to skill, also critical mindset, critical distance => allowed to focus on "investigating in order to evaluate"

# three balancing acts, not balancing act, continuous movement

doing testing yourself versus supporting testing by others
being embedded in a team vs being in a separate team
doing your job versus improving the system

continuously moving


---


# Testers do testing

## But they're not the only ones

But a tester can also do testing by looking at monitoring, attending to CI/CD pipelines, participating in refinement. And that still leaves out some crucial acitivities, such as test strategy and test reporting. And the things we expect from every team member, e.g. participate in the retrospective.

Testers roles and services: https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html

What's curious about testing, though, is that the tester is not the only one doing it. Programmers write code, business analyists gather requirements, product owners set priorities, ux designers design. Others might help out here and there, but it's clear who's in the lead. Yet, when you ask: "Who tests?" The answer should be: "Hopefully not just the tester!"

# A tester's role is dynamic along three axes

link to [quality engineer experience report](link://slug/im-a-quality-engineer-and-im-not-sure-how-i-feel-about-that)

Maaret: be like water, but sometimes be ice

## Doing testing yourself versus supporting testing by others

## Being in a separate team versus being embedded in a team

## Doing your job versus improving the system

## Working inside and outside of the existing structures

What all of these have in common: working inside and outside of the existing structures

---



## Improving the system

If things aren't ideal, you can try to change them.
- enabling your job
	- that's a manager's job! (every team member's job up to a point)
	- only so much you can do from a tester's position

### The balancing act

- doing your job
	- either you accept a very limited not-my-problem attitude or you burn out -> burn-out post
- enabling your job
	- influence, no authority
	- not undermine others' authority
	- too distant from other managers / upper management limits impact
- the middle ground
	- all the glue work
	- all the admin work
	- appreciated, but not really seen, not really rewarded, accepted as the default(?)
	- ...
- bonus value delivered by testers
	- fixing the organization so they can do good testing

diagram with Maaret: really good one!
> From an observation of how much "manager" kind of work agile team's testers have been taking without the manager power
https://www.linkedin.com/feed/update/urn:li:activity:7021181214204080128/

Quoting Anna Baik: "As testers, we are often expected to not only do our work, but fix our organizations to be able to do so."  
https://www.linkedin.com/posts/maaret_testers-activity-7033160980041719808-ZFAj


Maaike's 4 levels: 1-3 team; 4 organisation
https://twitter.com/Maaikees/status/1617816571786977280