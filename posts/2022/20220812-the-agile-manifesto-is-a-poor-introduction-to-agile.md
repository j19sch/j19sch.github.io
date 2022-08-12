<!--
.. title: The Agile Manifesto is a poor introduction to Agile
.. slug: the-agile-manifesto-is-a-poor-introduction-to-agile
.. date: 2022-08-12 09:37:25 UTC+02:00
.. tags: agile, agile manifesto, mētis, teaching
.. category: agile
.. link: 
.. description: 
.. type: text
-->

Last week [Elizabeth Zagroba](https://twitter.com/ezagroba) [asked on Twitter](https://twitter.com/ezagroba/status/1557608861690912772):

> If someone was completely new to working on software on an Agile team, what would you want them to read about Agile first?

My first thought was: "The Agile Manifesto!" After a second thought, though, I reconsidered and [replied](https://twitter.com/j19sch/status/1557650105930579968):

> And I would recommend against reading the Agile Manifesto without consulting any secondary sources, except if you read it in the same way as you would visit a historical site "just to see where it all happened".

As I wrote this, I could not really put my finger on why exactly I felt this way. The best I could come up with was that the Agile Manifesto is hard to understand on its own. You need some historical context and practical experience to make sense of it. Serendipity came to the rescue, though, as I'm currently reading [*Seeing Like a State*](https://en.wikipedia.org/wiki/Seeing_Like_a_State) by [James C. Scott](https://en.wikipedia.org/wiki/James_C._Scott). Chapter 9 of the book focuses on the Greek concept of *mētis* (μῆτις) and how it relates to rules of thumb. Turns out that this explains why the Agile Manifesto is a poor introduction to Agile.

<!-- TEASER_END -->



# Mētis and rules of thumb

*Chapter 9. Thin Simplifications and Practical Knowledge: Mētis* of the book explains[^1] mētis as follows:

> The concept comes to us from the ancient Greeks. Odysseus was frequently praised for having mētis in abundance and for using it to outwit his enemies and make his way home. Mētis is typically translated into English as "cunning" or "cunning intelligence." While not wrong, this translation fails to do justice to the range of knowledge and skills represented by mētis. __Broadly understood, mētis represents a wide array of practical skills and acquired intelligence in responding to a constantly changing natural and human environment.__ Odysseus's mētis was in evidence, not only in his deceiving of Circe, the Cyclops, and Polyphemus and in binding himself to the mast to avoid the Sirens, but also in holding his men together, in repairing his ship, and in improvising tactics to get his men out of one tight spot after another. The emphasis is both on Odysseus's ability to adapt successfully to a constantly shifting situation and on his capacity to understand, and hence outwit, his human and divine adversaries. *(p. 313) [emphasis mine]*

[^1]: The author bases his explanation on "Cunning Intelligence in Greek Culture and Society" by Marcel Detienne and Jean-Pierre Vernant, trans. Janet Lloyd (Atlantic Highlands, N.J.: Humanities Press, 1978), originally published in French as "Les ruses d’intelligence: La mētis des grecs" (Paris: Flammarion, 1974)

He then explains the relation between mētis and general rules of thumb:

> Even the part of mētis that can be conveyed by rules of thumb is the codification of practical experience. (p. 330) Taking language as a parallel, I believe that the rule of thumb is akin to formal grammar, whereas mētis is more like actual speech. __Mētis is no more derivative of general rules than speech is derivative of grammar.__ *(p. 319) [emphasis mine]*

This means that these general rules of thumb on their own are insufficient for success in practice:

> The generic formula does not and cannot supply the local knowledge that will allow a successful translation of the necessarily crude general understandings to successful, nuanced, local applications. __The more general the rules, the more they require in the way of translation if they are to be locally successful.__ *(p. 318) [emphasis mine]*

Which has James C. Scott asking the question: "Why are the rules of thumb that can be derived from any skilled craft still woefully inadequate to its practice?" He answers his own question as follows:

> Knowing a craft's shorthand rules is a very long way from its accomplished performance: "These rules and principles are mere abridgements of the activity itself; they do not exist in advance of the activity, they cannot properly be said to govern it and they cannot provide the impetus of the activity. A complete mastery of the principles may exist alongside a complete inability to pursue the activity to which they refer, for __the pursuit of the activity does not consist in the application of these principles; and even if it did, the knowledge of how to apply them (the knowledge of actually pursuing the activity) is not given in a knowledge of them__."[^2] *(p. 316) [emphasis mine]*

[^2]: "Rationalism in Politics and Other Essays", Michael Oakeshott (New York: Basic Books, 1962)



# The Agile Manifesto as rules of thumb based on mētis

All of the above, in my opinion, applies to Agile software development and the Agile Manifesto. The Manifesto are rules of thumb codified by its authors based on their mētis of lightweight methods of developing software.

As [Alistair Cockburn tells it](https://youtu.be/fG6N-QNDblM?t=2677) in *3 Decades of History and Stories about Agile with Alistair Cockburn*, the 2001 gathering in Snowbird that resulted in the Manifesto, started with a short opening statement by Bob Martin. In that statement Bob Martin said that he invited everyone because even though they have some differences, he also believed they have something in common. So it would be good to write a manifesto, since a rising tide raises all boats.

So who were these invitees and what had they been doing? They were representatives of several lightweight methods that were created in the '90s: Adaptive Software Development, Crystal, Extreme Programming (XP), Pragmatic Programming (PP), and Scrum. As Alistair Cockburn says [earlier in that same video](https://youtu.be/fG6N-QNDblM?t=1280):

> We didn't have to make up stuff. We had been doing stuff, for all of us, for five, eight, ten years, whatever the number might have been.

Which is also reflected by the start of [the Manifesto](https://agilemanifesto.org/):

> We are uncovering better ways of developing software by doing it and helping others do it. Through this work we have come to value: [...]

So it was the mētis acquired by these 17 people, that got codified into the Agile Manifesto as four values and twelve principles, i.e. as general rules of thumb. As mentioned above, these general rules require a translation based on local knowledge if they are to be applied successfully. And the more general the rule, the more translation is required. The Agile Manifesto is a set of very general rules, since they codify the rules of thumb common to five lightweight methods, each of which is already a codification of the mētis of its creators. In that sense, the Manifesto is twice removed from actual practice.

This to me is the reason why the Agile Manifesto is not a good introduction to Agile. The translation from the Manifesto to someone's own circumstances is too great for someone who is looking for an introduction to the topic. This is I think not only true when it comes to applying the Manifesto in practice. It already comes into play when trying to understand on a conceptual level what the Manifesto is saying. The only reason I would share the Manifesto is as a historical document. To show it and say: "This is the origin of Agile."



# So how do you introduce someone to Agile?
If not through the Agile Manifesto, then how do you introduce Agile? Next to my comment about the Manifesto, I [replied this](https://twitter.com/j19sch/status/1557618194927476736) to Elizabeth's question:

> First [https://www.jamesshore.com/v2/books/aoad2/what_is_agile](https://www.jamesshore.com/v2/books/aoad2/what_is_agile) to get the big picture, then "Agile Conversations" by Douglas Squirrel and Jeffrey Fredrick, so they can have good conversations with colleagues about how to agile.

That link leads to the first chapter of [*The Art of Agile Software Development (2nd ed)*](https://www.jamesshore.com/v2/books/aoad2) by [James Shore](https://twitter.com/jamesshore). The chapter does reproduce the Manifesto, but it also explains what it means. It provides historical context. It explains why Agile won, why it works, and why it fails. As far as short introductions go, I think it's hard to do much better. And for anyone who wants a more in-depth introduction, there are the remaining 470 pages of the book.

Yet another way to introduce people to Agile would be to not spend much time on it at all. Give a brief historical overview by mentioning the heavyweight methods of the '70s-'80s-'90s, the lightweight methods of the '90s, and the resulting Agile Manifesto of 2001. Explain that a lot has happened in the 20+ years since. Agile has been used and misused in a multitude of ways. There's also DevOps and Lean now. With everyone (or close to it) claiming to be Agile now, there's not much use in worrying about what is or isn't Agile. These days, it's basically a synonym for software development. And if despite that, you're still curious, go read some of the articles listed at [Context of Agile](https://context-of-agile.org/). *(Disclaimer: I own that site.)*
