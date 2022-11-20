<!--
.. title: "Tester" is an overloaded variable
.. slug: tester-is-an-overloaded-variable
.. date: 2022-08-04 11:39:25 UTC+02:00
.. tags: management, semantics, software testing, test management
.. category: software testing
.. link: 
.. description: 
.. type: text
-->

Yesterday I came across a post on LinkedIn explaining why there are no testers in Scrum[^1]. What struck me most about the post was the amount of work the word "tester" was doing. In one sentence it meant one thing (a role in a team), in the next sentence something else (a step in the process), and so on. Hence the title of this post: the word "tester" was being used as an overloaded variable. So let's do some unpacking.

[^1]: Which I don't think is true. The 2020 [Scrum Guide](https://scrumguides.org/scrum-guide.html) says *"Scrum Teams are cross-functional, meaning the members have all the skills necessary to create value each Sprint."* and *"Developers are the people in the Scrum Team that are committed to creating any aspect of a usable Increment each Sprint. The specific skills needed by the Developers are often broad and will vary with the domain of work."*  
It does not say that every single Developer should have all the skills necessary. Nor does it not limit Scrum's Developer-role to specific skills or activities. The Scrum Guide also states early on *"We use the word "developers" in Scrum not to exclude, but to simplify. If you get value from Scrum, consider yourself included."*



# Testers to people management
*"Having a tester"* means that there are people with the official title of "tester" or "QA engineer" or whatever within the company. For the purposes of people management[^2], there's a distinction between this role and the other roles in the company. This allows for more specific expectations about the role, for different career paths and salary scales, etc.

<!-- TEASER_END -->

However, it tells you little about how what these testers do, is organized. There might be a separate reporting chain for testing all the way up the to the CTO or CIO. There might be a matrix structure, where people management is separated from work management. Or every member in the team reports to the same engineering manager or team lead. It also does not tell you if testers are part of the development teams[^3] and if so, in what way exactly. The only thing it really tells you is that some people got a contract that lists for example "test engineer" as their job.

[^2]: I refuse to call it Human Resources. [Emily Webber](https://emilywebber.co.uk/) has a great blog post (and flowchart) on this topic: ["Should you call people resources?"](https://emilywebber.co.uk/should-you-call-people-resources/)

[^3]: This tends to be called "embedded testers", which I find increasingly odd. It makes it sound you're not a real team member, but someone inserted into the team from the outside.




# Testers as a process step

*"Having a tester"* means there is a testing phase after the development phase - implying a large and information-poor handover from development to testing[^4]. As is often the case, the specifics matter here.

It is true there is always some testing you can only do after you believe all the code has been written. And if you have a tester, there's usually[^5] some handover to that tester. However, the timescale and the level of collaboration make all the difference here. A handover of 3 weeks of programming work via poor documentation is a very different beast from a handover of 3 hours of programming work via a short pairing session. The former type of handover leads to a world of pain, while the latter reaps the benefits that testers can provide[^6].


[^4]: What rarely gets mentioned in this context is the handover of bug reports from testing to development and the handover of fixes from development to testing.

[^5]: Ensembling (mob programming/testing) is an excellent way to eliminate handovers.

[^6]: The benefits a tester can provide, extend beyond the current topic of "checking stuff at the end", btw.



# Testers and their team
*"Having a tester"* means someone with the role of tester is involved in at least part of software development and delivery. This can take on two quite different forms: being a tester for the team versus being a tester of the team.


## Tester for the team
*"Having a tester for the team"* means there is someone responsible for the work labeled as "testing". If this tester is a member of the development team, they tend to be the sole owner of the "testing" column[^7] on the team's board. So in a very real sense, this team is operating as two teams: a development team and a testing team[^8].

For this reason I think that this setup is in many ways the same as having a separate team of testers[^9]. It's not the team that's doing the testing; testers are doing the testing for the team. If the tester is not available, little to no testing will happen.


## Tester of the team
*"Having a tester of the team"* means that there is a team member who spends most of their time doing testing. All members of the team do all sorts of things, including testing. The tester of the team, however, has testing as their main focus, similar to how other team members have their own areas of focus.

[Maaret Pyhäjärvi](https://twitter.com/maaretp)'s blog post ["Tester roles and services"](https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html) does a great job illustrating this way of working. She distinguishes 15 different testing hats and shows how each of the four team members either never wear that specific that, occasionally engage in that hat's activity, or are focused on it. Today she re-posted the [diagram on LinkedIn](https://www.linkedin.com/posts/maaret_it-is-possible-to-both-have-a-tester-in-the-activity-6960845948419747840-NKpv), saying: *"It is possible to both have a tester in the team and have full team testing."*

[^7]:It's always interesting to see which kinds of testing do happen inside that column and which kinds don't.

[^8]: Two good definitions of teams: *"If some of us can win, while others lose, we're not a team."* (source?) and *"A team is a group of people that share a problem."* ([Douglas Squirrel](https://twitter.com/douglassquirrel))

[^9]: They are not the same for activities that don't fit in the "testing" column. A tester inside the team, even if it's a for-the-team tester, will have more opportunities to participate in other team activities than a tester who's in a separate testing team.


<div style="margin-top: 2.7rem" />


So all of this to say what exactly? I guess nothing more than this: if you say that you have testers or that you don't have testers, that does not tell me a lot. So I'd be curious to hear more about how you do software.

---

*This post was also published in the [November '22 issue](https://teatimewithtesters.com/wp-content/uploads/2022/11/TTwT_November_2022.pdf) of [Tea-time with Testers](https://teatimewithtesters.com/).*
