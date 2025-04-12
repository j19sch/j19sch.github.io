<!--
.. title: A good tester is all over the place
.. slug: a-good-tester-is-all-over-the-place
.. date: 2023-11-26
.. tags: quality engineering, management, software development, software testing, test management
.. category: quality engineering
.. link: 
.. description: 
.. type: text
-->


Over the past year, I've been thinking about how testing-related roles are still an unsolved problem in software development. We keep trying different permutations: shifting left and shifting right, being closer to the programmers while not too far from other testers, doing less testing ourselves so we can support others more, etc.

And still, to be effective in any of these permutations, you can't let yourself be limited by them. You need to work both inside and outside the existing structures. You have to "be all over the place", in a good way.



# Testers do testing

Let's start with a straightforward statement: a tester tests. Then what is testing? I [still like](link://slug/reflections-on-my-testing-manifesto) the definition *"Testing is investigating in order to evaluate a product."* The most obvious thing to investigate, to test, is the code that is being written. The best way to do this, in my opinion, is through the combination of exploratory testing and test automation, i.e. what [Maaret Pyhäjärvi](https://maaretp.com/) has named "[contemporary exploratory testing](https://www.youtube.com/watch?v=T_67oQrPZhQ)". And to be clear, while the execution part tends to be the most visible, effective testing also needs good test strategy, design, and reporting.

<!-- TEASER_END -->

There's more to do as a tester, though, than testing the code that is being written. Testers should also be involved in monitoring production, in attending to CI/CD pipelines, in maintaining test data and test environments. And they should participate in refinement, design, and architecture.

So that's quite a wide range of activities, even when I leave out activities related to being a member of the development team (e.g. retrospectives) and to being an employee (e.g. all-hands meetings). Luckily, testers are not the only ones doing testing. Unluckily, this creates some challenges.


## But they're not the only ones testing

Other roles - programmers are the clearest example - seem to have a good overlap of what their focus is (programming) and what their domain is (only we do the programming). A curious thing about testing is that this is very much not the case. Testers are not the only ones doing testing.

Developers should test their own work. It cannot be that when you ask a developer *"Is the code you wrote good enough?"*, the reply is *"I have no clue, that's not my job. Ask a tester."* And the same applies to the other testing-related activities I mentioned - monitoring, pipelines, design - it's hard to imagine developers not being involved in those.

So based on a high-level list of activities, there doesn't seem to be anything that distinguishes a tester from a programmer. This raises an important question for any tester: if you do everything a programmers does, except for programming, what value do you add over a developer?

A cynical conclusion from this could be that testers are some kind of second-tier developers, focusing on the stuff that needs to happen, but that is not programming and that programmers shouldn't invest their time in.

I don't accept that conclusion. Testers can bring great value to their teams, because they don't have to focus on the programming. It allows them to bring something different.


## Yet they bring something different

The unique thing a tester brings, is not in the fact that they do testing. It's that they bring something different to that testing.

By being "a tester", they have the space to focus on testing. First of all, they can focus their professional development on this area. They can build and deepen their testing skills beyond a level that would make sense for non-testers. Secondly, throughout the development process, testers can take a testing perspective. They can keep the question *"How might this work? And how might it not?"* front of mind, leaving the question *"How can I build this?"* more in the background and to the other team members.

To be very clear, "being a tester" doesn't have to be a long-term role. You can have a team of programmers, where each sprint one team member takes the tester-role for that sprint. What you lose in having a dedicated specialist, you gain in raising the skill level of all team members.


## Please point at where the testing happens

All of this means, that it's hard to point in a meaningful way to where testing happens. There's no single activity in which all the testing is concentrated. There isn't a single role either. Testing - investigating in order to evaluate a product - happens everywhere, all the time, by everyone.

As such, testers need to be all over the place, all over software development, because that's where testing happens. There's more to it than that, though.



# Three axes to move around on<a id="three-axes-to-move-around-on"></a>

Next to being active all across the software development process, testers also need to decide, situation-by-situation, where they want to position themselves on three axes:

- do testing yourself or support testing by others,
- be embedded in a team or be part of a separate team,
- do your job or improve the system.

