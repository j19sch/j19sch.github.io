<!--
.. title: "Tester" is an overloaded variable
.. slug: tester-is-an-overloaded-variable
.. date: 2022-08-03 17:12:25 UTC+02:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
-->

Yesterday I came across a post on LinkedIn explaining why there are no testers in Scrum[^1]. What struck me most about the post was the amount of work the word "tester" was doing. In one sentence it meant one thing (a role in a team), in the next sentence something else (a step in the process). Hence the title of this post: the word "tester" was being used as an overloaded variable.

**people management**  
*"Having a tester"* means that there are people with the official title of "tester" or "QA engineer" or whatever within the company. For the purposes of people management[^2], there's a distinction between this role and the other roles in the company. This allows for more specific expectations about the role and for different career paths and salary scales.

<!-- TEASER_END -->

It tells you little however about how what these testers do, is organized. There might be a separate reporting chain for testing all the way up the to the CTO. There might be a matrix structure, where people management is separated from work management. Or every member in the team reports to the same engineering manager or team lead.


**process step**  
*"Having a tester"* means there is a testing phase after the development phase. There is a tiny sliver of truth in this. There is always some testing you can only do after you believe the programming work is completed. And if you have a tester, there's usually some hand-over to that tester involved.

This picture leaves out two important things, though. Firstly, the timescale and the level of collaboration make a big difference. A documents-only hand-over of 3 months of programming work is a very different beast from a hand-over through pairing of 3 weeks of programming work. On a theoretical level you could argue there always is a hand-over. In practice, you can do a hand-over where the benefits of getting the tester involved greatly outweigh the cost of that hand-over.
Secondly, the description in the previous paragraph ignores all the other valuable work a tester does. It reduces its view of a tester's role to "checking stuff at the end".


**testers in a separate team**  
didn't think of this one initially  
arguably the same as the next one, and previous one applies


**tester for the team (team role)**  
*"Having a tester"* means that there is a team member responsible for the work labeled as "testing". Often you'll see that the team's board has a "testing" column of which the tester is considered the sole owner. In these cases it's not that hard to argue that this team is rather two teams than one single team.

So when it comes to programming and testing, this team operates more as two separate teams than as a single team.

Interesting to see what testing is seens as part of the testing column and what's not.


**tester of the team (main focus)**  
*"Having a tester"* means that there is a team member who spends most of their time doing testing. Other team members are also testing, but their main focus is on something else.

[Maaret Pyhäjärvi](https://twitter.com/maaretp)'s blog post ["Tester roles and services"](https://visible-quality.blogspot.com/2021/07/tester-roles-and-services.html) does a great job illustrating this. She disintguishes 15 different testing hats and shows how each of the four team members either never wear that specific that, or occasionally engage in that hat's activity, or are focused on it.

--- 

Of the four "testers" described above, some are mutually exclusive, some are not.

All of this to say, what actually? I guess: I don't care if you have testers or not; I want to know more about how you do software.

don't tell me if you have testers or not, tell me how you do software

I don't care to hear if you have testers or not ...


[^1]: Which I don't think is true. The 2020 [Scrum Guide](https://scrumguides.org/scrum-guide.html) says *"Scrum Teams are cross-functional, meaning the members have all the skills necessary to create value each Sprint."* and *"Developers are the people in the Scrum Team that are committed to creating any aspect of a usable Increment each Sprint. The specific skills needed by the Developers are often broad and will vary with the domain of work."*  
It does not say that every single Developer should have all the skills necessary. It also does not limit Scrum's Developer-role to specific skills or activities. The Scrum Guide even states early on *"We use the word "developers" in Scrum not to exclude, but to simplify. If you get value from Scrum, consider yourself included."*

[^2]: I refuse to call it Human Resources. For the reason why, see this excellent blog post by [Emily Webber](https://emilywebber.co.uk/): ["Should you call people resources?"](https://emilywebber.co.uk/should-you-call-people-resources/)
