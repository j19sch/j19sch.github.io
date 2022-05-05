<!--
.. title: Thinking about quality: choosing your value system
.. slug: choosing-your-value-system
.. date: 2021-02-15 20:09:08 UTC+01:00
.. tags: peer conference, value systems, quality
.. category: quality
.. link: 
.. description:
.. type: text
-->

On 30 January 2021 I participated in the Quality Acceleration Peer Conference organized by Huib Schoots and Joost Voskuil. Participants were [Alan Page](https://twitter.com/alanpage), [Areti Panou](https://twitter.com/unremarkableQA), [Ash Winter](https://twitter.com/northern_tester), [Bart Knaack](https://twitter.com/btknaack), [Conor Fitzgerald](https://twitter.com/conorfi), [Rouke de Jong](https://twitter.com/roukedejong), [Gwen Diagram](https://twitter.com/gwendiagram), [George Dinwiddie](https://twitter.com/gdinwiddie), [Janet Gregory](https://twitter.com/janetgregoryca), [Joost Voskuil](https://twitter.com/joost_voskuil), [Joost van Wollingen](https://twitter.com/jpjwolli), [Martijn Meijering](https://twitter.com/mmeijeri), [Rob Meaney](https://twitter.com/robmeaney), [Vincent Wijnen](https://twitter.com/vinwijnl) - with [Huib Schoots](https://twitter.com/huibschoots) facilitating the peer conference. The main topics mentioned in the invite were: "How can you sell quality?", "How can you convince people that quality can accelerate software delivery?", and "What limitations or barriers do you hit?"

Reflecting during and after our discussions on these topics, I realized there are some interesting things going on about how we talk about quality and how to sell it. Enough interesting things to fill more than one blog post, so this will be a four-part series. And I might expand on some ideas in the series after that.


## Quality has two different meanings
On the one hand, we use quality when we talk about things that are obviously better. A [$3500 coffee grinder](https://www.youtube.com/watch?v=-3mB4MBITEI) is obviously better than [a £50 one](https://www.youtube.com/watch?v=AVYGxext8XI). An application that does not crash on you is obviously better than one that does. Almost all other ways to input your phone number are better than [these](https://qz.com/679782/programmers-imagine-the-most-ridiculous-ways-to-input-a-phone-number/).

<!-- TEASER_END -->

On the other hand we also say quality is in the eye of the beholder or that quality is value to a person who matters. Which requires us to explore who these stakeholders are and what qualities they value. What things are important to them when it comes to the product, the processes, the organization, the company, the people working for the company, the societal impact, the environmental impact, their own ethics and morality, their personal motivations, their own qualities and their own limitations, etc.

I don't think it's a problem that quality is one of the many words that has multiple meanings. I do think that the second definition leads to more interesting territory. The first one nudges us to focus only on product quality and in the direction of the devil's triangle of project management: time - cost - quality. And that raises the question: do you want to tackle this problem of quality on the project level? Or can you take a wider view than the current project, taking into account the product through its life cycle, the people working on it, the tools they're working with and the environment they are working in?

This first definition of quality also nudges you towards transactional thinking: you invest now in anticipation of future returns, or you take on debt now knowing it will need to be repaid in some way in the future.


## Alternatives to transactional thinking about quality
A lot of our talk about quality is framed in transactions: investment and debt, doing thing A (payment, debt) to get thing B (return, benefit). This makes sense. If you work for a for-profit company, regardless what goods or services it provides, you're also in the money-making business.

A different but related perspective that I see popping up in discussions about quality is consequentialism: evaluating actions based on their consequences. We should have unit tests so we can maintain velocity in the longer run. We have to release this in the next three months or we'll miss our entry in the market.

What these two perspectives, transactional thinking and consequentialism, have in common is that decisions are made based on the expected outcomes. You compare (if not explicitly, then implicitly) different versions of the future based on actions you take now. This is also where weighing pros and cons, and balancing priorities come in. The underlying idea is that we can score everything on a big balance sheet and that will tell us what the best course of action is.

However, there are other perspectives to base decisions on, to base value judgments on. You can also base decisions on rules or on what's virtuous.

In a rule-based (aka deontological) value system, the value of an action is not determined by its consequences, but by whether it adheres to a certain set of rules. For instance, a team might have the rule that if your commit makes the build go red, you have 15 minutes to fix it, or your commit gets reverted. So if you make the build go red, there's no discussion about the pros and cons of fixing it in 15 minutes versus taking more time. You follow the rule. You either fix the problem in 15 minutes, or you revert your commit. A convenient aspect of such a rule-based system is that often it can be applied automatically by our tools - as is the case for this example.

A second alternative is a virtue-based value system. Virtue is not about consequences or about rules, it's about the positive characteristics of a person or a team. An example of such a system are the Extreme Programming values of communication, simplicity, feedback, courage, and respect. So you find yourself comparing different ways to build something and you go with the simplest one, because simplicity. Again, no discussion about pros and cons. And also, no following a rule that says to always pick the simplest option. Rather, you see simplicity as a virtue, something that needs to be nurtured in who you are and how you work.


## Choosing your value system
Comparing these three types of values systems (consequentialism, rules, and virtue) I must say that I feel more comfortable with the consequentialist argument than with the ones based on rules or virtue. Those two leave me with questions like: "But why have a rule that says to write unit tests?" and "But why is unit testing a virtue for programmers?" However, the consequentialist argument isn't stronger per se, since it requires you to predict the future: if we (this specific group of individuals in our specific context) have unit tests, we will be able to maintain velocity in the longer term. That kind of fortune telling will work in [Cynefin](https://en.wikipedia.org/wiki/Cynefin_framework)'s obvious/clear domain, might work in its complicated domain, and won't work in the complex domain.

In addition to the above abstract comparison of what kind of reasoning you are more comfortable with, it's interesting to think about what kind of value system you apply in what situations. For instance, assuming you're in favor of diversity in teams, why is that? Because you value diversity and equal opportunity? Or because studies show that diverse teams are more effective and productive?

Or, if you could increase your company's revenue by a million at the cost of one employee burning out, would you? And if not, what about five million? Or is there no such number, because no amount of money is worth even one person having a burnout? Yet, if you believe that, are you and your company doing enough to prevent burnout?

These questions don't have easy answers and there's a good chance they don't have answers at all. So my suggestion to you: once in a while after making a decision impacting quality, reflect on what kind of value system you used. Was that decision, that value judgement, based on consequences, rules, or virtue? And was that the right way to make this decision? Which ironically is a value judgement on its own.
