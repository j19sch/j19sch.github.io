<!--
.. title: VIPT - bottom-up or top-down
.. slug: vipt-bottom-up-or-top-down
.. date: 2012-07-17 20:02:42 UTC+02:00
.. tags: VIPT, context-driven testing, models
.. category: philosophy of testing
.. link: 
.. description:
.. type: text
-->

In this second post on VIPT I want to talk about bottom-up vs. top-down. The original plan for this post was to talk about the distance between tools and value, but in the past few days I figured out that bottom-up vs. top-down is a better approach.
If you don't know what VIPT is, please read [this previous post](link://slug/yet-another-testing-model-value-information-processes-value). Don't worry, I'll wait.

## VIPT is a top-down model

For me as a context-driven tester the VIPT model is very much a top-down thing. You analyze the context, find out what value you should/can deliver and then you proceed to information, processes and tools. Of course, that's easier said than done. Going through this for everything you do, requires a lot of time and effort. So most of the time you do quick analysis of the context, decide that it sufficiently resembles a context you encountered earlier and you use the same tools you used then. Most of the time that's ok - as long as you stay alert to any signs that you misread the context.[^1]

<!-- TEASER_END -->


## Dangers of using VIPT as a bottom-up model

Now what if you have a tool and you used it in several contexts with a sufficient amount of success? You might be tempted to conclude the tool will work in all contexts. It has worked so far, hasn't it? 

### The danger of best practices

Congratulations, you just created a best practice! This also means in regard to VIPT you have gone from a top-down approach to a bottom-up one. Instead of taking value as a starting point, you start with a tool, on the assumption it will deliver the same value as it did in previous cases. Chances are small you will notice any indications your tool does not fit the context until it's too late.

At best, you will see signs of the gap between tool and context and attempt to fix it. However, because of the bottom-up approach, you will not be looking at how to optimize the value you generate, you will focus on optimizing your tool. And this doesn't just apply to best practices. You run this risk anytime you approach VIPT bottom-up instead of top-down.

### The danger of local optimization
Let's say you have a tool that results in a sufficient amount of success and you decide to improve the tool. Say hello to the problem of local optimization.

Imagine that we make a map of all testing tools and express the value they generate (in your context) by raising the surface of the map in proportion to the value they generate. Basically, you get a mountainous region of testing tools with the highest mountain being the best tool. You are already using a tool, so you are on one of these mountains. If the only thing you do, is climbing up that same mountain, i.e. optimizing your tool, you will never be able to rise beyond the top of the mountain you're currently on. And what if that mountain is not high enough?

The only solution to this is to also descend once in a while. Explore the region and get to know the different mountains. It will make it easier to recognize when your current tool just won't be enough for the job at hand.

### The danger of using a tool to enforce process
Another problem with the bottom-up approach is that it makes it tempting to use a tool to force a certain process, assuming this will ensure you get the information and value you want.  

A great example of this are defect management tools. More specifically, defect management tools that assign different roles with different privileges to different users. For instance, only developers can change the status of a defect from 'in analysis' to 'fixed' to 'ready for test'. This means first of all that going straight from 'in analysis' to 'ready for test' is not possible. You have to click through 'fixed' first. Secondly, this cannot be done by a tester or a designer; it needs to be done by a developer. Luckily, most of the time these tools are accompanied by a process flow diagram. Otherwise you'd first have to map out this maze of privileges before you can actually actually use the tool.  

Now it's not that hard to imagine why you would configure your tool like that. You want to keep proper track of defects. So you want to have correct information. This means that certain processes need to be followed. So you get a tool to facilitate this. And then you realize that people may make mistakes or that people take short cuts to make life easier for themselves. So you configure the tool not only to facilitate the processes you want, but also to enforce them. This does not work. Like the internet does with censorship, people see it as damage and route around it. Your plan backfires and instead of good, you get awfull information in your bug tracking tool.

I was supposed to say a few things about teaching testing in relation to VIPT, but I'm saving that for the [next post](link://slug/vipt-how-to-teach-software-testing).

---

*This post was originally published on my old blog.*


[^1]: This is a really good moment to go and read Iain McCowatt's latest blog post "[Doctor, Doctor](http://exploringuncertainty.com/blog/archives/860)", by the way. It's about how testers make decisions.