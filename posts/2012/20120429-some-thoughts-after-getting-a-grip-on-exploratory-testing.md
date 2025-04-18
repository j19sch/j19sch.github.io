<!--
.. title: Some thoughts after attending the 'Getting a Grip on Exploratory Testing' workshop
.. slug: some-thoughts-after-attending-the-getting-a-grip-on-exploratory-testing-workshop
.. date: 2012-04-29 19:55:30 UTC+02:00
.. tags: exploratory testing, workshop, software testing
.. category: exploratory testing
.. link: 
.. description:
.. type: text
-->

About two weeks ago I attended [James Lyndsay](http://www.workroom-productions.com/)'s 'Getting a Grip on Exploratory Testing' workshop in Amsterdam. So it's about time to write something about it…

Now one of the things I dislike about workshop blog posts is that people will say "It was great! And person X is such a good trainer!" without saying much about the content of the workshop. However, I find myself now writing this post and thinking: I shouldn't post a full summary of the workshop. Not that it would spoil too much for any future attendee: most of the workshop consists of exercises and discussion. But posting a summary of the workshop that James has put a lot of effort in to create, just doesn't feel right. So let me just say this: the workshop was great and James is such a good trainer! :-D

Now that's out of the way, there are a few things from the workshop I'd like to share. Of course, the usual disclaimer applies: these are my thoughts on what was presented during the workshop. Any misrepresentations are my responsibility.

<!-- TEASER_END -->

## Exploratory testing styles
First of all, style. Different people have different styles of exploratory testing. Your style influences how you test, what you find, when you find it, etc. For example, some elements of my own style are:  

- tendency to exceed the time box.  
- explores with about three variations before moving on to something else.  
- takes a lot of notes.

Before the workshop I thought a style was like an approach. People prefer certain styles/approaches, but if their current one is failing them, they can switch to a different one. Turns out is's not that simple. Style is very much like your personality and you don't switch those easily either.

That does not mean it's not a good thing to know what your style is like. Your style is an important part of how your mind works. Your mind is probably the most important testing tool you have. And as any craftsman can tell you: a good craftsman needs an excellent understanding of his tools. So knowing your style is important. Not just for when you're testing by yourself, but also when you decide to team up with someone. Do you want to team up with someone with a similar style or with someone whose style complements your own?


## Weapon of choice
Secondly, one small, but cool thing that came up was the 'weapon of choice' of a tester. (Which reminded me of a scene from a movie I can't remember the title of. Two gentlemen are about to fight a duel. One says: "Choose your weapon: sword or pistol." The other one: "I choose the sword." To which the first one replies: "Fine, then I will take the pistol.") Anyhow, if you were stranded on some desert island and had to do some software testing: which testing tool would you take with you? That tool is your 'weapon of choice'. For me at the moment it's Notepad++. I have my notes and to do-list in there. And I spend a lot of time with xmls, which Notepad++ does quite nicely with the proper plug-in.


## Discovering value vs discovering problems
Finally, perhaps the most important thing I learned is a simple model about exploratory vs. scripted testing:

- Scripted testing starts from what is expected. It is focused on discovering value.  
- Exploratory testing starts from what is delivered. It is focused on discovering problems.  

In some contexts this model may be too simple, but for me it really helps as a starting point to think about how one can fit scripted and exploratory testing into a test strategy.

This model has also helped me to explain exploratory testing to people and especially to people that approach testing in the traditional way, i.e. like TMap and ISTQB do. These people often think of exploratory testing as one of the many testing techniques at their disposal. So exploratory testing is not seen as having a fundamentally different approach from scripted testing. Rather, exploratory testing is something you can do besides e.g. decision table testing or use case testing.  

The reason for this (in my opinion) is that these traditional methods reduce testing to showing that what has been delivered meets a certain set of expectations – be it specifications, use cases or requirements. This covers both the 'verification' part (Did we build the product right?) and the 'validation' part (Did we build the right product?) of testing. If that is all there is to testing, it's hard to see what's so great about exploratory testing. It's what you do when you don't have enough information to use any of the other (better) techniques.

So if you want to explain exploratory testing to someone with this traditional view on testing, you'll first have to change their mindset. Show them there is more to testing. And please do that before you start talking about sessions and charters and debriefings and all that other stuff. First show them that there is another purpose to testing: investigating what has been delivered in search of problems (and/or surprises). Make them see the context in which you apply exploratory testing. With that done, it will be so much easier to explain what exploratory testing is.

---

*This post was originally published on my old blog.*