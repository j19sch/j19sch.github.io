<!--
.. title: Four skills for the four Agile values
.. slug: four-skills-for-the-four-agile-values
.. date: 2022-02-04 22:04:06 UTC+01:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
-->

Different title:

- to embody
- to support
- as a foundation to

Also update last paragraph of the Scrum/XP section.

My initial idea for this blog post was to include an updated version of the Agile Manifesto in the format of *"x over y through z"*. That's probably too early. And I'm not sure about either the four values or the four skills.

---

If you're familiar with the [Agile Manifesto](https://agilemanifesto.org/), you're familiar with its four values:

- Individuals and interactions over processes and tools
- Working software over comprehensive documentation
- Customer collaboration over contract negotiation
- Responding to change over following a plan

Which makes me wonder: how do you apply these values? How do you live and embody them? Since I was not able to find any guidance on this, I decided for myself which skill can support each of these four values.

<!-- TEASER_END -->

# What do Scrum and XP say about this?

As a start, I decided to look at how Scrum and XP[^1] approach this - even though they have their own different sets of values.

The [Scrum Guide](https://scrumguides.org/scrum-guide.html#scrum-values) says:
> Successful use of Scrum depends on people becoming more proficient in living five values: *Commitment, Focus, Openness, Respect, and Courage*.

Followed by two paragraphs desribing what that would (should?) look like. It never gets specific, though, with the explanation of "commitment" being *"The Scrum Team commits to achieving its goals and to supporting each other."*

*Extreme Programming Explained (2nd ed.)* has the following to say about its values (communication, simplicity, feedback, courage, respect) and practices[^3] in chapter 3:
> Values are the large-scale criteria we use to judge what we see, think, and do.

> Practices are evidence of values. Values are expressed at such a high level that I could do just about anything in the name of a value.

> Just as values bring purpose to practices, practices bring accountability to values. [Because it's clear if you are following a practice.]

Unfortunately, neither Scrum or XP provided me with what I was looking for. Both of them recognize courage as a value, but provide no guidance on how to be courageous[^4]. And that's the thing I'm curious about, although today with respect to the values of the Agile Manifesto. What skills do I need to value individuals and interactions over processes and tools? How should my mind work, how can I practice to allow me to bring that value to life?

After giving it some thought, I decided the four following skills support the four values of the Agile Manifesto:

- Choosing to perform interpretive labor
- Detaching
- Daring greatly
- Flowing with the go


# Choosing to perform interpretive labor

In "[The Utopia of Rules](https://en.wikipedia.org/wiki/The_Utopia_of_Rules)" [David Graeber](https://en.wikipedia.org/wiki/David_Graeber) writes[^7]:

> "Most of us are capable of getting a superficial sense of what others are thinking or feeling just by observing their tone of voice, or body language - it's usually not hard to get a sense of people's immediate intentions and motives, but going beyond the superficial often takes a great deal of work. Much of the everyday business of social life, in fact, consists in trying to decipher others' motives and perceptions. Let us call this "interpretive labor". One might say, those relying on the fear of force are not obliged to engage in a lot of interpretative labor, and thus, generally speaking, they do not." (p66-67)

That last sentence reminds of the disctincion in types of power made by Just Associates[^8] in "[Making ChangE haPPEn: POWER](https://justassociates.org/wp-content/uploads/2020/08/mch3_2011_final_0.pdf)": Power Over, Power With, Power To, and Power Within. Power Over does not require you to perform interpretive labor; Power With does.

In software development we see Power Over in the processes and tools. More so when they are mandated from above, but also still when they were chosen by the team. A process or a tool on their own cannot perform interpretive labor. That requires a human being who chooses to perform that labor, who chooses to interact with other human beings to try to understand them and where they are. So to embody the value of **individuals and interactions over processes and tools** we need the skill to choose to perform interpretive labor even when we have the option of using our Power Over instead.


# Detaching / Defocusing

**Working software over comprehensive documentation**

## Cockburn

Alistair Cockbur, Agile Software Development, The Cooperative Game Principle:

> Software development is a (resource-limited) cooperative game of invention and communication. The primary goal of the game is to deliver useful, working software. The secondary goal, the residue of the game, is to set up for the next game. The next game may be to alter or replace the system or to create a neighbouring system. (p 31)


# Daring greatly

**Customer collaboration over contract negotiation**

# Flowing with the go

In the 1995 documentary "Choke", one of the greats of [Brazilian Jiu-Jitsu](https://en.wikipedia.org/wiki/Brazilian_jiu-jitsu), [Rickson Gracie](https://en.wikipedia.org/wiki/Rickson_Gracie) says:

> "You don't know exactly where you're going, until the movement happen, because you cannot anticipate what's gonna happen. You must allow yourself to be in a zero point, in a neutral point and be relax [sic] and connected with the variations. So you pretty much flow with the go." ([1:00 - 1:22](https://youtu.be/QtBLhYB6Muk?t=60))

What this means is that when you're grappling, you can't make things happen directly. You're not in full control, because your opponent has their own plans. While you are trying to submit them, they are trying to submit you. So going straight for a submission (a joint lock or a choke) is very rarely a good plan. Instead, you flow with your opponent, adapt to what they are doing, exploiting openings to continuously improve your position, i.e. move to a position where you have more/better options[^5] and your opponent has fewer/worse ones. As you do that, opportunities for submissions will present themselves for you to take. As the BJJ saying goes: *"Position before submission."*

Then Rickson Gracie continues:
> "This is a point beyond the knowledge. It is years of [sic] years of playing around, giving you this kind of sensibility." ([1:24 - 1:32](https://youtu.be/QtBLhYB6Muk?t=84))

I include that quote, because what he's saying here is that *"flow with the go"* is a skill. It's something you can learn through practice. And I'm curious if Rickson Gracie (or anyone for that matter) has developed a way of teaching it actively[^6], instead of solely relying on years and years of playing around.

I think we need a similar skill in software development for **responding to change over following a plan**.





[^1]: Although those are the two most well-known Agile methodologies, they are not the only ones. I looked up some of the others, but none seem to list a set of values. DSDM has eight principles. The Crystal family has three properties: safety in project outcome, efficiency in development, habitability of the conventions. Adaptive Software Development does not seem to have any overarching principles.[^2] It might actually be an intersting research project to look into the distinction between values, principles, and properties across these methodologies.

[^2]: While looking all of this up, I found an [interesting article by Dirk Riehle]((https://riehle.org/computer-science/research/2000/xp-2000.pdf)): *"A Comparison of the Value Systems of Adaptive Software Development and Extreme Programming: How Methodologies May Learn from Each Other"*

[^3]: Next to values and practices, XP also identifies 14 principles: *"Bridging the gap between values and practices are principles."*

[^4]: I suspect a similar problem is at play with "agile mindset". The agile mindset is a [thought process](https://www.atlassian.com/agile/advantage/agile-mindset), a [set of attitudes](https://www.infoq.com/articles/what-agile-mindset/), or a [culture that you implement](https://www.agile-scrum.be/agile-software-development/agile-mindset/) with the incentive to accept or adopt the cultural norms. The problem seems to me a Cartesian separation of thinking and doing, where 'correct' thinking will lead to correct action. While thinking is also an action, involving intellectual, emotional, ethical, ... skills.

[^5]: I wrote something similar for the last paragraph of my post "[Thinking about quality: so what to do?](link://slug/thinking-about-quality-so-what-to-do)":  
*"All these aspects I've summarized for myself as: managing a network of tensions. You are a node in a network of tensions and you take small steps to influence those tensions towards configurations that align with your hopes, dreams, and intentions, with your horizon. And that game, that art, those skills, are what I think of when I say "Do something small, and do something today."*

[^6]: I might need to do a follow-up post about skill development based on this post and "[An approach to teaching Agile 20 years after the Agile Manifesto](link://slug//an-approach-to-teaching-agile-20-years-after-the-agile-manifesto)", in which I said:  
*"Software development is not an easy problem to solve, let alone teaching the skills that enable you to solve it. But I do believe this approach [noticing - options - principles] has a good chance of helping people to acquire that skill set and to deal confidently and comfortably with whatever situation, team, and organization they find themselves in."*

[^7]: On page 70, he also writes: *"Nothing I am saying here is particularly new to anyone familiar with Feminist Standpoint Theory or Critical Race Studies."* And on page 103: *"[...], I was actually unware that most of these ideas has already been developed within feminist standpoint theory. That theory itself has been so marginalized I was only vaguely aware of it."*

[^8]: The social activist angle of Agile has been labeled as "Team-Scale Anarcho-Syndicalism" by Brian Marick in his talk "[Artisanal Retro-Futurism Team-Scale Anarcho-Syndicalism](https://www.youtube.com/watch?v=T5yv-WcQ4wY)". In a [blog post on the same topic](http://arxta.net/explanation.html), he writes: *"Anarcho-syndicalism’s concentration on the self-organization and solidarity of the people whose hands and minds make the product is reminiscent of Agile at its best."* and *"We are also taken by anarcho-syndicalism’s emphasis on direct action."*
