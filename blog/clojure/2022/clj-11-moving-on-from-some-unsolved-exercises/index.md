<!--
.. title: (clj 11) Moving on from some unsolved exercises
.. slug: clj-11-moving-on-from-some-unsolved-exercises
.. date: 2022-12-29 16:08:36 UTC+01:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description: 
.. type: text
-->

At the end of chapter 4 of ["Clojure for the Brave and True"](https://www.braveclojure.com/clojure-for-the-brave-and-true/) there are [four exercises](https://www.braveclojure.com/core-functions-in-depth/#Exercises). This post is about me deciding to move on to chapter 5 after solving 1.5 of these exercises.


# The challenge with these exercises

A good example to talk about the challenge with these exercises is the second one:

>  Write a function, append, which will append a new suspect to your list of suspects.

<!-- TEASER_END -->

The list of suspects is part of the [example program](https://www.braveclojure.com/core-functions-in-depth/#A_Vampire_Data_Analysis_Program_for_the_FWPD) at the end of chapter 4, which was the topic of my two previous posts [(clj 9)](link://slug/clj-9-how-to-figure-out-what-a-function-does) and [(clj 10)](link://slug/clj-10-the-mapify-function-of-clj-9-revisited). This list is read from a csv file, so one way to interpret the exercise, is that you have to append them to the file. However, writing to the csv file is what exercise 4 is all about.

Another possibility is to append when the file is read by the program. So I took inspiration from the example's main function `glitter-filter`:

```Clojure
(glitter-filter 3 (mapify (parse (slurp filename))))
```

and changed it to this:

```Clojure
(defn append
 	[name glitter-index]
 	(conj (mapify (parse (slurp filename))) {:name name :glitter-index glitter-index})
 	)
(append "Bob" 5)
; => ({:name "Bob", :glitter-index 5} {:name "Edward Cullen", :glitter-index 10}
; 	{:name "Bella Swan", :glitter-index 0} {:name "Charlie Swan", :glitter-index 0}
;	{:name "Jacob Black", :glitter-index 3} {
```

As you might have noticed, however, that's a prepend, not an append. That can be solved by changing the list to a vector - as lists are made for prepending and vectors for appending - but why does the exercise require me to do this?

And how does this solution work in the wider context of the program? Should I merge it with the original `glitter-filter` function so I can run it on the file plus one more suspect?


## What's the purpose of these exercises?

This led me to wonder about what the purpose of these exercises is. Are they about getting a (the?) correct solution? Or are they about getting you to explore Clojure a bit further by presenting you with a problem?

The book unfortunately does not tell you. Exercises are first introduced in chapter 3 as *"a fun way to test your Clojure knowledge and to learn more Clojure functions"*. It's unclear, however, if that also applies to exercises in subsequent chapters. Another hint to an answer is that the authors haven't published the solutions. They are not in the book and they are not in the [repo](https://github.com/braveclojure/cftbat-code) that reproduces the example code from the book.

Other people have [published](https://github.com/raverona/clojure-for-the-brave-and-true/blob/master/src/clojure_for_the_brave_and_true/chapter4/exercise2.clj) their [solutions](https://github.com/dancrumb/clojure-brave-and-true/blob/master/src/clojure_brave_and_true/chapter4.clj) to the [exercises](https://github.com/rafaeldelboni/clojure-brave-and-true/blob/master/src/clojure_brave_and_true/chapter4.clj). Curiously, they're all very different solutions to the same exercises.

So it seems these exercises are more prompts to learn and practice than exercises with a very specific learning goal to each of them.


# Deciding to move on

After spending a few hours on these exercises and going through the above thought process, I needed to decide what to do. Am I going to spend more time trying to tackle these exercises, even though I'm learning Clojure for fun and I'm having no fun?

Then I realized there was another question hiding behind that question. If I learned things about Clojure by working on these exercises, but didn't find a solution to most of them, isn't that sufficient? Shouldn't that be sufficient? I learned things, right? Especially if my goal is to understand Clojure and not (yet) to start using it?

I wish I could wholeheartedly answer "yes" to that question. That's not the case, though. So it is both confident I'm making the right decision and feeling a little sad and disappointed with myself, that I have decided to let these exercises be and move on to chapter 5.
