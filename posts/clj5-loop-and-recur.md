<!--
.. title: (clj 5) Loop and recur
.. slug: clj5-loop-and-recur
.. date: 2020-12-23 15:25:15 UTC+01:00
.. tags: clojure, brave-true, loop, recur
.. category: clojure
.. link: 
.. description:
.. type: text
-->

Yet again it's been a while since I did some Clojure or blogged about it. This time I'm writing this blog post
three months after working on the code on September 5, 6 and 12. I'm not going to dwell on that too long, because
other things in my life were more important. I did feel a little sad when this year's [Advent of Code](https://adventofcode.com/)
launched and I realized my Clojure is nowhere near a state where I could attempt the puzzles. So I ended up doing
the first 10 days in Python, which is twice as far as I got last year.

I also feel like my current approach to learning lends itself well enough to going slow. Taking my time to play around
and make notes with while working through a section of [Clojure for the Brave and True](https://www.braveclojure.com/)
and then revisiting my code and notes later to write a blog post, does seem to result in stuff actually sticking in my memory.
(Disclaimer: am writing this before writing the rest of this blog post.) Slow is smooth and smooth is fast, as they say.

The section I tackled in September is "Pulling It All Together" from Chapter 3, which describes the construction of a 
piece of code of about 50 lines in which - I'm sorry to say -  a hobbit gets hit in different body parts.

<!-- TEASER_END -->

## Retracing my steps from three months ago
Despite the optimistic tone in the intro above, waiting three months to write this blog post might not have been the best idea.
There's enough to work with: the section of the book, my [notes](https://workflowy.com/s/clj-5-ch3-pulling-it/DneREuVAmKt9PHwU)
in [Workflowy](https://workflowy.com/), and of course my [code](https://github.com/j19sch/clojure-brave-true/blob/master/clojure-noob/src/clojure_noob/hobbit.clj). But it is taking some work.

Some of the things I had to rediscover:
- `:%Eval` makes vim-fireplace evaluate the whole file
- the thing with square brackets that looks like a Python list is called a vector
- "coll" is short for collection, so maps, vectors, lists and sets
- my code had a bunch of `ArityException`s because it was calling the wrong function (`hit` instead of `target-hit`)
- what I struggled with in this section (`loop` and `recur`, `into` and `conj`, `reduce`) and why
- if you don't push your code, it's hard to pull it when you're working on your other machine

And there's one thing I'm happy I discovered: figuring out what my 167 lines of Clojure do, was made easier due to the
functional style of programming. You put some thing(s) in a function and you get something back. No state, no classes.
Understand what each function does, figure out which function calls which other one and you're there.

So having reacquainted myself with what I did, this blog post will cover the following topics:
- vim-sexp and bracket editing
- loop and recur
- into and conj
- reduce
- what would `hobbit.clj` look like in Python?


# notes

yay shift+k

## remaining exceptions
`NullPointerException   clojure.lang.Numbers.ops (Numbers.java:1013)`
-> invalid target for target-hit

`ClassCastException class clojure.lang.PersistentVector cannot be cast to class java.lang.Number (clojure.lang.PersistentVector is in unnamed module of loader 'app'; java.lang.Number is in mo dule java.base of loader 'bootstrap')  clojure.lang.Numbers.add (Numbers.java:128)`
-> vector of vectors into looper function (oh yeah, it's called vector)

`ArityException Wrong number of args (3) passed to: core/looper  clojure.lang.AFn.throwArity (AFn.java:429)`
-> three arguments instead of vector to looper function

`IllegalArgumentException Don't know how to create ISeq from: java.lang.Long  clojure.lang.RT.seqFrom (RT.java:542)`
`(into [1] 2);` while `(conj [1] 2);` works, so does `(conj [1] [2]);` and `(into [1] [2]);`



## vim sexp (with alt bindings) and brackets
forgot a closing bracket while copying code

getting curious about conjure because tweets by Oliver Caldwell
https://github.com/Olical/conjure
https://twitter.com/olivercaldwell?lang=en


## loop and recur
related to looper and other-loop and set-looper  and looper1 -> loop/recur

## into and conj

The hobbit script uses an `into` to add a set of maps to a vector of maps inside a `recur`. That tripped me up,
also when building my own loopers where I had to use `conj` instead. It's interesting how simple functions such
as `into` and `conj` become harder to undestand when part of a more difficult context.

In the end I found it helpful to try out a bunch of variations, starting with vectors containing integers, 
then replacing the integers with maps to get closer to what's in the hobbit script.

```clojure
(into [] [1 2 3] )
; => [1 2 3]
(conj [] [1 2 3] )
; => [[1 2 3]]
(into [9 8] [1 2 3] )
; => [9 8 1 2 3]
(conj [9 8] [1 2 3] )
; => [9 8 [1 2 3]]
(into [1 2 3] [])
; => [1 2 3]
(conj [1 2 3] [])
; => [1 2 3 []]
(into [1 2 3] 4)
; IllegalArgumentException Don't know how to create ISeq from: java.lang.Long  clojure.lang.RT.seqFrom (RT.java:542)
(conj [1 2 3] 4)
; [1 2 3 4]
(into [{:name "my-arm"}] [{:name "left-head"} {:name "right-head"}])
; => [{:name "my-arm"} {:name "left-head"} {:name "right-head"}]
(conj [{:name "my-arm"}] [{:name "left-head"} {:name "right-head"}])
; => [{:name "my-arm"} [{:name "left-head"} {:name "right-head"}]]
```

These examples allowed me to see that Clojure's `into` and `conj` are very similar to Python's `extend()` and `append()`.


## reduce

My notes show it took me some effort to understand `reduce`. They say "struggling a bit with syntax" and
"it's not obvious" and "had to re-read and re-learn", but I have no idea what it was that I found non-obvious.

My best guess is that it was a bit of a leap for me to go from these examples:
```clojure
(reduce + [1 2 3 4])
; => 10
(reduce + 15 [1 2 3 4])
; => 25
```

to a `reduce` that takes an anonymous function calling an other function to work on a vector of maps. To be fair,
it is an improved implementation of a function that was explained earlier, so it is clear what this `reduce` refactored
function is supposed to do.


## comparing with python
how would I write in in Python?
more functional style?
https://github.com/j19sch/clojure-brave-true/blob/master/python-comparisons/hobbit.py