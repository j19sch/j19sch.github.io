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

Despite their differences, I've found they do have something in common: they're all problematic, or rather: unstable. They require a contiuous balancing act, a never-ending re-invention of our jobs, adapting to the situations we find ourselves in. And I guess this partially explains why we keep coming up with new titles for what we do: quality assurance analyst, test engineer, software development engineer in test, quality engineer, etc. No solution to "the testing role" is stable.

<!-- TEASER_END -->

# The three axes of trouble

The trouble with this balancing act of any tester role, is that it takes place on three different axes:

- doing testing versus supporting testing
- being embedded versus being in a separate team
- doing jour job versus enabling your job

To be clear: I have no problem with expecting some adaptability and flexibility from team members. The best teams I've worked on where dynamic in this way, with people covering gaps where needed.

What I do have a problem with is having to do this across three different axes. Especially if - as we shall see - there rarely (if ever) is a long-term stable position on any of the three axes. At that point we have to start asking the question if there isn't some more fundamental problem with testing-related roles.


## Doing testing versus supporting testing

### Places along the axis

- doing the testing
	- separate "testing" column
	- tester for the team
- whole-team testing
	- tester of the team
- support only
	- quality engineer



### Why none of them are stable
- doing the testing
	- bottleneck, dependency on tester
	- dev testing vs tester testing, separated, not even a handover (except automation)
- doing and supporting
	- moving targets
	- some stuff: doing -> supporting
	- other stuff: only tester will do; demonstrate the need/value of it
	- Maaret's 15 hats
		- each hat: never, sometimes, focus
		- https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html
	- risks:
		- doing too much
		- doing too little
		- only supporting, nothing left to do, value is questioned
	- ongoing conversations: where to do, where to support
- supporting the testing
	- not really part of the team, not really contributing
	- supporting needs domain knowledge, so needs doing testing
	- danger similar to scrum master who only facilitates scrum events, can't contribute
- bonus value delivered by testers
	- doing testing and teaching others to test

---

the testing that devs do versus the testing testers do -> weird
no the case for BA, UX, etc

doing -> bottleneck
supporting -> too distant, not contributing, lack of domain knowledge, scrum master who only knows how to facilitateq

> “Having a tester for the team” means there is someone responsible for the work labeled as “testing”.
> “Having a tester of the team” means that there is a team member who spends most of their time doing testing.

http://localhost:8000/blog/2022/tester-is-an-overloaded-variable/

> [...] the difference between an agile tester and a quality engineer becomes rather moot. In practice they will be doing very similar things: avoiding to become a quality safety blanket for the team, and working in a supportive and collaborative way with their team on quality.

http://localhost:8000/blog/2022/agile-tester-or-quality-engineer-whos-to-say/


## Being embedded versus in a separate team

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


## Doing your job versus enabling your job

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


# So where does that leave us?

Again, not about unfairness of having to adapt. About unfairness of not having a clear, stable base.

Not a lamentation. Also makes the work interesting. (check my privilege though)

Hence, fundamental problem, "just keep adapting" is not a solution.

I don't have a solution. I have some more thoughts on related aspects.

The too big solution: stop outsourcing a large chunk of quality to specific roles (inc Head of Quality). Or stop doing that, while separating people. Sports teams and infantry squads don't. Or sports teams have a goalie, team member yet different. Specialization is needed. We say we want to build quality in, but we keep separating out building from testing. Big gap in paradigms / communities / ... between devs and testers.
Quality does not work that way (oursourcing). It's emergent. So it should be throughout your management chain.
Since that won't happen anytime soon, I'll keep my job and the challenge.
