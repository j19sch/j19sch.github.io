<!--
.. title: The affordances of our work management tools are not very agile
.. slug: work-management-tools
.. date: 2023-01-14 13:46:25 UTC+01:00
.. tags: quality engineering, agile
.. category: agile
.. link: 
.. description: 
.. type: text
.. previewimage: /images/2023/work-mgt-tools/fig4-stories-on-a-wall.jpg
-->

# ToDO

- better title
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

- documentation? kind of? but not really? but no other?
- adding stuff in commments instead of description


### Work management tools used for backlogs

https://elizabethzagroba.com/posts/2022/11_19_half-life_for_your_backlog/

- should it be easy to manage a large backlog?
	- Weinberg story about bug db performance

> We have so many bugs, our bug database doesn't work efficiently. (p 40) - Perfect Software and Other Illusions about Testing, Jerry Weinberg


### Work management tools used for work breakdown structures
- epics -> stories -> tasks
	- old-school work breakdown structure, kinda waterfall, although slices are more vertical


## Managing the work management tool replaces doing the work

- all the extra fields
	- from managing work to capturing information / documentation
	- to do list and done list and journal and documentation
	- huge backlogs, afraid to delete stuff -> EZ post


- alt title Managing the work management tool becoming work
- managing the work versus managing the work (working the management?)
- one is managing the actual work, the other is managing the work artefacts
- isntead of a tool, something ancillary, the work management becomes a focus
















# Intermezzo: Affordances. signifiers, and constraints

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

the tool is a commodity (Wardley mapping) -> the practices become too -> no competitive advantage

should you? depends, but Accelerate convincing point of how crucial it is to be good at sw dev


Individuals and interactions over processes and tools -> managing the work management tool
Working software over comprehensive documentation -> managinf the work management tools
https://agilemanifesto.org/



## Maaret -> what different can look like

A No Jira Experiment
https://visible-quality.blogspot.com/2022/12/a-no-jira-experiment.html

https://www.linkedin.com/feed/update/urn:li:activity:7021350602873913344/

What if not break down epics into stories in advance?
Need someone like Maaret to come up with and try it. Goes against 20+ years of agile.
