<!--
.. title: Yet Another Testing Model: Value - Information - Processes - Tools
.. slug: yet-another-testing-model-value-information-processes-value
.. date: 2012-07-09 20:21:44 UTC+02:00
.. tags: VIPT, context-driven testing, models
.. category: philosophy of testing
.. link: 
.. description:
.. type: text
-->


During Let's Test 2012 some ideas clicked in my mind with the result of yet another testing model:
Value - Information - Processes - Tools.

For me this model really is a culmination of being part of the context-driven testing community. If you have been reading about context-driven testing, I'm sure you'll be able to spot plenty ideas I stole from others. ;-) So thank you so much to all of you!  
Secondly, I have trouble believing I am the first one to come up with this simple model - although a google search didn't turn up anything.[^1] So if any of you know of similar models, please leave a comment!

And now to the actual model. Since you can't have a model without a drawing, here's a not so spectacular one:

<!-- TEASER_END -->

<div class="d-flex justify-content-center">
	<figure class="figure w-50">
  	<img src="/images/2012/yatm-vipt/vipt.png" class="figure-img img-fluid rounded"
  	alt="VIPT diagram: value - Information - processes - tools"/>
	</figure>
</div>

Value is worth, usefulness.  
Information is thoughts, ideas, questions, etc.  
Processes are everything that happens: thinking, reading, talking, testing, etc.  
Tools are stuff. Pen and paper, requirements document, charters, heuristics cheat sheets, etc. And people are also tools (no pun intended)[^2].


## A simple example

Ok, now on to a simple example. Let's take a look at you reading this blog post.

This blog post is a tool, a communication tool. It's a specific configuration of pixels on a screen that can be interpreted as a set of letters in the Latin alphabet which can be read as a text in the English language.  
Which brings us to the process part: you reading and interpreting it. Without you doing this, this blog post is just a set of pixels. Without a process the tool doesn't do anything.  
This process results in you getting information: your interpretation of what I wrote and your ideas, thoughts and questions based on that interpretation.    
And hopefully this information is of value to you in some way.

That's all there is to it!


## A testing example: defect management

Let's continue with an example that actually has something to do with testing: defect management.
The most typical tool of defect management is the bug tracker. It can be an expensive tool, an open source-tool, a set of sticky notes or a list in your head. The processes involved are quite obvious: creating, reading and updating entries. The information (Remember that this information is not what's in the tool; it's an interpretation of what's in the tool.) consists of what the defects is about, its status, who is supposed to something with it, etc. Finally the value is keeping track of the defects: defects should be fixed and/or registered, not forgotten.

However, that's not the whole story. Keeping track of defects is of value, but we can also see it as a tool. By keeping track of the defects, we can analyse their current status. This gives us information about how the testing is going, how many issues there are with the product, what kind of issues there are and are not, etc. This information is valuable because it allows us to change our test approach if needed.
So as this example illustrates, often it's possible to build one VIPT pyramid on the other with the value becoming the tool.


## The tangible and the intangible

One of the most inmportant things to note about this model is that only tools can be actual things, objects. Processes are events; they occur. Some processes are observable; some are not. Information exists only in your mind. And so does value. Of course, you can use the tool of speech in a process of communication to share information about why you find this VIPT model valuable. But all I would get from that is the value of my interpration of what you said. I do not get your information or your value.

Or to put it differently. It's possible to share a tool: I can give you the requirements document. It's possible to partly share a process: we can review the requirements document together. It's possible to share filtered information: you can interpret what I say. It's possible to share translated value: I can tell you what I find valuable.  

So basically, what we care about is value, but all we really 'have' are tools. And to get from tools to value, we need to go through processes that generate information. This distance between tools and value can make a life as tester a bit complicated sometimes. This problem is what [part two](https://testingcurve.wordpress.com/2012/07/17/vipt-bottom-up-or-top-down/) of this post will be about.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2012/07/09/yet-another-testing-model-value-information-processes-value/).*


[^1]: This may have something to do with me heavily leaning on Kantian epistemology to simplify the model, though. (If you want to learn more about Kantian epistemology, reading Schopenhauer is a good start.)

[^2]: Of course one should remember Immanuel Kant's admonition here always to treat people as ends in themselves, never as mere means.