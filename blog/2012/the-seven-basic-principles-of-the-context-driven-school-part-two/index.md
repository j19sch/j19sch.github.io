<!--
.. title: The Seven Basic Principles of the Context-Driven School - part two
.. slug: the-seven-basic-principles-of-the-context-driven-school-part-two
.. date: 2012-02-05 21:51:01 UTC+01:00
.. tags: context-driven testing, software testing
.. category: philosophy of testing
.. link: 
.. description:
.. type: text
-->

After the introductory post (to be found [here](https://testingcurve.wordpress.com/2012/01/15/the-seven-basic-principles-of-the-context-driven-school-part-one/)) it's time to take a closer look at each of [the basic principles](http://www.context-driven-testing.com/). In the past weeks I found out that it's quite possible to take any one of these principles as a starting point for several different trains of thought. More importantly I discovered a story[^1] to the principles: the first five principles are ways in which software testing is intellectually challenging, as stated by principle six. And principle seven then wraps it all up.
So below you can find some of the thoughts I had on the principles and the story I discovered.

### 1. The value of any practice depends on its context.
To get a better understanding of this principle I started thinking: what if the value of a practice did not depend on context? What else coud it depend on?

<!-- TEASER_END -->

One possibility is that practices have an intrinsic value. If that's the case, how can we compare two practices to see which one has the most intrinsic value? Should we look at elegance, simplicity, completeness, ... [^2] ? The problem is that those are not the usual criteria we judge a practice on. Since a practice is something that requires application, it does not stand on itself for us to enjoy its intrinsic value. So the value of a practice depening on intrinsic value makes little sense. Although I do think it's something people take into account: a good method also needs a good story. It needs to be convincing.

Another possibility is that pracitices do not have any value: it doesn't really matter what you do. Or that there is no way for us to discern the differences in value - even in hindsight. As a consequence it does not matter what you do, because you will never know if you could have done any better. If that were the case, software testing would be the easiest job in the world and the most ridiculous. Of course, often it is difficult to choose between different practices, but the choices you make do matter.

So these two alternatives are not complete nonsense, but in the end they do not (or at least should not) determine the value of a practice. The context does. But are all software testing contexts sufficiently alike so that we only need one practice? To answer this we need to look at the second princple.

### 2. There are good practices in context, but there are no best practices.
If there are good practices in context, there are also bad practices. Secondly, there are no best practices - 'best' implying context-independence here. Remains the question: are there better practices? Are some practices better than others? Outside of any context, there cannot be. Otherwise the one practice that is better than all the rest would be the best practice. In context, obviously, some practices are better than others. And to take the point even further: what is a good practice on one context, may be a bad practice in a different context. Which is kind of a weird thought if you're used to thinking in best practices and maturity models.

Another thing I wondered is if there are ways around this principle. I could think of two. Unfortunately neither work.

Firstly, there are 'best' practices, i.e. best practices applied with some adaptivity. So you apply your best practices and where it doesn't work you patch it up by getting creative. The problem with this workaround is that you will always maintain the basic philosophy of your practice. So in the details your approach may not be one-size-fits-all, the fundamental parts of your approach will be. You will approach every problem from the same perspective. This makes you context-conscious, but not context-driven.

The other workaround is creating a practice that is abstract enough that it's context-independent. I don't think that's possible. Sure, it is possible to define a set of principles that is abstract enough. Just look at these seven principles. But I don't see how one could create a practice that is abstract enough to be context-independent, yet concrete enough to have any practical value.

### 3. People, working together, are the most important part of any project's context.
What does 'working together' mean? Are factory workers at a production line working together? Or does it depend on the degree of communication and interaction between them? On a shared goal, a shared understanding of what they are doing and of what they are trying to accomplish? I think it does. Working at the same production line or being assigned to the same project, does not mean you are 'working together'. So the most important part of a project's context is the ways in which the people in the project interact with each other. And remember, you are one of those people.

Also, because the value of a practice is determined by context, these interactions are what the value of your testing practice depends upon. This also means that the following parts of a project's context are less important to the value of your practice: deliverables, processes, the type of product, laws and regulations, the project management method, the planning, etc.

### 4. Projects unfold over time in ways that are often not predictable.
My first reaction to this one was "Well... duh!" My second reaction was "But what do we do with this knowledge?" Which got me to my third reaction "What does 'not predictable' mean?"

Well, we all know that unexpected stuff happens and that's why we add an error margin to our budget and our planning. We may not be able to predict exactly which tasks are going to eat up our error margin, but we can make a fair guess how much error margin we need. Often enough that guess is wrong, but luckily the project plan and the project itself are not two seperate entities. Changing the plan changes the project and vice-versa. As a result this kind of being not predictable is manageable to some degree.

Yet the above is not what we should think about to understand this fourth principle. What we should think about is that our model of the project might be wrong. Something that happens and does not fit into your model, is truely 'not predictable'. Which is different from 'hard to estimate'. (See the idea of black swans and the known unknown vs the unknown unknown, or this set of blog posts by Michael Bolton.) Now why would our model be wrong? Assuming we're not clinging on to some best practice, in most cases I think it's simply a case of having several models fitting the observations of the project so far. So there is just no way of deciding which of these models is the correct one. Hopefully, as the project progresses, we stay alert and will be able to discard the models that no longer fit our observations.

### 5. The product is a solution. If the problem isn't solved, the product doesn't work.
The easiest interpretation here is saying this principle is about verification (Did we build the product right?) versus validation (Did we build the right product?). As a consequence, delivering a product that meets all documented requirements on time and on budget, does not mean it's a good product. One could argue that it was a well-managed project that produced this product, but does that really matter if the product is no good? Probably not.

A more difficult question is who gets to define the problem. One way to look at it is that everyone with access to information about the problem, defines the problem by building a mental model about the problem. However, none of the models are the definitive model. So another way to look at it is that nobody gets to define the problem. And that is (at least to me) the fun part of testing: you are being challenged to build two sets of models. One set about the problem and one set about the solution; comparing those with eachother is what we call 'testing'.


### 6. Good software testing is a challenging intellectual process.
The main implication of this principle is that good software testing is not defined by following a method, going through the test process step by pre-defined step. It is defined by exploration, investigation and learning.

And as I said above, one way to look at the principles is to see the first five principles as ways in which software testing is intellectually challenging:  
1\. Understanding the context of a project.  
2\. Deciding which practice to use in a specific context.  
3\. Interacting succesfully with people.  
4\. Building and evaluating models of the project.  
5\. Evaluating if the product solves the problem.  
Those are the five skills you need to be a good software tester.

### 7. Only through judgment and skill, exercised cooperatively throughout the entire project, are we able to do the right things at the right times to effectively test our products.
This last principle wraps it all up, referring to the other principles: judgment and skill (principle 6), cooperatively (principle 3), right things (principle 1 and 2), right times (principle 4), to efectively test our products (principle 5). And last but not least, 'throughout the entire project' implies there is no testing phase.

That concludes part two. In part three I will use these principles to compare the Context-driven school with the other schools of testing.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2012/02/05/the-seven-basic-principles-of-the-context-driven-school-part-two/).*

[^1]: There's a reason I say 'story'. Stories are great ways to make sense of things, but they can also be deceptive. People like stories, but not everything allows to be 'storified' without losing important bits.
[^2]: I know, one can argue none of those are actual indicators of intrinsic value. Elegant/simple/complete to whom?