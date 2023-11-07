<!--
.. title: A good tester is all over the place
.. slug: a-good-tester-is-all-over-the-place
.. date: 2023-11-05
.. tags: quality engineering
.. category: quality engineering, management, software development, software testing, test management
.. link: 
.. description: 
.. type: text
-->

* --> Before I start this post, I shoud say that we use "tester" in [so many different ways](link://slug/tester-is-an-overloaded-variable), that there are so many different views about what good testing is, let alone what good software development looks like, that either I had to cut a lot of the nuance from this post, or I had to write an extremely long post with nuances stacked on top of nuances. I chose for the former approach.*

*--> Since I took on a job as quality engineer about six months ago, I've been thinking more about the different testing-related roles I've had in the past 15+ years. I've been a tester in a separate testing team, a tester in an Agile team while reporting to either a test manager or an engineering manager, a principal test engineer, and since recently a quality engineer.*

*-->Despite their differences, I've found they do have something in common: they're all problematic, or rather: unstable. They require a continuous balancing act, a never-ending re-invention of our jobs, adapting to the environment we find ourselves in. And I guess this partially explains why we keep coming up with new titles for what we do: quality assurance analyst, test engineer, software development engineer in test, quality engineer, etc. No solution to "the testing role" is stable. To be effective, we have no choice but to work as much around the existing structures as within them.*

<!-- TEASER_END -->

# Testers do testing

Let's start with a straightforward statement: a tester tests. Then what is testing? I [still like the definition](link://slug/reflections-on-my-testing-manifesto) *"Testing is investigating in order to evaluate a product."* The most obvious thing to investigate, to test, is the code that has been written[^1]. The best way to do this, in my opinion, is through the combination of exploratory testing and test automation, i.e. what [Maaret Pyhäjärvi](https://maaretp.com/) has named ["contemporary exploratory testing"](https://www.youtube.com/watch?v=T_67oQrPZhQ).

[^1]: Which can take different forms: from investigating the code as code, to investigating (part of) the code as it runs, to investigating the code as a product.

These two aspects, the exploratory and the automation activities, are the most visible parts. They would yield very poor results, though, without good strategy, planning, and design of the testing. And the results would of be of little use without good test reporting.

While the above covers the core of what a tester does, there's more testing to do. I expect testers to also be involved in monitoring production, in attending to CI/CD pipelines, and to participate in refinement, design, and architecture.[^4]

[^4]: And even that list is too short and generic, see [Maaret Pyhäjärvi](https://maaretp.com/)'s ["Testers roles and services"](https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html).

So that's quite a wide range of activities. Luckily, yet also unluckily, they are not the only ones doing testing.

So that's quite a wide range of activities. Luckily, they are not the only ones doing testing. Unluckily, this also creates some challenges.


## But they're not the only ones testing

A curious thing about testing, is that the tester is not the only one doing it.

I expect developers to test their own work. It cannot be the case that when you ask a developer "Is the code you wrote good enough?", the reply is "I have no clue, because that's not my job. Ask a tester to look at it." And as to the other set of activities I mentioned - monitoring, pipelines, design - it's hard to imagine developers not also being involved in those.

So it seems there's nothing that distinguishes a tester from a programmer in the types of activities they do. A cynical conclusion from that could be that testers are programmers who aren't good enough at programming. They get to be second-tier developers, focusing on stuff that needs to happen, but is not programming.

I don't accept that cynical conclusion, though. It's not because anyone can cook or anyone can write a book, that everyone's cooking or writing is equally good. The same applies to testing. I've seen plenty of testers bring great value to their team, because they bring something different.


## Yet they bring something different

As mentioned above, the unique value testers bring, is not in what they do. They should not be the only ones testing. The unique thing a tester (or at least a good tester) brings, is in how they do testing.

By being "a tester", they have the space to focus on testing. First of all, they can focus their professional development skills on this area. They can build and deepen their testing skills beyond a level that would make sense for non-testers.[^2] Secondly, throughout the development process, testers can take a testing stance. The can keep the question "How might this work? And how might it not?" front of mind, leaving the question "How can I build this?" more in the background.

[^2]: If you're not getting that from your testers, there's an interesting conversation to be had.

*--> That is not to say that all of that testing will be great or even adequate. Some of it will be too shallow, or poorly done, or the best you could get from someone who lacks certain skills, has a bad day, or isn't provided with an environment to support their best.*


# Please point at where the testing happens

All of this means, that it's hard to point in a meaningful way to where testing happens. There's no single activity in which all the testing is concentrated. There isn't a single role either. Testing - as in: investigating in order to evaluate a product - happens everywhere, all the time, by everyone.[^3]

[^3]: My favorite far-fetched example is a programmer's proprioception if they are hitting the right keys while writing code.

As such, testers needs to be all over the place, all over software development, because that's where testing happens. It's not only that, though. They also need to decide, situation-by-situation, where they want to stand on the following three axes:
- do testing themselves or support testing by others
- be embedded in a team or be part of a separate team
- do their job or improve the system

*--> And it is to say that testers both need to claim and not claim ownership of testing. -> doing vs support testing*
*--> they need to adjust their stance as they do so. As they engage with different parts of software development, they have to choose to*
*--> The different ~~stances~~ of a tester*

# Three axes to position yourself on --> 'position' is too static

While I'm most interested in the dynamic aspect of these axes, there is a static aspect too. The job you got hired to do, gives you a kind of 'neutral' position on these axes. For example, when I was a [quality engineer](link://slug/im-a-quality-engineer-and-im-not-sure-how-i-feel-about-that), I was expected to support testing by others, while embedded in two teams, and to do my job. To be effective though, I did have to do testing myself, team up with the other quality engineers, and improve the system. That dynamic, this continuous movement along these three axes, is in my opinion essential be effective as a tester.

*--> And this continuous movement is not a balancing act. It's not about finding a spot that's dynamically stable for each of these three axes. It's deciding - often multiple times a day - where to position yourself on those three axes, depending on the people you're working with, the activity you're engaging in, and the goal(s) of that activity.*

## Doing testing yourself versus supporting testing by others

Doing the testing means that you do testing and share the results of your testing. A big risk here is that you become the sole owner of the kind of testing you do. It's your domain and others leave it for you to do. Having a dedicated "testing" column on your board is one sign that this happening - at least to some degree.

Supporting testing by others means that you enable others to do testing. You talk with developers before they test, debrief with them after, and you pair test. The big challenge here is that by not doing any testing yourself, but only supporting others, it becomes very hard to build a deep understanding of the product and technology. And that limits how well you can support the testing. You want to be specific and concrete in your support, not only hand out generic testing wisdom.

The middle ground between doing and supporting is often called whole-team testing. As I said in a [previous blog post](link://slug/agile-tester-or-quality-engineer-whos-to-say):

>  Ironically, an important challenge for an agile tester is to not do too much testing.

> [...] the difference between an agile tester and a quality engineer becomes rather moot. In practice they will be doing very similar things: avoiding to become a quality safety blanket for the team, and working in a supportive and collaborative way with their team on quality.

However, it's not really a middle ground, a balancing act between two extremes. Rather, you need to continuously decide how much doing and how much supporting makes sense in that particular moment, for that particular activity, with those particial team members. And you can't leave your team members guessing about those decisions, so it requires an ongoing dialogue with them about what you do versus what you support.

This continuous movement and dialogue can get quite taxing for everyone involved.

*--> This ongoing dialogue and the changes that come with it, however, are quite taxing for the team. The team's way of working isn't a stable base to work from. It's in a constant state of flux, both potentially and in reality. Now, in a way this is an ideal scenario, with a team that keeps adapting and improving. However, often enough there are enough sources of instability and change around the team already and a team can only cope with so much of it.*


## Being embedded in a team versus being in a separate team
One of the many good things Agile has done, is pull testers into the development team. Instead of having the testers do their work only after the programmers are done writing all the code, they get to collaborate. Shorter feedback loops FTW!

Unfortunately, with agile teams being rightfully relatively small, this leaves the tester in a somewhat lonely spot. There's probably only one tester on the team. So you don't have any peers inside your team to run ideas by. As a more junior tester, you don't have a more senior tester in your team to learn from. Last but not least, your manager is more likely to have a programming than a testing background, so there's a limit to the kind of support and mentoring you can get from them.

Those disadvantages do not mean, however, that you should set up an org structure that separates development from testing. 

*-->, with all the unproductive incentives that comes with it. For more on the pitfalls of this setup, I recommend [Elisabeth Hendrickson](https://ruby.social/@testobsessed)'s [*"Better Testing, Worse Quality?"*](https://web.archive.org/web/20041001003124/http://www.qualitytree.com/feature/btwq.pdf). One thing that becomes very clear from it, is that even if you have a well-functioning setup with an independent test team, the managing of quality needs to happen on a higher level. It needs to cover requirements analysis and developer and independent testing and defect prevention.*

*-->Even when you manage to avoid those pitfalls, having two separate teams will create some amount of siloisation, so more friction in hand-overs, less collaboration, and the transfer of problems to the other team.*

The solution here is to have on the one hand a cross-functional team, all reporting to the same manager, who is responsible for the results of the team, and on the other hand, create incentives and structures for the testers to connect with one another. That structure can be a test guild, a community of practice, a [regular ensembling session](https://ezagroba.github.io/mob-testing/#/), or just an informal catchup meeting every week.

*--> The advantage of getting the testers to connect with each other goes beyond them feeling they have a group of peers within the company. A good tester looks at a bigger picture, beyond the scope and focus of their team. They can do this a lot more effectively if they're sharing information with each other. This then becomes a basis for collaborating with each other, whenever that's useful. And if you're lucky, they'll bring their team along with them. So in this way testers become important in linking teams together and creating aligninment on what they deliver.*


## Doing your job versus improving the system
It’s important to do your job, but to do a good job you discover you first have to change the organization a little (or a lot).

### Doing your job

As a tester your job is to test things. To uncover interesting information about the product.  Ideally you do this throughout the software development lifecycle: from ideation to production. Ideally you have access to the code and to the necessary tools. Ideally your other team members are involved in testing and ideally they involve you in what they are doing.

Unfortunately, things very often aren't ideal. It could be that you're testing code written by a third party based on the specs written by a business analyst. So doing your job, means you do your best with whatever's given to you. Even if that means your testing is a lot less effective than it could be (should be?).

### Improving the system

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

diagram with Maaret
> From an observation of how much "manager" kind of work agile team's testers have been taking without the manager power
https://www.linkedin.com/feed/update/urn:li:activity:7021181214204080128/

Quoting Anna Baik: "As testers, we are often expected to not only do our work, but fix our organizations to be able to do so."  
https://www.linkedin.com/posts/maaret_testers-activity-7033160980041719808-ZFAj


Maaike's 4 levels
https://twitter.com/Maaikees/status/1617816571786977280



# Working inside and outside existing structures
So even though your official job description puts you clearly on one end of each axis - for example my quality engineering role was supporting testing by others, being embedded in a team, and doing my job -, you can only make that work by constantly observing and adjusting your actual position on these three axes. You need to work as much inside the existing structures, as around them. That makes these roles challenging and interesting, but often enough also frustrating. And yet, I wouldn’t want it any other way.

discover gaps and decide which to fill, be like water and like ice

whatever structure is in place, you have to work around it -> workflowy note
	and thus you change it

Again, not about unfairness of having to adapt. About unfairness of not having a clear, stable base.

Not a lamentation. Also makes the work interesting. (check my privilege though)

Hence, fundamental problem, "just keep adapting" is not a solution.

I don't have a solution. I have some more thoughts on related aspects.

The too big solution: stop outsourcing a large chunk of quality to specific roles (inc Head of Quality). Or stop doing that, while separating people. Sports teams and infantry squads don't. Or sports teams have a goalie, team member yet different. Specialization is needed. We say we want to build quality in, but we keep separating out building from testing. Big gap in paradigms / communities / ... between devs and testers.
Quality does not work that way (oursourcing). It's emergent. So it should be throughout your management chain.
Since that won't happen anytime soon, I'll keep my job and the challenge.




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

programmer who 'just' happens not to specialize in testing.


# questions for the reader

Can you relate to this balancing act? Do you move more across some dimensions than others? Do you move across different ones? Would making your balancing act(s) explicit improve your collaboration with others?


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

