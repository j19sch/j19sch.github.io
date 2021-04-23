<!--
.. title: VIPT Intermezzo - Models and the Unix philosophy
.. slug: vipt-intermezzo-models-and-the-unix-philosophy
.. date: 2012-07-15 20:25:03 UTC+02:00
.. tags: VIPT, context-driven testing, models
.. category: philosophy of testing
.. link: 
.. description:
.. type: text
-->

Thanks to [Neil Thompson's comments](https://testingcurve.wordpress.com/2012/07/09/yet-another-testing-model-value-information-processes-value/#comments) on my previous post, I started thinking about what I want to do with the VIPT model. Do I want to expand and refine it to a grand unified theory of testing? And if not, then what?


## The Unix philosophy

After some thinking I realized that with regard to models, I adhere to the [Unix philosophy](http://www.faqs.org/docs/artu/ch01s06.html).

### Do one thing and do it well
Particularly I am thinking about the following quote from Doug McIlroy:

> "This is the Unix philosophy: Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface."

<!-- TEASER_END -->

As a result you can do this in Unix *(example taken from [here](http://www.december.com/unix/tutor/pipesfilters.html))*:

```sh
cat apple.txt | wc | mail -s "The count" nobody@december.com
```

By piping the output of the first command to the second and then to the third, you get a small 'program' that counts the characters, words, and lines of the apple.txt file, then mails the results to nobody@december.com with the subject line "The count."

### Worse is better

Another part of the Unix philosophy according to Richard P. Gabriel is "Worse is better." (As can be read [here](http://www.dreamsongs.com/RiseOfWorseIsBetter.html).) Simplicity is more important than other attributes - including correctness, consistency, and completeness. Basically you want something that's good enough for you to have a use for it and simple enough for you to understand it. Quite similar to the ultimate toolbox actually: duct tape and WD40. If it moves and it shouldn't, you need duct tape. And if it doesn't move and it should, you need WD40. No need to worry if you want to use glue, a nail or a screw and of what kind, just duct tape.


## Applying the Unix philosophy to models

Translating this to models, we get the following three principles:

- Create models that do one thing and do it well.
- Create models that work together.
- Prefer simplicity in your models over correctness, consistency and completeness.

This certainly won't get us to a grand unified theory of testing. It also won't give us any definitive models. What it does give us, is a big set of simple models. Sometimes we need only one model; sometimes we need to take a few and make them work together. Other times we may find none of our models are good enough, so we just build a new one and add it to our collection. And since models are always limited and thus fallible, let's keep them simple, because what we never will achieve is correctness, consistency or completeness.

As such a model is very much a tool in the VIPT model. On its own it doesn't do anything. When part of a process, it can provide valuable information - or not.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2012/07/15/vipt-intermezzo-models-and-the-unix-philosophy/).*
