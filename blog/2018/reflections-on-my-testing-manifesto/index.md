<!--
.. title: Reflections on my testing manifesto
.. slug: reflections-on-my-testing-manifesto
.. date: 2018-12-22 17:43:10 UTC+01:00
.. tags: agile, context-driven testing, devops, manifesto, software testing
.. category: testing manifesto
.. link: 
.. description:
.. type: text
-->

Earlier this month I published my [Manifesto for software testing](link://slug/manifesto-for-software-testing). This manifesto is my attempt to bring together what I have learned about testing from the context-driven, agile and DevOps communities. Below you can find the manifesto with my reflections on it.

#### 1. Testing is investigating in order to evaluate a product.
This definition is clearly influenced by James Bach's "questioning a product in order to evaluate it". I'm not sure at which point I started misremembering his definition as "investigating a product...", but it works well with a change I did make intentionally: moving "a product" to the second part of the definition. As explained in 6. I believe that in order to evaluate the product, we need to investigate a number of different things, not only the product.

<!-- TEASER_END -->

#### 2. An evaluation is a judgement about quality - quality being value to persons who matter.
The definition of quality used here is Jerry Weinberg's. I made one small change: "persons who matter" instead of "a person who matters". I did this, because it makes more sense in the context of the previous point. In 1. I say we want to evaluate the product, say something about its overall quality, which consists of the quality to different people who matter. (I had trouble coming up with a product where there is only one person who matters.)
There is a risk in the way I am phrasing this: it might suggest that all persons who matter, assign the same value to the same things. That is not the case and Jerry Weinberg's definition captures this better.

#### 3. This makes testing a fundamentally human and contextual activity.
With people doing the investigating and the evaluating and the assigning value, there is no escaping humanity in testing. This means we need to account for the nature of human observation and cognition (both their strengths and their limits), for how we assign value and meaning, for the social aspects of software development and for its ethical aspects.

Since being human means being contextual - none of us are all-seeing and all-knowing - the same applies to testing. This is also why in a draft version of this manifesto 4. contained the context-driven statement "There are no best practices in testing, only good practices in context."

#### 4. As such, testing is an exploratory and open-ended activity, requiring continuous evaluation of and experimentation with our practices.
I packed a lot of different influences in this one sentence to expand on 3.
Testing is a wicked problem. Testing deals with the known knowns (Are we sure?), unknown knowns (Can we make these explicit?), known unknowns (Can we find out?) and unknown unknowns (Can we find out what it is we need to find out?). Both people and innovation fall (mostly?) in the complex domain of Cynefin, so we need to probe - sense - respond. Also, systems thinking! Finally, serendipity is an amazing testing skill.
In addition to that, there are the ideas from the agile, modern agile, and lean communities that all reinforce the need for continuous evaluation and experimentation.
There is no fixed recipe; there is only a craft to practice.

Finally, I snuck in an "our" without explaining who this "we" is, it refers to. As a matter of fact, I never clarify this in the manifesto. The reason for this is that the manifesto addresses everyone who performs activities that to this manifesto qualify as testing.

#### 5. As such, testing cannot be automated. We do use a wide variety of tools to support, extend and amplify our testing. We may also delegate some decisions to our tools. However, without a human context, these decisions are meaningless.
With testing a fundamentally human activity requiring continuous evaluation and experimentation, automating testing is not going to happen. People will need to be involved in some way.

However, without tools, without automation, testing becomes nearly impossible. No notebooks, no mindmaps, no bug trackers, no IDEs, no browser developer tools, no way to interface with an API, no way to look at log files, no Excel, no nothing. Because of this, I think the concept of "extended cognition" is an excellent way to think of tool usage in testing. (One of my older blog posts, "[The test case - an epistemological deconstruction](https://testingcurve.wordpress.com/2015/02/01/the-test-case-an-epistemological-deconstruction/)", also ventures in this territory.)

The words "support, extend and amplify" are deliberately chosen. Tools that support us, makes things easier than doing these things without them. Tools that extend our abilities, increase our reach. They allow us to go deeper and further than without them. Tools that amplify, increase the intensity of what we do. They allow us to do the same thing faster than without them. Often this means we can do a lot more of the same thing.
Finally, we can delegate decisions to our tools. I wrote that with continuous integration and deployment in mind.

#### 6. Anything that can be observed, can be investigated: the product, artifacts, interactions, and tools.
Investigating the product can be split in three different areas:  
(1) static testing: any investigation that doesn't require the product to be running;  
(2) dynamic testing: any investigation that does require the product to be running;  
(3) monitoring: any investigation while the product is in actual use.

However, as mentioned in the reflection on 1. we should not only investigate the product. Anything related to the product can be a valuable source of information. We can review acceptance criteria and design document. We can do an analysis of the commit history, e.g. usage of curse words in commit messages. We can count the number of questions team members ask each other in the daily scrum. Etc.

Finally, we should not forget that a lot of testing is hidden in other activities. For instance, a developer looking at their screen as they are programming, is testing. I could even argue that even if they were to close their eyes, they are still testing: their muscle memory will give them information on how likely it is they hit the intended key on the keyboard.

#### 7. This means that testing is fundamentally interwoven with all activities within a product's existence: conception, development, operation, and disposal.
As hinted at in the last paragraph of the reflection on 6. testing is happening all the time - in subtle and less subtle ways. Any feedback loop implies testing is happening.

The choice of the four phases conception, development, operation, and disposal is deliberate. With testing being a fundamental part of all phases, the question "When should testing start?" makes no sense. And testing only ends when the software is done, which means when the product no longer exists as product.

#### 8. And the core question during the product's lifecycle is: how do we discover what we need to discover in the most effective way?
This cuts through all the questions about processes, procedures, roles, people, tools, artifacts, methodologies, etc. In the end the product of testing is information, so how are you going to get that done?

---

*This post was originally published [here](https://testingcurve.wordpress.com/2018/12/22/reflections-on-my-testing-manifesto/).*
