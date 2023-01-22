<!--
.. title: Our work management tools are limiting our imagination
.. slug: our-work-management-tools-are-limiting-our-imagination
.. date: 2023-01-22 13:46:25 UTC+01:00
.. tags: quality engineering, agile
.. category: agile
.. link: 
.. description: 
.. type: text
.. previewimage: /images/2023/work-mgt-tools/fig4-stories-on-a-wall.jpg
-->

# ToDO

- better title
	- Our work managment tools are limiting our imagination
- tl;dr


---


About two weeks ago I had a thought that felt both serious and not serious, so [I asked Mastodon](https://chaos.social/@joeposaurus/109635747014542350) if I should write a post about it:

> Should I write a blog post about companies leaving money on the table by not leveraging their choice of work management tool (Jira, Shortcut, etc) as a competitive advantage?

31% said "yes" and 54% said "a post about what now?", which I suppose reflects my own feelings about the topic. And it feels as an encouragement to write this post, especially because of that 54%. So let's talk about work management tools, the original (user) stories, affordances and signifiers, and how these tools are hurting agility. 



Jira, Shortcut, YouTrack, Trello, Basecamp, Asana, ClickUp, Rally

# The core idea (tl;dr)

Current work management tools (Jira, Shortcut, Asana, YouTrack, etc):


- try to be too many things
- suggest a specific way of working without us noticing, with us thinking that's the default


<!-- TEASER_END -->


# What do work management tools do?

At the core of any work management tool I've seen or used in software development, are cards representing work, grouped by status. Initially these were physical cards on a wall. As described for example in "Extreme Programming Explained (2nd ed)" (Kent Beck with Cynthia Andres):

> Give stories short names in addition to a short prose or graphical description. Write the stories on index cards and put them on a frequently-passed wall. (p 45)

What that looks like, with the cards sorted by statyus is shown on page 40 in figure 4:

<div class="d-flex justify-content-center">
	<figure class="figure" style="width:65%">
		<img src="/images/2023/work-mgt-tools/fig4-stories-on-a-wall.jpg" class="figure-img img-fluid rounded"
			alt="Figure 4 Stories on a wall from Extreme Programming Explained 2nd ed. A wall with index cards grouped into Done, This Week, This Release, To Be Estimated, Future."/>
	</figure>
</div>

Note that having physical cards on a physical wall was a conscious choice:

> Every attempt I've seen to computerize stories has failed to provide a fraction of the value of having real cards on a real wall. If you need to report progress to other parts of the organization in a familiar format, translte the cards into that format periodically. (p 45)

With *"Extreme Programming Explained (2nd ed)"* being from 2004 this may seem outdated advice, but James Shore delivers the same message in the second edition of his *"The Art of Agile Development"* which was published in 2021:

> Finally, another common change is to track stories in a spreadsheet, or issue tracking tool, rather than on index cards. That can make a list of stories easier to read, but it makes visualizations and collaboration more difficult. It's a net loss that's hard to appreciate without experience. Give cards at least three months before trying alternatives. Even if your team is remote, use virtual index cards on your virtual whiteboard rather than a spreadsheet or issue tracking tool. (p 138)

And similar to Kent Beck he emphasizes limiting the information on a story or card:

> *Stories* are for planning. They're the playing pieces of the planning game. That's it! Alistair Cockburn calls them "promissory notes for future conversations." (p 13)

> Because stories are just a reminder to have a conversation, they don't need to be detailed. (p 130)


## The digitalization of work management tools

However, that's not how most people work. They do use a computerized work management tool such as Jira, Shortcut, Asana, YouTrack, etc. And that allows you to do a lot more:

- longer descriptions: requirements or acceptance criteria, implementation details, how to test, questions, risks
- have a comments section
- finegrained statuses with access control
- use additional fields: component(s), issue type, project, priority, fix version, ...
- assign stories to one or several team members
- tracking epics and tasks together with the stories
- integration with your version control, CI/CD pipeline
- track relations between cards: relates to, blocks, depends on, ...
- graphs (eg. burn-up/down chart), dashboards, and reports
- maintain a large backlog
- do all of this across teams / on department level

So instead of a lightweight work management tool, we end up with a work adminstration system. Instead of a tool to enable conversations, we have a knowledge management application. And that leads to problems. I'll give a few examples below and then share the underlying bigger problem.

### Work management tools used for documentation

With the introduction of description fields, work managment tools allow us to capture a lot more detail for each story. So these work items become a kind of a documentation. Unfortunately, a poor kind at that.

They are written before the work is done. Things we learn after refinement are often added in comments (if it all) instead of updated in the description. Work items are transient. The description of one feature might be linked to five work items, some of them ammending, changing, or removing parts of other work items. So getting a picture of the current state of a feature is a form of archeology. Finally, I suspect that filling the description field of a work item often is sufficient to satisfy our felt need for documentation. So we don't write any additional documenation.

### Work management tools used for backlogs

Managing a backlog on paper index cards comes with toil, but arguably that's a good thing. A digital backlog lets you keep adding and adding stuff. There's no incentive to be reluctant in adding things, or to clean it up, because there's just too much stuff in it. For some excellent practical advice on this topic, go read Elizabeth Zagroba's post [*"Half-Life For Your Backlog"*](https://elizabethzagroba.com/posts/2022/11_19_half-life_for_your_backlog/).)

It's a good thing we have been throwing some proper computing power at our backlogs, or many of us would have ended up as one of Jerry Weinberg's clients and their bug database:

> We have so many bugs, our bug database doesn't work efficiently. (p 40, Perfect Software and Other Illusions about Testing, Jerry Weinberg)


### Work management tools used for work breakdown structures

Breaking down stories into tasks is nothing new. (Extreme Programming Explained 2nd ed describes it on page 46-47.) Digital tools do make it easier to do that well in advance, because it's easy enough to change them later. They also make it easy to group stories into epics and let you see all stories in an epic with a click of a button. Next there's the feature of tracking relations between stories, e.g. a dependency. Finally, we do all of this in one digital tool across all teams. And what we end up with is a reinvention of work breakdown structures, Gantt charts, and PERT charts. The only difference is the agile terminology and hopefully a more vertical work breakdown than in the waterfall days.


## Managing the work in the work management tool becomes work

With all these additional features and uses of our work management tools, we also spend more time in those tools. Instead of an ancillary tool to facilitate doing the work, managing all the information in the tool becomes additional work. Instead of the tool being an aide for building software, we have to split our time between building software and the artefacts collected in our work management tools.

Arguably that's fine. The work needs to be managed, artefacts and tools help us in that. However, there is the danger of the reifaction of those artefacts. We're no longer managing the work related to the story, we're managing the story artefact in our work management tool.

And at that point we've come quite far from the [Agile Manifesto](https://agilemanifesto.org/)'s *"Individuals and interactions over processes and tools"* and *"Working software over comprehensive documentation"*.









# Affordances. signifiers, and constraints (intermezzo / interlude)

## Affordances -> how our tools shape us

> We shape our tools and thereafter our tools shape us.[^1]

[^1]: This quote is often ascribed to Marshall McLuhan, but that's [up for debate](https://quoteinvestigator.com/2016/06/26/shape/).



Affordances and signifiers of our work management tools shape our behaviour.
Affordances are tempting. Making decisions for us. -> If all you have is a hammer, ...

It doesn't feel like a choice. It's the normal/default way of doing things.

- Teams vs Slack: I can hang out in Slack, but not in MS Teams.
- title vs description vs comments
- assign to one, to many, to team
- epics -> stories -> tasks
	- old-school work breakdown structure, kinda waterfall, although slices are more vertical



The Design of Everyday Things (revised and expanded) by Donald A. Norman

classic example: door handles that through their shape (signifier) make it clear if they need to be pushed or pulled (affordance)

> An affordance is a relationship between the properties of an object and the capabilities of the agent that determine just how the object could possibly be used. (p 11)

> The notion of affordance and the insights it provides originated with J. J. Gibson, an eminent psychologist [...] (p 12)

> But just as I appropriated *affordance* to use in design in a manner somewhat different than its inventor had intended, [...] (p 14)

> Perceived affordances help people figure out what actions are possible without the need for labels or instructions. I call the signalling component of affordances *signifiers*. (p 13)

> The first edition of this book introduced the term *affordances* to the world of design. (p 13)

> "Affordances determine what actions are possible. Signifiers communicate where the action should take place. We need both." (p 14)

> Affordances represent the possibilities in the world for how an agent (a person, animal,or machine) can interact with something. Some affordances are perceivable, others are invisible. Signifiers are signals. (p 18)

> "To summarize:
>
> - Affordances are the possible interactions between people and the environment. Some affordances are perceivable, others are not.
> - Perceived affordances often act as signifiers, but they can be ambiguous.
> - Signifiers signal things, in particular what actions are possible and how they should be done. Signifiers must be perceivable, else they fail to function."" (p 19)


constraints 73

7 principles of design p 72-73

> 7. Constraints. Providing physical, logical, semantic, and cultural constraints guides actions and eases interpretation. (p 73)


# how is this hurting agility?

we still need all (most) of this stuff right?
we document more, but we need some documentation
we track work across teams, but that needs to happen in some way
etc etc

the tool is a commodity (Wardley mapping) -> the practices become too -> no competitive advantage

should you? depends, but Accelerate convincing point of how crucial it is to be good at sw dev


Individuals and interactions over processes and tools -> managing the work management tool
Working software over comprehensive documentation -> managing the work management tools
https://agilemanifesto.org/



## Maaret -> what different can look like

A No Jira Experiment
https://visible-quality.blogspot.com/2022/12/a-no-jira-experiment.html

https://www.linkedin.com/feed/update/urn:li:activity:7021350602873913344/

What if not break down epics into stories in advance?
Need someone like Maaret to come up with and try it. Goes against 20+ years of agile.
