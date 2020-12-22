<html><body><p>Last week ago the following happened on twitter:
</p><blockquote class="twitter-tweet" lang="en">New word of the day: "information debt". It's like technical debt, but related to information, communication, models, docs, visualisations.

— Joep Schuurkes (@j19sch) <a href="https://twitter.com/j19sch/statuses/486534198803841024">July 8, 2014</a></blockquote>
<blockquote class="twitter-tweet" lang="en"><a href="https://twitter.com/j19sch">@j19sch</a>: New word of the day: "information debt" =&gt; blogpost coming up ?!?!?

— Simon P. Schrijver (@SimonSaysNoMore) <a href="https://twitter.com/SimonSaysNoMore/statuses/486551279590977536">July 8, 2014</a></blockquote>
<blockquote class="twitter-tweet" lang="en"><a href="https://twitter.com/SimonSaysNoMore">@SimonSaysNoMore</a> Wasn't planning to, but now you made me think about it, so yes. Damn you! :-P

— Joep Schuurkes (@j19sch) <a href="https://twitter.com/j19sch/statuses/486555404089188352">July 8, 2014</a></blockquote>
In case you don't know what technical debt is, you might want to read this first: <a href="http://techblog.net-a-porter.com/2011/10/agile-tetris/">http://techblog.net-a-porter.com/2011/10/agile-tetris/</a> (It's the oldest source I could find of the technical debt-tetris analogy, by the way. If you know of an older one, please leave a comment.)
Information debt is the same but different. It's not about the code or the implementation, but it's about information, communication, models, documents and visualizations. Information debt is information being less available than you'd like it to be. Or relating it to <a href="http://testingcurve.wordpress.com/2012/07/09/yet-another-testing-model-value-information-processes-value/">the VIPT model</a>: information debt are your processes and/or tools making valuable information less available than you want it to be.

And it turns out information debt is everywhere:
- a huge document (e.g. test plan) that's very hard to navigate
- test cases that don't communicate why these specific test cases have been chosen
- an outdated document that's not being updated because everyone knows what it should say
- only one person knows and he's on vacation
- a quickly sent out mail just about that one item leading to confusion and discussion
- sloppy bug reports
- a meeting with a bunch of people, none of which have enough of the relevant information
- not having the proper application to view a document (I'm looking at you MS Project)
- the models or visualizations of the system exist in people's heads only
- a daily stand-up about tasks and resources instead of sharing information
- the only reliable list of outgoing interfaces is in the scheduler of the application

And it's caused by a number of things:
- lack of skill
- taking shortcuts because of time pressure
- whiteboards or similar not being available
- not giving it any thought
- the assumption that everyone knows already
- not being aware of the debt
- following processes and templates instead of being purpose-focused
- not taking the time to do it properly
- having to get up from your desk to talk to someone
- thinking of something as trivial or obvious
- not knowing any better

Now these are two very nice and very incomplete lists, but what's really going on here?

First of all, good information management is hard, very hard. I recently participated in the BBST Bug Advocacy course and even then, even when you can take all the time you want to focus on adding the perfect comment to a bug report, you'll get feedback containing plenty of things to improve. And that's in a "You had one job"-scenario. In a real working situation it will be so much more difficult - more pressure and more constraints.

Which brings me to my second point. There's a reason the agile manifesto says: working software over comprehensive documentation. Our primary product as a software development team is that software. Good information management is very important to deliver that software, but it has a supportive role. It's not on center stage. (Which, as with technical debt, makes it so easy to take some shortcuts now and worry about the consequences later.)
However, as a tester information *is* your main product. You don't design the software, you don't build the software, you investigate the software(1) to evaluate it. And not only is information your main product, it's also one of your main tools. You want to know what to test, how to test, what's been tested, the results of those tests, how to recognize a problem, ... This makes information debt a very big deal: it touches the core of what we do as testers. Although information debt has team impact, it's the testers that it hits the hardest.

So what are we to do? To start off I can think of three things:
- become more aware of information debt, recognize it, identify it, name it
- when there are trade-offs to be made, make the information debt explicit
- become better at making information available: improve your writing, reading, talking, drawing, ...

Finally, I feel like I should say something about how all of this relates to tacit and explicit knowledge. I do think some interesting points can be made about information debt and tacit knowledge, but I need to give it some more thought. So I will leave that for a later blog post.

--- --- ---

(1) Or rather: you investigate the *product* to evaluate it, but that sounded a bit confusing with a different referent of 'product' in the previous sentence.</body></html>