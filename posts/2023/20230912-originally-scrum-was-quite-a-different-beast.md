<!--
.. title: Originally Scrum was quite a different beast
.. slug: originally-scrum-was-quite-a-different-beast
.. date: 2023-12-02
.. tags: agile, scrum, books
.. category: agile
.. link: 
.. description: 
.. type: text
-->

In 2001, nine years before the first version of the Scrum Guide[^1], Ken Schwaber and Mike Beedle published "Agile Software Development with Scrum". Scrum as described in that book is quite a different beast from what it is today.

Here are the three things that struck me most while reading it:

In this post I'll share the three differences that I found most intriguing.

Not saying we need to start doing this kind of Scrum, but these are striking differences. And I miss how radical it is in the way we often now do software development.

[^1]: The first version of the Scrum Guide was published in February 2010. You can find a [copy](https://res.cloudinary.com/mitchlacey/image/upload/v1589750495/Scrum_Guide_v1_Scrum_Alliance_qe0y2w.pdf) on Mitch Lacey's site.

<!-- TEASER_END -->



# three main differences

- no retrospectives
	- continuous removal of impediments
- scrum master
	- management role
	- project manager / team lead
	- engineer
- 30-day sprints with goal over tasks
	- tasks, not user stories or use cases


is there a product owner? -> yes, eg p 34


---


# A different breed of scrum master

I have written about scrum masters in the past, partially inspired by this book.

[What is a scrum master?](link://slug/what-is-a-scrum-master)

[Scrum master or scrum mascot?](link://slug/scrum-master-or-scrum-mascot)

two mentions in index: change agent p142, definition p31

## Authority

> The Scrum Master is a new management role introduced by Scrum. The Scrum Master is responsible for ensuring that Scrum values, practices, and rules are enacted and enforced. *(p 31)*

> The Team Leader, Project Leader, or Project Manager often assume the Scrum Master role. Scrum provides this person with the structure to effectively carry out Scrum's new way of building systems. If it's likely that many impediments will have to be initially removed, this position may need to be filled by a senior manager or a Scrum consultant. *(p 32)*

> How does the Scrum Master keep the team working at the highest level of productivity? The Scrum Master does so primarily by making decisions and removing impediments. When decisions need to be made in the Daily Scrum, the Scrum Master is responsible for making the decisions immediately, even with incomplete information. *(p 32)*

> The Scrum Master's job is to increase the productivity of the team in any way possible. Arranging chairs is one small demonstration of commitment. (p 42)

> The Scrum Master needs to have management's full support and engagement. Most importantly, the Scrum Master needs to have the authority to cause impediments to be removed. If management disagrees with actions that the Scrum Master takes, it should offer suggestions, provide guidance, and give coaching. But no matter what, management must support the Scrum Master. *(p 142)*

> However, the Scrum Master needs to know what authority he has to rapidly resolve impediments. If the answer is "not much," then maybe the organization in question isn't ready to implement Scrum. *(p 143)*

## Not the team's internal differences
> As a Scrum Master, I'm often tempted to help a team resolve its internal problems. Experience has taught me not to. The team has committed to a goal. When I help them resolve differences, I'm taking some of their responsibility away. The team committed to the goal; the team gets to figure out how to meet the goal, as best as they can. *(p 36)*

## Also a good engineer
> The best Scrum Masters are also good engineers. The Scrum Master helps the team improve its engineering practices, just as a coach teaches a team to play better. He or she causes the team to reevaluate and discard wasteful practices, and to assess, design and adopt new practices. For instance, Mike Beedle likes many Extreme Programming practices. He has helped Scrum teams implement them within their projects. *(p 60)*

---

__extra quotes__

> The Scrum Master represents management and the team to each other. At the Daily Scrum, the Scrum Master listens closely to what each team member reports. He or she compares what progress has been made to what progress was expected, based on Sprint goals and predictions made during the previous Daily Scrum. *(p 31-32)*

> As I [Ken Schwaber] ran the daily Scrums for the PNP team, it became apparent that I was fulfilling a management job. I blocked interference, allowed the team to keep focused, removed impediments and helped the team reach decisions quickly. This was a radical change, a flip to what management had previously done. The team figured out how to do what it had committed to do. Management's new and primary job was to maximize the team's productivity, to be there to help it do the best it could. *(p 7)*






# There is no retrospective, or rather it's continuous

daily scrum and review as 'control' moments

if management does not resolve impediments -> cancel sprint

relates to Maaret's: your job is to get better at software development, software is a side-effect

"The object isn't to make art, it's to be in that wonderful state which makes art inevitable." - Robert Henri => Woody Zuill

> If a team member identifies something that is stopping him or her from working effectively, the Scrum Master is responsible for recording and removing that impediment. Impediments should be written down on the white board on the wall. (p44, in section about Daily Scrum meetings)

> The Scrum Master's top priority is removing impediments. If team members inform the Scrum Master that he or she can do something to make them more productive, the Scrum Master should do it. The Daily Scrum gives the Scrum Master direct information on what he or she can do to improve the productivity of the team. (p 45)

> If the open impediments on the white board get to be lengthy, this may indicate that the larger organization isn't supporting the team. In this case, the Scrum Master may have to cancel the Sprint. This is a very powerful card to play. It should only be played when the Scrum Master is very concerned that the organization's support for the project is so low as to render the team ineffective. [...] The Scrum Master has observed there are many impediments and management is unwilling or unable to remove them. The Scrum Master should very carefully and intesely discuss these observations and the consequences of the lack of support with management before canceling the Sprint. Once the decision has been made to cancel the Sprint, the Scrum Master is effectively stating that there isn't enough management support or organizational effectiveness for the project to succeed. (p 45)

> Usually, the first question that is asked when a Sprint is terminated is: "Who is responsible for this meeting [Sprint Planning] occurring early?" Because people don't want to be named as the answer to this question, very few Sprints end up being terminated. (p 54)

> They [Daily Scrum meetings] don't only make everyone say what the issues are, but it makes everyone say it face to face to their management. This forces everyone to have courage and to be honest, and gives everyone a tool to put pressure on management about resolving issues. (p105-106)

privilege!

> __Risk of not resolving issues promptly.__ Scrum puts the burden of proof on management by requiring daily active management. In Scrum, the role of management is bi-directional, in that management also reports to the staff how it is resolving issues throughout the Daily Scrums. (p 109)


# 30-day sprint with sprint goal and tasks

main things:

- partial Sprint Backlog
- modify Spring Backlog throughout the sprint

not necessarily fully planned, adjust as you go based on sprint goal instead of later stories spill over

refer to toot: you're waterfalling because your sprints are too short

reply about Honeycomb: 8ths as smallest planning

> The requirements are listed in the Product Backlog. The Product Backlog represents everything that anyone interested in the product or process has thought is needed or would be a good idea in the product. It is a list of all features, functions, technologies, enhancements, and bug fixes that constitute the changes that will be made to the product for future releases. Anything that represents work to be done on the product is included in Product Backlog, These are examples of items that would go on the Product Backlog:

> - Allow users to access and view account balances for six months.
> - Improve scalability of product.
> - Simplify installation process when multiple databases are used.
> - Determine how workflow can be added to product. (p 33)

> To get the first Sprint going, Product Backlog only needs to contain enough requirements to drive a thirty-day sprint. A Sprint can start from only concepts and a wish list. (p 33)

> The Product Backlog emerges from this initial list as the product and the customer's understanding of their needs emerge and evolve. Backlog is dynamic. Management repeatedly changes it to identify what the product requires to be appropriate, competitive, and useful.(p 33)

> The Sprint planning meeting actually consists of two consecutive meetings. At the first meeting, the team meets with the Product Owner, management, and users to figure out what functionality to build during the next sprint. At the second meeting, the team works by itself to figure out how it is going to build this functionality into a product increment during the Sprint. (p 47) -> refinement in planning meeting

> The Sprint Goal is am objective that will be met through the implementation of a Product Backlog. For instance, this Sprint Goal could be:  
> __Sprint Goal__: to provide a standardized middleware mechanism for the identified customer service transactions to access backend databases. (p 48)

> The reason for having a Sprint Goal is to give the team some wiggle room regarding the functionality. (p 48)

> Sometimes only a partial Sprint Backlog can be created. The team may have to define an initial architecture or create designs before it can fully delineate the rest of the tasks. In such a case, the team should define the initial investigation, design, and architecture work in as much detail as possible, and leave reminders for work that will probably have to be done once the investigation or design has been completed. At that time, the work will be more fully understood and another team meeting can be convened to detail it. (p 49)

> The team modifies Sprint Backlog throughout the Sprint. As it gets into individual tasks, it may find out that more or fewer tasks are needed, or that a given task will take more or less time than had been expected. As new work is required, the team adds it to the Sprint Backlog. [...] When tasks are deemed unncessary, they are removed. (p 49)

> Sprints last for thirty calendar days. A team takes this long to get its arms around a problem and to produce a product increment. (p 52)

> However, one of the key differences of Scrum was that it allowed Backlog items other than functional requirements. This made tremendous difference because we could see for once the "hidden tasks" that we had left out by blindly making our plans "use case driven". (p138)
