<!--
.. title: Thinking about quality: management paradigms and quality
.. slug: management-paradigms-and-quality
.. date: 2021-03-15 09:32:08 UTC+01:00
.. tags: peer conference, quality, management, paradigms
.. category: quality
.. link: 
.. description:
.. type: text
-->

On 30 January 2021 I participated in the Quality Acceleration Peer Conference organized by Huib Schoots and Joost Voskuil. Participants were [Alan Page](https://twitter.com/alanpage), [Areti Panou](https://twitter.com/unremarkableQA), [Ash Winter](https://twitter.com/northern_tester), [Bart Knaack](https://twitter.com/btknaack), [Conor Fitzgerald](https://twitter.com/conorfi), [Rouke de Jong](https://twitter.com/roukedejong), [Gwen Diagram](https://twitter.com/gwendiagram), [George Dinwiddie](https://twitter.com/gdinwiddie), [Janet Gregory](https://twitter.com/janetgregoryca), [Joost Voskuil](https://twitter.com/joost_voskuil), [Joost van Wollingen](https://twitter.com/jpjwolli), [Martijn Meijering](https://twitter.com/mmeijeri), [Rob Meaney](https://twitter.com/robmeaney), [Vincent Wijnen](https://twitter.com/vinwijnl) - with [Huib Schoots](https://twitter.com/huibschoots) facilitating the peer conference. The main topics mentioned in the invite were: "How can you sell quality?", "How can you convince people that quality can accelerate software delivery?", and "What limitations or barriers do you hit?"

Reflecting during and after our discussions on these topics, I realized there are some interesting things going on about how we talk about quality and how to sell it. Enough interesting things to fill more than one blog post, so this will be a four-part series. And I might expand on some ideas in the series after that.

This is the third part, exploring five different management paradigms as identified by [Carol Sanford](https://twitter.com/carolsanford) in her book "[The Regenerative Business](https://carolsanford.com/the-regenerative-business/)" and how they affect quality. The first part was about choosing your value system can be found [here](link://slug/choosing-your-value-system). The second part about selling quality can be found [here](link://slug/who-doesnt-want-quality).

## Psychological cover and psychological safety
If the challenge of quality is getting several things right (perception, desire, and means) and getting to an agreement among people, how we organize ourselves becomes a crucial topic. As W. Edwards Deming said: "A bad system will beat a good person every time." Or as Kurt Lewin said in a more neutral way: "Behavior is a function of the Person and the Environment." An important part of any environment is psychological safety. In [episode 155](https://www.conversationaltransformation.com/blog/we're-the-aliens-three-ways-to-seek-safety/) of their [Troubleshooting Agile](https://www.conversationaltransformation.com/troubleshooting-agile-podcast/) podcast [Jeffrey Fredrick](https://twitter.com/Jtf) and [Douglas Squirrel](https://twitter.com/douglassquirrel) make an interesting distinction between psychological cover and psychological safety.

<!-- TEASER_END -->

With psychological cover you feel safe (covered) because someone tells you exactly what to do (build this thing) or because something tells you exactly how to do it (follow this process). It's a way to be held blameless, because you're just doing what you're told (asked?) to do. With psychological safety your focus is not on being told the what or the how, but on the actual mission. Your focus is on the problem you're sharing with a group of people (Douglas Squirrel's definition of a team). And that means you don't have any cover, so it will be scarier than the other two options.

In their book "[Agile Conversations](https://itrevolution.com/agile-conversations/)" Squirrel and Fredrick make the distinction between compliance and commitment. Compliance is going through the motions; commitment is engaging with your whole self. Compliance is doing what you're told; commitment is actively  participating. Psychological cover is great if you're looking for compliance. If you want commitment, you'll need psychological safety.

Thinking about those ideas I couldn't help but notice similarities to the management paradigms [Carol Sanford](https://twitter.com/carolsanford) distinguishes in her book "[The Regenerative Business](https://carolsanford.com/the-regenerative-business/)". (To be fair, I should point that Carol Sanford does have some [issues with the idea of psychological safety](https://carolsanford.com/2017/11/why-psychological-safety-is-the-wrong-goal-for-business-and-bad-for-democracy/), especially if seen as something that managers need to create for their reports.) In this post I will walk you through these five management paradigms and how they affect quality.


## Five different management paradigms

### The aristocracy paradigm
The aristocracy paradigm is about hierarchy and power. There are those in a position of authority who get to make the decisions and there are those who aren't. A small group is entrusted to make decisions on behalf of everyone. Instead of using hierarchies as a way to organize thinking, they are used as a way to organize people to do different levels of thinking. So a small group of people gets to decide what work gets done and how to do it.

Two typical practices from this paradigm are delegation and job descriptions -  where I'd say that job descriptions can be seen as a formalized way of delegation. Both involve some higher up in the hierarchy deciding that something needs to be done, either a task (delegation) or a recurring set of tasks (job description), and handing those off to an individual or a job role. Both delegation and job descriptions have a fragmenting effect: tasks get handed down to someone who probably does not have access to the larger picture, to the rationale and meaning for those tasks. And to someone who has no agency in deciding what tasks are important or necessary.

Quality within this aristocracy paradigm is whatever the small group of people in authority decides it is: the product owner, the Architecture Change Board, the CEO, etc. And on a process level: compliance officers, the most senior person on the team, the agile implementation team, etc. And I've seen it often enough that discussions don't go further than referring to one of those authorities: we have no idea why we should do this, we only know that we definitely have to. So we're firmly in the psychological cover and compliance area here.

### The machine paradigm
The machine paradigm looks at people as replaceable and interchangeable cogs in the machine. What matters is that your actions match the standardized instructions, that 'resources' have the required skill sets and that they get allocated correctly within the organization.

Typical practices for this paradigm are standards and procedures combined with metrics-based auditing. Standards and procedures provide precise descriptions of how people are expected to do the work so that it can be consistent in both execution and output. Metrics-based auditing then has you check whether an action has produced its expected, quantifiable output. Whether actions have also achieved their intended purpose is not evaluated. That's expected to be guaranteed by how the standards and procedures were made.

Within this paradigm you get quality by adhering to the standards, the processes and procedures. So the perfect example of psychological cover through being told how you have to do your job, and of compliance. For example, a good daily stand-up is one where everyone answers the three questions. A good testing process is one where every tester executes the required number of test cases per day. Or measuring lines of code, perhaps the oldest example of focusing on output instead of outcome and meaning.

### The behavioral paradigm
Instead of trying to control the process like the machine paradigm does, the behavioral paradigm tries to get people to behave in specific ways through a system of rewards and punishments. Internal, subjective experience is irrelevant; what matters are behaviors which can be observed and conditioned through that system of rewards and punishments.

A good example of this paradigm is how people's performance is usually managed. We provide incentives to encourage future behaviors and rewards to reinforce past behaviors. We provide recognition to certain individuals, both as a reward for them and as an example to others. Then once a year, people get rated against expectations and ranked in comparison to others. This feeds into your performance review, where someone tells you what you have done well and where you could improve. 

Similar to the two previous paradigms, the behavioral paradigm requires some authority to determine what quality is and to shape the system of rewards and punishments to control the behaviors of the people doing the work. This means we're still in the domain of compliance and psychological cover. And if the system of rewards and punishments is not clear, it might feel even less safe than the aristocracy or the machine paradigm. Also, the external motivation of rewards and punishments will displace whatever internal motivation that's present. Although it's possible to set up a wide variety of systems of rewards and punishment, based on the common practices in this paradigm, I think this paradigm most commonly leads to an organization where heroes are celebrated when they save the day, and where people try hard to score in front of their managers. You can't get rewarded if your manager doesn't see something to reward.

### The human potential paradigm
The human potential paradigm is a significant break with the previous three paradigms. It's built around the idea that human beings are inherently worthy. Instead of focusing on controls like the aristocracy, machine, and behavioral paradigms, the human potential paradigm focuses on self-direction. It's not about optimization, but actualization. People are not tools or means to an end; there's value in nurturing the potential in each person.

On a practices level, this paradigm will have a company adopt an institutional ideal of for example being a great place to work, getting input from its employees through surveys and participatory ideation. Their goal is to create a more hospitable work environment for human beings, paying attention to all their needs.

It may seem that adopting this paradigm will lead to psychological safety and commitment, but I don't think it's guaranteed. I can see this paradigm being used by someone as a reason to say: "I'm not being an asshole, I'm just speaking the truth as I see it." And I can see someone complying with an obligation to set annual learning goals instead of committing to them. This is something Carol Sanford brings up in her book: when you're steeped in the machine and behavioral paradigms, it's very easy to see "human development" as a new version of "performance". And in essence nothing much changes then.

The basis for quality in this paradigm is self-actualization and internal motivation. My focus is on what I can contribute, how I can grow and develop. So this where a team will start using a cool new tool, because they're interested in exploring it. How much consideration they have for their stakeholders, the organization, or even wider society and the environment, will vary. It's not truly a consideration in this paradigm.

### The regenerative paradigm
The regenerative paradigm is the main focus of Carol Sanford's book "The Regenerative Business", in which she describes what such a business looks like and how to transform your business into one. This paradigm is built around three core human capabilities. The first one is internal locus of control: people understanding that they have full responsibility for their actions, how they experience the world, and the outcomes they produce for themselves and others. The second one is external considering, caring deeply about something or someone in addition to ourselves. The third one is personal agency, the strong inner urge of people to be active players in the world, taking responsibility for manifesting the effects they want to create. These three come together in requesting employees to make a promise beyond ableness (so they're not able to do it yet) to something bigger than themselves.

As you might expect, the practices in a regenerative business are quite different from how most organisations operate. For example, no one serves as a boss over another person's work. Employees are expected to be self-managing, conscious of the whole of the business. There are no job descriptions. Roles evolve as the company evolves and these are self-defined and self-initiated. Pay does not increase with position or seniority. It increases as employees take on increasingly challenging and comprehensive improvements.

Since I don't have any experience with this paradigm, I find it hard to say much about what quality means in this paradigm. There's a focus on the development and expression of human potential, without forgetting that you want to run an effective business,  and without forgetting that there's a society and a world outside our business that we want to care for. As such, I find it hard to imagine you could have such a regenerative business without psychological safety or without commitment from the people involved.

### The reality of multiple paradigms being at play
Few (if any?) companies organize themselves based on one single paradigm. I suspect most of the time they end up with a mix of four or five of the paradigms, making it hard sometimes to see where one ends and the other begins. Take for example the W. Edwards Deming's quote: "People with targets and jobs dependent upon meeting them will probably meet the targets - even if they have to destroy the enterprise to do it." Assuming someone else set their targets for them, that's the aristocracy paradigm. Targets, often enough defined based on outputs, come from the machine paradigm. And the reward for meeting the target (or the punishment when you don’t) points to the behavior paradigm. Combine those three as in Deming's quote and you're unlikely to end up with quality.


## So now what?
And that concludes this third post in the series, having covered some rather big philosophical thoughts about value systems, the social nature of agreement, and different management paradigms. Although I see a lot of value in these kinds of thoughts, they are also something you can get stuck in, not sure where to start if you actually want to make something happen.

To counter that, I think it helps to take inspiration from Carol Sanford's three core human capabilities: internal locus of control, external considering, and personal agency. Do something small, and do something today - which I want to say a few things about in the fourth and final post in this series.