While I'll be focusing in this post on the dynamic aspect of these axes, there is a static aspect to them. The job you got hired to do, gives you a kind of 'neutral' position on these axes. For example, when I was a [quality engineer](link://slug/im-a-quality-engineer-and-im-not-sure-how-i-feel-about-that), I was expected to support testing by others, while embedded in two teams, and to do my job. To be effective though, I did have to do testing myself, team up with the other quality engineers, and improve the system. That dynamic, this continuous movement along these three axes, is in my experience essential to be effective as a tester.


## Doing testing yourself versus supporting testing by others

Doing testing yourself means that you do testing and share the results of your testing. A big risk here is that you become the sole owner of the kind of testing you do. It's your domain and others leave it for you to do. Having a dedicated "testing" column on your board is one sign that this might be happening.

Supporting testing by others means that you enable others to do testing. You talk with developers before they test, debrief with them after, and you test in a pair and/or ensemble. The big challenge here is that by not doing any testing yourself, but only supporting others, it becomes very hard to build a deep understanding of the product and technology. And that limits how well you can support the testing. You want to be specific and concrete in your support, not be limited to only handing out generic testing wisdom.

The middle ground between doing and supporting is often called whole-team testing. However, it's not really a middle ground, a balancing act between two extremes. Rather, you need to continuously decide how much doing and how much supporting makes sense in that particular moment, for that particular activity, with those particular team members. And you can't leave your team members guessing about those decisions. It requires an ongoing dialogue with them about what you do versus what you support.


## Being embedded in a team versus being in a separate team
One of the many good things Agile has done, is pull testers into the development team. Instead of having the testers do their work only after the programmers are done writing their code, they get to collaborate.

Unfortunately, with agile teams being relatively small (as they should), this leaves the tester in a lonely spot. There's probably only one tester on the team. So you don't have peers inside your team to run ideas by. As a junior tester, you don't have a more experienced tester to learn from. And your manager more likely than not has a programming background, so there's a limit to the support and mentoring you can get from them.

Those disadvantages do not mean that we should return to org structures that separate programming from testing. We should keep our cross-functional teams, with each team reporting to the same manager, responsible for the team's results. And we should create incentives and structures for the testers to connect with one another. That structure can be a test guild, a community of practice, a [regular ensembling session](https://ezagroba.github.io/mob-testing/#/), or just an informal catch-up meeting every week.

So it's not an either/or. Testers need to be both a member of their cross-functional team, and of the testing team. Where hopefully "the testing team" includes everyone with an interest in testing and not just the people with "tester" as their job title.


## Doing your job versus improving the system

As a tester your job is to test things. To uncover interesting information about the product.  Ideally you do this throughout the software development life cycle: from ideation to production. Ideally you have access to the code and to the necessary tools. Ideally your other team members are involved in testing and ideally they involve you in what they are doing.

Unfortunately, things often aren't ideal. And sometimes they are very far from it. Doing your job then means doing your best with whatever is available to you. Even if that means your testing is a lot less effective than it could be.

Things not being ideal is also an opportunity for change. You can try to improve the system. On some level that's expected of any team member. Testers, however, often seem to need to do more than that. Few organizations are set up in a way that enables good testing. Changing that is more of a manager's job, though.[^1] As a tester, without a manager's authority and without a manager's access to higher management, getting things to change will be a challenge at best and an impossible task at worst.

