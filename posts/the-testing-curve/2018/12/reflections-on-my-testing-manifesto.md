<html><body><p>Earlier this month I published my <a href="https://testingcurve.wordpress.com/2018/12/04/manifesto-for-software-testing/">Manifesto for software testing</a>. This manifesto is my attempt to bring together what I have learned about testing from the context-driven, agile and DevOps communities. Below you can find the manifesto with my reflections on it.<br></p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4>1. Testing is investigating in order to evaluate a product.</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>This definition is clearly influenced by James Bach's "questioning a product in order to evaluate it". I'm not sure at which point I started misremembering his definition as "investigating a product...", but it works well with a change I did make intentionally: moving "a product" to the second part of the definition. As explained in 6. I believe that in order to evaluate the product, we need to investigate a number of different things, not only the product.<br></p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4>2. An evaluation is a judgement about quality - quality being value to persons who matter.</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>The definition of quality used here is Jerry Weinberg's. I made one small change: "persons who matter" instead of "a person who matters". I did this, because it makes more sense in the context of the previous point. In 1. I say we want to evaluate the product, say something about its overall quality, which consists of the quality to different people who matter. (I had trouble coming up with a product where there is only one person who matters.)<br>There is a risk in the way I am phrasing this: it might suggest that all persons who matter, assign the same value to the same things. That is not the case and Jerry Weinberg's definition captures this better.<br></p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4>3. This makes testing a fundamentally human and contextual activity.</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>With people doing the investigating and the evaluating and the assigning value, there is no escaping humanity in testing. This means we need to account for the nature of human observation and cognition (both their strengths and their limits), for how we assign value and meaning, for the social aspects of software development and for its ethical aspects.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Since being human means being contextual - none of us are all-seeing and all-knowing - the same applies to testing. This is also why in a draft version of this manifesto 4. contained the context-driven statement "There are no best practices in testing, only good practices in context."</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4>4. As such, testing is an exploratory and open-ended activity, requiring continuous evaluation of and experimentation with our practices.</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>I packed a lot of different influences in this one sentence to expand on 3.<br>Testing is a wicked problem. Testing deals with the known knowns (Are we sure?), unknown knowns (Can we make these explicit?), known unknowns (Can we find out?) and unknown unknowns (Can we find out what it is we need to find out?).  Both people and innovation fall (mostly?) in the complex domain of Cynefin, so we need to probe - sense - respond.  Also, systems thinking! Finally, serendipity is an amazing testing skill.<br>In addition to that, there are the ideas from the agile, modern agile, and lean communities that all reinforce the need for continuous evaluation and experimentation.<br>There is no fixed recipe; there is only a craft to practice.<br></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Finally, I snuck in an "our" without explaining who this "we" is, it refers to. As a matter of fact, I never clarify this in the manifesto. The reason for this is that the manifesto addresses everyone who performs activities that to this manifesto qualify as testing.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4>5. As such, testing cannot be automated. We do use a wide variety of tools to support, extend and amplify our testing. We may also delegate some decisions to our tools. However, without a human context, these decisions are meaningless.</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>With testing a fundamentally human activity requiring continuous evaluation and experimentation, automating testing is not going to happen. People will need to be involved in some way.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>However, without tools, without automation, testing becomes nearly impossible. No notebooks, no mindmaps, no bug trackers, no IDEs, no browser developer tools, no way to interface with an API, no way to look at log files, no Excel, no nothing. Because of this, I think the concept of "extended cognition" is an excellent way to think of tool usage in testing. (One of my older blog posts, "<a href="https://testingcurve.wordpress.com/2015/02/01/the-test-case-an-epistemological-deconstruction/">The test case – an epistemological deconstruction</a>", also ventures in this territory.)<br></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The words "support, extend and amplify" are deliberately chosen. Tools that support us, makes things easier than doing these things without them. Tools that extend our abilities, increase our reach. They allow us to go deeper and further than without them. Tools that amplify, increase the intensity of what we do. They allow us to do the same thing faster than without them. Often this means we can do a lot more of the same thing.<br>Finally, we can delegate decisions to our tools. I wrote that with continuous integration and deployment in mind.<br></p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4>6. Anything that can be observed, can be investigated: the product, artifacts, interactions, and tools.</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Investigating the product can be split in three different areas:<br>(1) static testing: any investigation that doesn't require the product to be running;<br>(2) dynamic testing: any investigation that does require the product to be running;<br>(3) monitoring: any investigation while the product is in actual use.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>However, as mentioned in the reflection on 1. we should not only investigate the product. Anything related to the product can be a valuable source of information. We can review acceptance criteria and design document. We can do an analysis of the commit history, e.g. usage of curse words in commit messages. We can count the number of questions team members ask each other in the daily scrum. Etc.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Finally, we should not forget that a lot of testing is hidden in other activities. For instance, a developer looking at their screen as they are programming, is testing. I could even argue that even if they were to close their eyes, they are still testing: their muscle memory will give them information on how likely it is they hit the intended key on the keyboard.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4>7. This means that testing is fundamentally interwoven with all activities within a product’s existence: conception, development, operation, and disposal.</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>As hinted at in the last paragraph of the reflection on 6. testing is happening all the time - in subtle and less subtle ways. Any feedback loop implies testing is happening.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The choice of the four phases conception, development, operation, and disposal is deliberate. With testing being a fundamental part of all phases, the question "When should testing start?" makes no sense. And testing only ends when the software is done, which means when the product no longer exists as product.<br></p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4>8. And the core question during the product’s lifecycle is: how do we discover what we need to discover in the most effective way?</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>This cuts through all the questions about processes, procedures, roles, people, tools, artifacts, methodologies, etc. In the end the product of testing is information, so how are you going to get that done?<br></p>
<!-- /wp:paragraph --></body></html>