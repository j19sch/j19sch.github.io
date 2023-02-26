<!--
.. title: The three axes of trouble in testing roles
.. slug: the-three-axes-of-trouble-in-tesing-roles
.. date: 2023-02-25 13:01:25 UTC+01:00
.. tags: quality engineering
.. category: quality engineering, management, software development, software testing, test management
.. link: 
.. description: 
.. type: text
-->

Since I took on a job as quality engineer about six months ago, I've been thinking more about the different testing-related roles I've had in the past 15+ years. I've been a tester in a separate testing team, a tester in an Agile team while reporting to either a test manager or an engineering manager, a principal test engineer, and since recently a quality engineer.

Despite their differences, I've found they do have something in common: they're all problematic, or rather: unstable. They require a continuous balancing act, a never-ending re-invention of our jobs, adapting to the environment we find ourselves in. And I guess this partially explains why we keep coming up with new titles for what we do: quality assurance analyst, test engineer, software development engineer in test, quality engineer, etc. No solution to "the testing role" is stable. To be effective, we have no choice but to work as much around the existing structures as within them.

<!-- TEASER_END -->

# The three axes of trouble

The trouble with this balancing act of any testing-related role, is that it takes place on three different axes:

- doing testing versus supporting testing
- being embedded versus being in a separate team
- doing your job versus enabling your job

To be clear: I have no problem with expecting some adaptability and flexibility from team members. The best teams I've worked on where dynamic in this way, with people covering gaps where needed.

What I do have a problem with is having to do this across three different axes. Especially if - as we shall see - there rarely (if ever) is a long-term stable position on any of the three axes. At that point we have to start asking the question if there isn't some more fundamental problem with testing-related roles.


# post 1: Doing the testing vs. supporting the testing

## Doing the testing
Doing the testing means that you test the product and share the results of that testing. There's a clear step in the process where you do testing - or rather the testing testers do, as opposed to the testing programmers do. This leads to all kinds of problems related to silos, handovers[^2] and bottlenecks.

[^2]: How often have you seen a developer do a good handover of the testing they have done already?

This is the default mode for waterfall, but plenty of Agile teams operate in a similar way. The only difference is that waterfall does this on a project-level and these Agile teams do it on a story-level.

You might be involved in things like refinement or story huddles to bring in "your unique perspective as a tester". So there too, you're doing testing.

## Supporting the testing
Supporting the testing means that you support and enable others (i.e. the developers) to test their own and each other's work. So you're not directly contributing and in that sense not a full member of the team. That also means that you're optional to the work, unless there's a strong culture of valuing your role of supporting testing.

A major challenge is that if you support the testing, but rarely do the testing, it will be very hard to build a deep understanding of the product and technology. And this limits how well you will be able to support the testing. You may end up as the scrum master who knows how to facilitate the scrum events, but has barely any idea of what the team actually builds. At that point, someone might rightfully raise the question why they keep you around at all.

## The balancing act
The middle ground between doing and supporting is often called whole-team testing. As I said in a [previous blog post](link://slug/agile-tester-or-quality-engineer-whos-to-say):

>  Ironically, an important challenge for an agile tester is to not do too much testing.

> [...] the difference between an agile tester and a quality engineer becomes rather moot. In practice they will be doing very similar things: avoiding to become a quality safety blanket for the team, and working in a supportive and collaborative way with their team on quality.

However, it's not really a middle ground, a stable base between two extremes. This position is a balancing act, where the middle ground keeps moving and you have to adjust to it. It requires an ongoing dialogue with your team about what you do versus what you support[^1] - with the assumption that some of what you do, will grow to something you support. At which point you might add something new to what you do, convince the team of its value, and then the cycle repeats itself. Luckily, there's some stuff developers never seem to take over and there's always more stuff you could do, so you won't make yourself obsolete.

[^1]: It also requires on ongoing dialogue about what they do and what you do. See [Maaret Pyhäjärvi](https://maaretp.com/)'s blog post [*"Tester roles and services"*](https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html) for an excellent example of such a dialogue.

This ongoing dialogue and the changes that come with it, however, are quite taxing for the team. The team's way of working isn't a stable base to work from. It's in a constant state of flux, both potentially and in reality. Now, in a way this is an ideal scenario, with a team that keeps adapting and improving. However, often enough there are enough sources of instability and change around the team already and a team can only cope with so much of it.

---

# post 2: Being embedded in a team as a tester versus being in a separate testing team

## Being embedded in a team

## Being in a separate team

## The balancing act

### Places along the axis

- in the team, same manager
- in the team, different manager
- in the team, but CoP and/or test guild
- separate testing team


### Why none of them are stable

- embedded
	- lonely, only tester
	- limited manager support, because manager is unlikely to be a former tester
		- the work
		- career progression
		- personal development
- 'middleground'
	- what problems are easiest to absorb
	- "one of us"-feeling with testers in other teams
	- testers creating additional lines of communication to counter isolation
		- to counter team-only focus -> bigger picture
- separate team
	- silo, makes collaboration hard, hand-overs
- bonus value delivered by testers
	- additional networks, more connected, extra flows of information
	- bigger picture view

---

lonely as only tester in a team, or quality engineer
connect with other testers / quality engineers

separate team: silos, hand-overs, etc
BAs, Devs, Testers each with their own manager, project manager for the team

---

# post 3: Doing your job as a tester versus enabling your job

## Doing your job

## Enabling your job (needs better word then enabling)

### Places along the axis

- doing your job
	- just test the story
	- sucks, very hard
		- 3rd party developers based on specs and me having to test
	- work with whatever's given, even if it means poor ineffective testing
- enabling your job
	- that's a manager's job! (every team member's job up to a point)
	- only so much you can do from a tester's position


### Why none of them are stable
- doing your job
	- either you accept a very limited not-my-problem attitude or you burn out
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

---

working -> environment sucks
improving -> management
but also: filling the gaps, doing glue work, so compensating for holes in the org, process, etc

management stuff

diagram with Maaret
> From an observation of how much "manager" kind of work agile team's testers have been taking without the manager power
https://www.linkedin.com/feed/update/urn:li:activity:7021181214204080128/

Quoting Anna Baik: "As testers, we are often expected to not only do our work, but fix our organizations to be able to do so."  
https://www.linkedin.com/posts/maaret_testers-activity-7033160980041719808-ZFAj


Maaike's 4 levels
https://twitter.com/Maaikees/status/1617816571786977280


---

# post 4: So where does that leave us?

whatever structure is in place, you have to work around it -> workflowy note
	and thus you change it

Again, not about unfairness of having to adapt. About unfairness of not having a clear, stable base.

Not a lamentation. Also makes the work interesting. (check my privilege though)

Hence, fundamental problem, "just keep adapting" is not a solution.

I don't have a solution. I have some more thoughts on related aspects.

The too big solution: stop outsourcing a large chunk of quality to specific roles (inc Head of Quality). Or stop doing that, while separating people. Sports teams and infantry squads don't. Or sports teams have a goalie, team member yet different. Specialization is needed. We say we want to build quality in, but we keep separating out building from testing. Big gap in paradigms / communities / ... between devs and testers.
Quality does not work that way (oursourcing). It's emergent. So it should be throughout your management chain.
Since that won't happen anytime soon, I'll keep my job and the challenge.