[^1]: [Maaret Pyhäjärvi](https://maaretp.com/) and I made an [incomplete model](https://www.linkedin.com/feed/update/urn:li:activity:7021181214204080128/) about this a year ago.

This makes this axis the hardest of the three. If you try to change the system too little, you'll struggle to do a good job testing. Try to change the system too much, you get hit by blowback and resistance. Both are demotivating and can have you heading towards a burn-out.

It's better to work in more subtle ways, picking the right opportunities to improve the system. That work, however, the work you do, just so you can do good testing, often remains invisible. Most people don't have an eye for it. And even if someone does, the testing work you do, will still be a more visible than your testing-enabling work.


# A good tester is all over the place

A good tester is all over the place. Roles and processes provide structure, a starting point. You can't limit yourself to only working inside those structures, though. You also need to be comfortable working outside (and around) them. Testing happens across roles, throughout the software development process. It happens everywhere all the time, so that's where a tester needs to be. 

That brings us to the three axes. You can't be everywhere at once. You need to make choices. Is this testing something you need to do or something you only need to support? Are you sufficiently connected to your team and to your fellow testers? Is it time to get some work done or is it time to work on the system?

As a tester, you need to find where the gaps are and decide which ones to fill. You need to be like water, flowing around the rocks, but also know when to become solid like ice. (And very rarely, you get to be the water that creeps into the cracks of a rock, freezes, and shatters it from within.)

And this is not just true for testers. All of the testing and testing-related roles I've had the past decade, were unstable to some degree. They required me to adapt, to keep re-inventing what my job was. I guess this partially explains why we keep coming up with new titles for what we do: quality assurance analyst, test engineer, software development engineer in test, quality engineer, etc. As an industry, we're just not sure what exactly to do with testing.



# Do we have to be, though?

If no solution to "the testing role" is stable, I want to start with a hat tip to everyone, testers and non-testers, who do their best to make it work regardless. It's a good fight, but not an easy one. So I wish I had a clear direction for a solution. I'm afraid I don't. The best I can do is share three elements that I think are part of the solution.

## Activities instead of roles

Roles, like "developer" and "tester", have value to HR. While I can imagine different solutions to the problems that roles solve for HR, those are not going to be easy to implement. So let's keep roles, but leave them to HR.

At a team-level, those same roles are incredibly limiting and thus damaging. People with all their richness of skills, knowledge, and experience, are reduced to "developer", "tester", "ux designer", etc. And we pretend that single label covers what they do: developing, testing, designing, etc.

This [confusion](link://slug/tester-is-an-overloaded-variable) of people, roles, and process steps means we rarely talk about what we do in a smart way. In a more specific, more granular way. What are the different activities that need doing? What skills and perspectives are needed for those activities? Who on our team can contribute?[^2]

[^2]: [Maaret Pyhäjärvi](https://maaretp.com/) has been doing great work mapping that our for her team(s). See for example ["Testers roles and services"](https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html) and [this diagram](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjhvut-TK-LDv4g4x6h-I40bkbuwQGf5vwMHezCj5UmCormNxbkGDCmpCCgPFhKzeTPQfit2-Hnb1sasiruYcPG5xpeT7vvBEzDijgBvFHQYEQkV7WPwXbtbFm9292LgooYdvy9w6zvV2UXY9YXiHfmMCLV52MIQOCp39Dg_9dKPWsCuHr3ymudFmhRWw/s2104/Screenshot%202023-11-16%20at%2021.13.59.png) from a [more recent post](https://visible-quality.blogspot.com/2023/11/secret-sauce-to-great-testing-is-to.html).


## Building bridges between communities

Testers are the most adjacent to programmers, without being programmers. And yet, there are very few bridges between the communities. A tester at a developer conference and a developer at a tester conference will feel the same way: as the odd one out. While both communities need spaces where they can have deep conversations about their specializations, we also need spaces where these communities come together. And more than just those two communities. Business analysts, scrum masters, product owners, SREs, engineering managers, etc. Where is the space where we all together can have a conversation about software development?[^3]

[^3]: One of the goals of [FroGS conf](https://frogsconf.nl/), an open space conference I co-organize, is to be such a bridge.


## Knowing what can be dreamt of

Some things you need to experience to know that they are possible. Or at least, you need to hear the stories of those that have had that experience. Before you can dream, you need to know what you can dream of. You need to know how big your dreams can be - and how wild.

---

## Questions for reflection

Does any of this make sense? How dynamic is your role, both across software development and the three axes? How often do you talk about that with your team members or your manager? What is it that you dream of?

---

*(edit 26 December 2023)* Today James Thomas published an excellent post titled ["Make, Fix, and Test"](https://qahiccupps.blogspot.com/2023/12/make-fix-and-test.html). In it he reflects on some of his recent work and identifies three additional dimensions to the three axes I identified in this post. I can fully relate to his three dimensions and am positively intrigued by the ways our posts and models relate to each other. Great food for thought!
