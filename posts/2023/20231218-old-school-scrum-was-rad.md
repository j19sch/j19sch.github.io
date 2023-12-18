<!--
.. title: Old-school Scrum was rad!
.. slug: old-school-scrum-was-rad
.. date: 2023-12-18
.. tags: agile, scrum, books
.. category: agile
.. link: 
.. description: 
.. type: text
-->


In 2001, nine years before the first version of the Scrum Guide, Ken Schwaber and Mike Beedle published *"Agile Software Development with Scrum"*. This version of Scrum has some remarkable differences from even the [first version of the Scrum Guide](https://res.cloudinary.com/mitchlacey/image/upload/v1589750495/Scrum_Guide_v1_Scrum_Alliance_qe0y2w.pdf).

The three things that struck me most about this version of Scrum, were

- Scrum Master is a management role, preferably by an engineer
- there is no retrospective, impediments are addressed in the Daily Scrum
- Sprints are 30 days and have a goal, tasks can be added and removed throughout

While I don't want to claim we should return to this old-school version of Scrum, I do appreciate how radical it is compared to how software development is done - even today.


<!-- TEASER_END -->


# Scrum Master as an engineering manager

A Scrum Master can be [many different things](link://slug/what-is-a-scrum-master). *"Agile Software Development with Scrum"* clearly states that the Scrum Master-role is a management one:

> As I [Ken Schwaber] ran the daily Scrums for the PNP team, it became apparent that I was fulfilling a management job. I blocked interference, allowed the team to keep focused, removed impediments and helped the team reach decisions quickly. This was a radical change, a flip to what management had previously done. The team figured out how to do what it had committed to do. Management's new and primary job was to maximize the team's productivity, to be there to help it do the best it could. *(p 7)*

<!-- -->

> The Scrum Master represents management and the team to each other. At the Daily Scrum, the Scrum Master listens closely to what each team member reports. He or she compares what progress has been made to what progress was expected, based on Sprint goals and predictions made during the previous Daily Scrum. *(p 31-32)*

For this to work, the Scrum Master *"needs to have management's full support and engagement. Most importantly, the Scrum Master needs to have the authority to cause impediments to be removed."* (p 142) The Scrum Master also needs the authority to make decisions: *"When decisions need to be made in the Daily Scrum, the Scrum Master is responsible for making the decisions immediately, even with incomplete information."* (p 32) So it should come as no surprise when the book says *"The Team Leader, Project Leader, or Project Manager often assume the Scrum Master role.* (p 32)

However, something the Scrum Master is not expected to do, is to help the team with internal issues:
> As a Scrum Master, I'm often tempted to help a team resolve its internal problems. Experience has taught me not to. The team has committed to a goal. When I help them resolve differences, I'm taking some of their responsibility away. The team committed to the goal; the team gets to figure out how to meet the goal, as best as they can. *(p 36)*

Finally, it helps if a Scrum Master has an engineering background:

> The best Scrum Masters are also good engineers. The Scrum Master helps the team improve its engineering practices, just as a coach teaches a team to play better. He or she causes the team to reevaluate and discard wasteful practices, and to assess, design and adopt new practices. For instance, Mike Beedle likes many Extreme Programming practices. He has helped Scrum teams implement them within their projects. *(p 60)*




# There is no retrospective, there is only the Daily Scrum

During the Daily Scrum each team member answers the following three questions (p 43):

- What have you done since last Scrum?
- What will you do between now and the next Scrum?
- What got in your way of doing work?

For the last one, the question about impediments,

> [...], the Scrum Master should encourage them [the team] to think "outside the box." If this were the perfect work environment, what else would it have? More specifically, what could help the team be more productive, both as a group of individuals and a cohesive team? *(p 44)*

So this goes beyond the regular question about impediments, about something specific slowing you down right now. It's a question about what improvements can be made to the team, to the way-of-working, to the tooling, to the organization. It's a daily retrospective and it's the only retrospective in old-school Scrum.

Two things should happen with these impediments identified in the Daily Scrum. They *"should be written down on the white board on the wall."* (p 44) and they become the Scrum Master's responsibility: *"The Scrum Master's top priority is removing impediments. If team members inform the Scrum Master that he or she can do something to make them more productive, the Scrum Master should do it."* (p 45)

This relentless daily focus on improving productivity is radical enough, but it gets even better.

Too many open impediments is a reason to cancel the sprint:

> If the open impediments on the white board get to be lengthy, this may indicate that the larger organization isn't supporting the team. In this case, the Scrum Master may have to cancel the Sprint. This is a very powerful card to play. [...] Once the decision has been made to cancel the Sprint, the Scrum Master is effectively stating that there isn't enough management support or organizational effectiveness for the project to succeed. *(p 45)*



# All you need for a sprint is 30 days and a goal

Sprint planning starts with selecting an item from the Product Backlog, which *"consists of product features, functionality, infrastructure, architecture, and technology work."* (p 72) Next, the Sprint Goal is created: *"an objective that will be met through the implementation of a Product Backlog [item][^1]."* (p 48) The third and final step is that *"the team determines what work will have to be performed in order to reach the goal."* (p 49) They do this by compiling a list of tasks.

[^1]: Confusingly the authors use "Product Backlog" to refer to both the whole backlog as to an item on the backlog.

This may sound familiar, but there's an important thing to note about the third and final step. While the Sprint Goal should be clear and can't be changed, the team gets a significant amount of flexibility with the tasks.

For one, the tasks on the Sprint Backlog are expected to change during the Sprint:

> The team modifies Sprint Backlog throughout the Sprint. As it gets into individual tasks, it may find out that more or fewer tasks are needed, or that a given task will take more or less time than had been expected. As new work is required, the team adds it to the Sprint Backlog. [...] When tasks are deemed unnecessary, they are removed. *(p 49)*

Secondly, the Sprint Backlog does not need to be complete at the start of the Sprint:

> Sometimes only a partial Sprint Backlog can be created. The team may have to define an initial architecture or create designs before it can fully delineate the rest of the tasks. In such a case, the team should define the initial investigation, design, and architecture work in as much detail as possible, and leave reminders for work that will probably have to be done once the investigation or design has been completed. At that time, the work will be more fully understood and another team meeting can be convened to detail it. *(p 49)*

This ties in with why Sprints are 30 days long:

> Sprints last for thirty calendar days. A team takes this long to get its arms around a problem and to produce a product increment. *(p 52)*

So teams get time to figure things out during the sprint itself instead of having to refine at least a sprint ahead  - often as hidden work in the current sprint.



# Should we return to old-school Scrum?

Should we return to old-school Scrum? Probably not.

We should take inspiration from it, though. From how the scrum master is expected to be more than a mere [scrum mascot](link://slug/scrum-master-or-scrum-mascot). From how it puts impediments front-and-center to both the team and to management. And from how it gives engineers time to figure things out during the sprint. 
