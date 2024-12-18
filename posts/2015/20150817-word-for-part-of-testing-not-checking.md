<!--
.. title: What's the word for the part of testing that's not checking?
.. slug: whats-the-word-for-the-part-of-testing-thats-not-checking
.. date: 2015-08-17 20:19:25 UTC+02:00
.. tags: context-driven testing, testing and checking, semantics
.. category: philosophy of testing
.. link: 
.. description:
.. type: text
-->

## The question I asked

Yesterday [I asked on twitter](https://twitter.com/j19sch/status/632910141751447552):

> Question: what's the proper word for the part of testing that's not checking? #cdt #testing #semantics  
> - Joep Schuurkes (@j19sch) August 16, 2015

The reason I asked, is that I noticed I needed that word in discussions about testing and checking. If checking is part of testing - and in the RST namespace it most definitely is, see '[Testing and checking refined](http://www.satisfice.com/blog/archives/856)' -, then what can I contrast checking with? Contrasting checking with testing (as in 'checking versus testing') isn't going to work: there's one thing that's checking and then there's this other thing, testing, that contains that one thing and some other stuff[^1], but it's like a completely different thing. See the difference? Conceptually that just doesn't work - at least not in my mind.


## The answers I got
So I figured I'd ask twitter in all its infinite testing wisdom and lo and behold, not only did people reply, a discussion ensued with the following people (listed in no particular order) participating in different configurations: [@eddybruin](https://twitter.com/eddybruin), [@mariakedemo](https://twitter.com/mariakedemo), [@SandroIbig](https://twitter.com/SandroIbig), [@TestPappy](https://twitter.com/TestPappy), [@dwiersma](https://twitter.com/dwiersma), [@ilarihenrik](https://twitter.com/ilarihenrik), [@PhilipHoeben](https://twitter.com/PhilipHoeben), [@huibschoots](https://twitter.com/huibschoots) and [@deefex](https://twitter.com/deefex). Thank you all!

<!-- TEASER_END -->

Do click on the embedded tweet to read all of it, but here's a list of the answers they came up with:

- Exploring
- Learning
- Evaluating
- Monitoring
- Confidence building and refining
- Experimenting
- Non-checking

It only took a few replies for me to realize I may have asked the wrong question - as in: not the question I had intended to ask. And a quick look at the diagram in '[Testing and checking refined](http://www.satisfice.com/blog/archives/856)' confirmed this:

<div class="d-flex justify-content-center">
	<figure class="figure w-50">
  	<img src="/images/2015/testing-not-checking/checking-diagram.png" class="figure-img img-fluid rounded"
  	alt="testing and checking diagram"/>
	</figure>
</div>


Testing is a very big box. Learning is a part of it and so are experimenting, studying, questioning, modeling, etc. **and** checking. So the part of testing that's not checking, isn't just one thing, it's many things. Hence Del Delwar's ([@deefex](https://twitter.com/deefex)) reply: "*I'd suggest that's possibly too wide an array of things to encapsulate in a single word. Try 'non-checking' :-)*"

## The question I meant to ask
So with that settled, on to the question I meant to ask: If checking is "*the process of making evaluations by applying algorithmic decision rules to specific observations of a product*" (source yet again '[Testing and checking refined](http://www.satisfice.com/blog/archives/856)'), then what's the name for the non-algorithmic evaluation of a product? A 'heuristic evaluation'? Does such a thing exist? Or are all our evaluations during testing checks?

First of all, when I test, it doesn't feel like all my evaluations are checks. That may not be a very strong argument, but I do think it's worth to at least note.

Secondly, where do these algorithmic decision rules come from? Do I need to have them beforehand? Do I need to have them recorded somewhere? Or can I just make them up as I go along? More importantly, do these rules need to be explicit?

And that last question led me to a bunch of philosophical questions:

- If not all of our evaluations are checks per se, is it possible to (re-)formulate them as checks?
- If I can't express my evaluation as a check, how would I able to communicate in a meaningful way about my evaluation?
- If my evaluation is founded on tacit knowledge and there's no need to make that knowledge explicit, because the people I communicate with, share in that tacit knowledge, can that evaluation still be considered a check?
- Does it matter if the tacit knowledge on which an evaluation is based, is 'weak' (we could make it explicit) or 'strong' (we can't make it explicit)?
- Where does algorithmic end? I can make an algorithmic decision if I find something beautiful, by observing my aesthetic feelings towards that object. If I observe positive feelings within myself, I find the thing beautiful. However, I can't make an algorithmic decision if I find some beautiful (yes, I know, that's the exact same sentence), because I can't specify a set of algorithmic rules that decide if I would find something beautiful. So what it boils down to is: is the algorithmic evaluation of an observation of my own mental state a valid check? Or should we go one level deeper, to the cause(s) of my mental state?
- Is the previous bullet point anything other than a philosophical quagmire one needs to extract oneself out off Münchhausen-style? In any case I highly recommend reading Raymond M. Smullyan's "[An Epistemological Nightmare](http://www.mit.edu/people/dpolicar/writing/prose/text/epistemologicalNightmare.html)" to sink a little deeper.

## Back to the context of the question
So… why was I asking this question again about non-algorithmic evaluation during testing? It's quite simple actually:  
(1) If testing is investigating a product to evaluate it  
AND  
(2) all evaluation is done by applying algorithmic decision rules,  
THEN  
(3) the core of testing is checking.

Of course, there's all the stuff going on around the checking. There's all the investigating, modeling, experimenting to come to the checks. And there's all the sense-making of the results of the checks to provide valuable information to our stakeholders. But it all revolves around checking.

So when I am talking to someone who seems to think that there's nothing more to testing than checking, I can argue that there's all this other stuff we testers do that is testing, but is not checking. But what I cannot argue is that there is something we do instead of checking (so something non-algorithmic) that leads to evaluative data[^2] about the product, because there is no such thing. And that bugs me, because that's not how I've been using the words 'checking' and 'testing'.

---

*This post was originally published on my old blog.*

[^1]: Advanced semantics question: is 'checking versus testing' more like 'apples versus fruit' or more like 'squares versus rectangles'?[^3]

[^2]: Data + interpretation = information. Hmm… or: Interpretation(data) = information.

[^3]: Apparently the correct answer is "[leaves vs trees](https://twitter.com/al3ksis/status/633343017252995073)".