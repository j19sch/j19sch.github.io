<!--
.. title: (clj 0) Diving straight in with some koans
.. slug: clj0-diving-straight-in
.. date: 2020-04-27 21:00:15 UTC+02:00
.. tags: clojure, koans, brave-true
.. category: clojure
.. link: 
.. description: 
.. type: text
-->

## Why Clojure?

A long time ago (meaning I don't remember when but it's been a while) I learned about a programming language called Lisp. It was said that by studying this language you'd gain [deep insights](https://twobithistory.org/2018/10/14/lisp.html) into programming and you'd never write code the same way again. That definitely piqued my interest.

Some time later (don't remember when exactly either) I learned about the existence of Clojure and that it too, was something special. So I added it to the list of programming languages I wanted to learn some day.

Then, earlier this month, I felt the need to start a new project. To learn something new. So I figured I'd learn Lisp. That didn't last long though, as I found out that the recommended editor for Lisp is Emacs. And from trying out Emacs and vi about 20 years ago I knew that for some reason vi does fit with how my mind works, and Emacs doesn't.

<!-- TEASER_END -->

So I went back to the drawing board, remembered there's a thing called [Clojure](https://clojure.org/), and learned that it's actually a Lisp dialect. Perfect! (Spoiler: Emacs is also recommended for Clojure, more on that later.) Next question was how to start learning. Back in 2018 I enjoyed [solving](https://github.com/j19sch/python_koans) the [Python koans](https://github.com/gregmalcolm/python_koans), so I did an internet search and found the [Clojure koans](https://github.com/functional-koans/clojure-koans).


## The Clojure koans
During the weekend of 18-19 April I [solved](https://github.com/j19sch/clojure-koans) the first 13 Clojure koans. I [tweeted](https://twitter.com/j19sch/status/1251948519373647876) how it made my head hurt but in a good way. But then on Monday the 20th I started on the 14th koan on recursion and got [stuck](https://github.com/j19sch/clojure-koans/commit/2a4dc73224d0c53665edcda4382376aa4ed1f129). And to be honest, I had also left a [ToDo](https://github.com/j19sch/clojure-koans/blob/master/src/koans/07_functions.clj#L29) in the 7th one about functions, because I wasn't sure I had the correct solution.

So I decided I needed a different approach, one that included more explaining. Searching the internet led to pages such as the [Clojure Newbie Guide](http://www.clojurenewbieguide.com/) and the Reference section of Reddit's [r/Clojure](https://www.reddit.com/r/Clojure/). A lot of people recommended the book "[Clojure for the Brave and True](https://www.braveclojure.com/)". After exploring the [free online version](https://www.braveclojure.com/clojure-for-the-brave-and-true/) I decided this was my way forward.


## Clojure for the Brave and True
The first chapter has you create a Clojure project. So I followed the steps and pushed it all into a new [git repository](https://github.com/j19sch/clojure-brave-true).

Next was chapter 2 "How to Use Emacs, an Excellent Clojure Editor", which led me to explore my options for Clojure editors. More on that in my next post.
