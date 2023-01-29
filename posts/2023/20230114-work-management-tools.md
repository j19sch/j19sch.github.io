<!--
.. title: Our work management tools are limiting our imagination
.. slug: our-work-management-tools-are-limiting-our-imagination
.. date: 2023-01-29 13:46:25 UTC+01:00
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

Arguably that's fine. The work needs to be managed, artefacts and tools help us in that. However, there is the danger of the reifaction of those artefacts. We're no longer managing the work related to the story, we're managing the aretefacts related to the story in our work management tool.

And at that point we've strayed quite a bit from the [Agile Manifesto](https://agilemanifesto.org/)'s *"Individuals and interactions over processes and tools"* and *"Working software over comprehensive documentation"*.



# Affordances, signifiers, and constraints -> Affordances and contraints shape our tools and ourselves

To understand what's happening here, there's the quote:

> We shape our tools and thereafter our tools shape us.[^1]

[^1]: This quote is often ascribed to Marshall McLuhan, but that's [up for debate](https://quoteinvestigator.com/2016/06/26/shape/).

To dig a bit deeper, I think *"The Design of Everyday Things (revised and expanded)"*" by Donald A. Norman is of use. More specifically, what he wrote about affordances, signifiers, and constraints.

### Affordances and signifiers

Norman summarizes the meaning of affordances and signifiers as:

> Affordances are the possible interactions between people and the environment. Some affordances are perceivable, others are not.  
> Perceived affordances often act as signifiers, but they can be ambiguous.  
> Signifiers signal things, in particular what actions are possible and how they should be done. Signifiers must be perceivable, else they fail to function. (p 19)

One of the classical examples from his book are doors and door handles. Sometimes you need to push a door to open it, sometimes you need to pull it, sometimes either works. Those are its affordances. But how do you know which of these three it is? That's where signifiers come in. A sign saying "push" or "pull" is a solution, but a better solution is to shape the door handle in a way that it's obvious whether you need to push or pull.

One of my own favorite examples of affordances is comparing Slack with MS Teams. On the one hand, they share a lot of affordances. You can chat with people in channels, to give the most obivous example. On the other hand, they have a very different feel - at least to me. Slack is a place where I feel I can hang out, MS Teams is not.

### Constraints

Norman identifies seven fundamental principles of design in his book (p 72-73). Affordances and signifiers are numbers 4 and 5. Constraints are number 7: 

> Constraints. Providing physical, logical, semantic, and cultural constraints guides actions and eases interpretation. (p 73)

Although all four kinds of constraints are relevant here, I want to especially point out cultural constraints:

> Cultural constraints and conventions are learned artificial restrictions on behavior that reduce the set of likely actions, in many cases leaving only one or two possibilities. (p 76)

> Conventions are actually a form of cultural constraint, usually associated with how people behave. Some conventions determine what activities should be done; others prohibit or discourage actions. But in all cases, they provide those knowledgeable of the culture with powerful constraints of behavior. (p 131)


### Affordances and contraints shape our tools and ourselves

Affordances on the one hand, and contraints on the other, map very well to the quote I started this section with. We shape our tools by adding affordances to them; thereafter they shape us by becoming constraints. And then these constraints might lead us to identify new needs, which become new affordances, and round and round it goes.

Initially these constraints will be mostly on the physical, logical, and semantic level. The tool makes sense in its context. Then with enough adaption, cultural constraints will build around it. The tool will make certain ways to manage work obvious, and others unimaginable. In this sense I think our work management tools have played and are playing a significant role in the reduction of Agile to the bland flavor of Scrum most Agile teams seem to be using these days.


### How are these constraints limiting us?

I can think of two ways in which these constraints are limiting us. A larger one related to commoditization and innovation (shoutout to Wardley mapping). A smaller one related to ownership.

Most (all?) work management tools are extremely similar, providing the features I listed above. They compete mostly on things like price and legitimacy, barely on feature sets. They're a commodity. And through their constraints they also commoditize the way people manage work, i.e. the bland scrum I mentioned earlier. So no innovation, but also no competitive advantage in how people manage work. Hence me using the words *"leaving money on the table"* in the question I started this post with.

Of course, it's very well possible that in your context doing work management like everyone else is perfectly fine. That it doesn't make sense to be an innovator in this area. However, these constraints are still limiting you. They are limiting the ownership your team members feel when it comes to work management.

To give one example, during a company Agile Guild meeting someone asked: "How do you do story points well?" And despite a colleague and me trying introduce the question "What would happen if you stopped using story point?" into the conversation, there was no interest. The person wanted to do story points and wanted to get them right.

Our tools are limiting us in imagining better ways to manage our work.



# Let's reclaim our imagination

At this point it's important to distinguish two questions. If you ask me *"But we still need to do all the stuff these tools allows us to do right? We need to visualize work, we need documentation, we need cross-team coordination."* I'd say: *"Yes, we do"* But I'd also add the question: *"Do we need to do these things in the most obvious way as provided by our tools?"* Because I don't think we do.

We don't need to accept the constraints created by our work management tools. And that can start small. Get rid of one of the many fields on your cards and see if anyone misses it. Create a virtual whiteboard for each epic and use that instead of the Description fields. Limit the number of "in progress"-columns (ideally to one), because if you can't remember the status of everything you're working on, you're probably doing too many things. Stop distinguishing bugs and features in your backlog, because once they're in the backlog, it matters what value they add to the product, not if they're a bug or a feature.

And if you're ready for something larger, [Maaret Pyhäjärvi](https://maaretp.com/) is a great inspiration. She recently shared a [list of things](https://www.linkedin.com/feed/update/urn:li:activity:7021350602873913344/) she has done differently in the past, and she has published a [blog post](https://visible-quality.blogspot.com/2022/12/a-no-jira-experiment.html) about how she *"got to stop using Jira for planning and tracking of work"*.

We need to reclaim our imagination, both in big and small ways. Uncover better[^2] ways of developing software by tring out different things. And perhaps it won't ever happen again that 17 people discovering these new ways get together and succeed in publishing a manifesto that captures the moment and shapes an industry. And that's ok. That too, shouldn't limit us in what we dare to imagine.

[^2]: And sometimes worse ways. Then we dust ourselves off, learn, and try something else.
