<!--
.. title: Cooking analogy
.. slug: cooking-analogy
.. date: 2023-03-10 13:12:25 UTC+01:00
.. tags: tools, test automation, metrics
.. category: metrics
.. link: 
.. description: 
.. type: text
-->

A few weeks ago someone suggested we should start measuring how many automated test cases we have versus how many manual test cases. Luckily it was part of a longer list of suggested metrics and it was also presented in that way: a list of possibilities, to be discussed later. And I say "luckily", because I know I disagree with using that metric, but I didn't have a good explanation as to why. At the moment I could have given a minutes-long monologue about how that metric doesn't fit how I think we should be thinking about testing. However, I have zero expectations that such a monologue could have worked as an effective argument in that situation. It would be all over the place as I philosophise about testing and make all kinds of connections and analogies.

So since then, I've been thinking: how would I present an argument against measuring manual versus automated test cases? Something to the point, something relatable, something that acknowledges the need behind asking for this metric. And today it hit me: use cooking as an anology. Now I know plenty of people have made this analogy before. However, I don't remember reading everything I will cover in this blog post. And also, there's value in different people saying similar things, but each in their own voice.

<!-- TEASER_END -->


# Is cooking automated?

Hopefully your first thought after reading the question "Is cooking automated?", is "No? Parts of it? Haven't really thought about it before?" Because that confusion matches how I feel when the topic of automated versus manual testing comes up. It does not fit my model of how testing should work.

## Cooking and automation

So how does cooking relate to automation?

There definitely is some automation in cooking: hand mixers, electric juicers, food processors, rice cookers. A more detable example of automation is using a mandoline slicer instead of a knife. It doesn't fully automate cutting, but the mandoline slicer does automate away the need for impressive knife skills.

This shows, automated versus manual is very much a question of parts and degrees. Most (all?) things you can do with a hand mixer, you can do by whisking manually. To help you decide if something is cooked perfectly, you can get help from a timer and a thermometer. Some ingredients you buy, instead of making them yourself from scratch (soy sauce). Or you buy them cut and washed (vegetables) or ground (pepper) for you. Also sometimes, you don't feel like cooking, so you just throw a frozen pizza in the oven.[^1]

[^1]: I like the fluidity of language here. Heating up a frozen pizza is not cooking, because it's so easy. It is cooking, though, since you are preparing a meal. Is making a salad for dinner cooking, but making a salad for lunch not? I'm not sure.

There are also natural processes that defy the distinction between manual and automated. If I set my dough away for a few hours so that it can rise, or if I let something soak in a marinade overnight, what should we call that? I'm not doing anything, the automation isn't doing anything, yet something is still happening.

Finally, there's one piece of automation in cooking that's so obviously, so implictly automated, we never think about that it is. Heat generation. Even if you go thoroughly old school and set fire to some logs using a bow drill, you are not manually generating the heat to cook.

## People's role in cooking

Even though automation in cooking has increased dramatically the past decades[^2] and there have been experiments with fully automated cooking, I think most people's experience with cooking at home and being cooked for at a restaurant is of a combination of automated and manual cooking.

[^2]: I am not a food or cooking historian. My layman's best guess is that electricity and the industrialization of the food industry have led to a dramatic increase in automation in cooking.

Few cooking activities are fully automated. Most of them are a combination of manual and automated. Often, the automation lets us do things that would otherwise take a lot of effort and/or skills. Being a human mandoline slicer or a human food processor would not be an easy job.

And some activities are fully manual. Plating is a simple example. A bigger one is checking if something is not overcooked or undercooked, or tasting if the flavors are right. You could automate those last two, by precisely following a detailed recipe[^3] that gives you exact ingredients and cooking times. However, even if you use a recipe for the first time, that's not how you cook. Even then you use your own senses and judgement to make small adjustments.

[^3]: Also, most recipes are not detailed in a way that supports this. For example, once I encountered a recipe that said "heat the oil to just before smoking".

## Where does cooking begin? Where does it end?

So far, I've discussed cooking as something that starts when you start preparing your ingredients and ends when you plate the food. Mostly that makes sense. Shopping for groceries is not cooking. Neither is inviting people over for dinner, or doing the dishes after. All of these do impact the cooking though. Cooking happens in a context. If you only focus on the context itself, it will be impossible to fully understand what's happening.

The activity most on the border of cooking and not-cooking, is probably deciding what to cook. If you do it well in advance, it's not cooking. If it's time to prepare dinner and you go through your pantries and fridge to decide what to cook, it arguably is cooking, because you would say "I have started to cook."



# Back to manual and automated testing

I suspect the analogies between cooking and testing are clear enough without me pointing them out in details.

Sometimes talking about doing something manually versus automated makes sense. Sometimes it doesn't. Sometimes it never even occurs to us to consider the distinction. (Raise your hand if you manually compile your code.)

We shouldn't forget to consider the context when we talk about test automation. Often test automation is a shorter way of saying test execution automation. That's fine, it's how language works. It does get dangerous, however, if it makes us forget there's more to testing than test execution.

## How to have a conversation about automated versus manual testing metrics

One way to initiate a conversation about automated versus manual testing metrics is to try to reframe the topic from automation to tooling. As with cooking, it's not that we have automated parts of it, it's that we use tools to support, extend and amplify what we can do. Reframing to tools also helps to talk about more than only test execution.

I don't think that this is the best approach, though. It's a lot more focused and to the point than the minutes-long monologue I mentioned at the start of the post, but it's still quite a step away from a request for this particular metric, and more importantly from the need behind that request.

Figuring out what that need is, through a dialogue, not a discussion, is in my opinion the best approach. Probably there is a concern that we're doing things manually, where we'd be more effective using tools and automation. Making that concern explicit is the perfect starting point for a further conversation about where additional tooling can help and how best to measure if it did indeed help.
