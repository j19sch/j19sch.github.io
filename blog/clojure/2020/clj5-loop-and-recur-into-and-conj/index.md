<!--
.. title: (clj 5) Loop and recur, into and conj
.. slug: clj5-loop-and-recur-into-and-conj
.. date: 2020-12-26 10:09:08 UTC+01:00
.. tags: clojure, programming, brave clojure, python
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

- `:%Eval` makes [vim-fireplace](https://github.com/tpope/vim-fireplace) evaluate the whole file
- the thing with square brackets that looks like a Python list is called a vector
- "coll" is short for collection, so maps, vectors, lists and sets (knowing the vocabulary matters)
- my code had a bunch of `ArityException`s because it was calling the wrong function (`hit` instead of `target-hit`)
- what I struggled with in this section (`loop` and `recur`, `into` and `conj`, `reduce`) and why
- if you don't push your code to remote, it's hard to pull it when you're working on your other machine

And there's one more thing: figuring out what my 167 lines of Clojure do, was made easier due to the functional style of programming. You put some thing(s) in a function and you get something back. No state, no classes. Understand what each function does, figure out which function calls which other one(s) and you're there.

So having reacquainted myself with what I did, this blog post will cover the following topics:

- vim-sexp and bracket editing
- loop and recur
- into and conj
- reduce
- what would `hobbit.clj` look like in Python?


## vim-sexp (with alt mappings) and brackets

While copying some code I forgot a closing bracket and that got me into trouble with [vim-sexp](https://github.com/guns/vim-sexp), which I use in combination with Tim Pope's [alternative mappings](https://github.com/tpope/vim-sexp-mappings-for-regular-people).
The trouble being that I found myself unable to add the closing bracket through normal editing. (I could not reproduce the problem
while writing this post. Perhaps because I only tried just now with simpler pieces of code, perhaps because I was mistaken earlier.)

One solution I found was to use `cse]` to surround an element in brackets and then delete the opening one. That's not a satisfactory
solution though, since it's a two-steps-forward-one-step-back kind of solution. I also found `<I` and `>I`, which allows you to insert at the beginning and end of a form, but since parantheses, brackets and braces determine where forms start and end, it wasn't a good solution either. In the end I settled for adding the closing bracket and then using slurpage ( `>)`, `<(` ) and barfage ( `>(`, `<)` ) to get it in the right place. And at some point during all of this, I found Micah Elliott's [vim-sexp cheat sheet](http://micahelliott.com/posts/2015-08-20-vim-sexp-cheat-sheet.html).

Finally, because it's the best place in this post to mention it, the more [Oliver Caldwell](https://twitter.com/olivercaldwell) tweets about 
his vim plugin [conjure](https://github.com/Olical/conjure), the more curious I get to try it out instead of [vim-fireplace](https://github.com/tpope/vim-fireplace).


## loop and recur

After a straightforward example with `loop` and `recur` in "Clojure for the Brave and True", you get thrown in the deeper end with the following piece of code:
```clojure
(defn symmetrize-body-parts
	"Expects a seq of maps that have a :name and :size"
	[asym-body-parts]
	(loop [remaining-asym-parts asym-body-parts
		   final-body-parts []]
		(if (empty? remaining-asym-parts)
			final-body-parts
			(let [[part & remaining] remaining-asym-parts]
				(recur remaining
					(into final-body-parts
						(set [part (matching-part part)])))))))
```
The explanation of this function ends with: _"If you’re new to this kind of programming, this code might take some time to puzzle out.
Stick with it! Once you understand what’s happening, you’ll feel like a million bucks!"_

Despite having written three additional functions with `loop`/`recur` in September, I fould myself having to puzzle it out yet
again to write this blog post. Upside of that is that after re-reading a part of the section, checking the Clojure documentation
on [`loop`](https://clojuredocs.org/clojure.core/loop) and [`recur`](https://clojuredocs.org/clojure.core/recur), and looking at
the above example again, I think I finally understand.

The key to that understanding was realizing what happens to the `remaining-asym-parts` and the `final-body-parts` in the `loop`.
When we reach the `loop`, `remaining-asym-parts` is the same as `asym-body-parts` and `final-body-parts` is an empty vector `[]`.
At some point `remaining-asym-parts` will be empty thanks to the code that follows, at which point the function return `final-body-parts`.
Until then however, the code splits `remaining-asym-parts` in `part` and `remaining`. The `part` gets put into `final-body-parts`, together
with its mirror part if needed. Or rather, `(into final-body-parts (set [part (matching-part part)]))` returns the updated
`final-body-parts`. Which means that we give our `recur` two expressions to use when jumping back to the `loop`: (1) `remaining`, which becomes the `remaining-asym-parts` of our `loop` and (2) the updated `final-body-parts`, which is the `final-body-parts` of our `loop`.

I think what made it difficult for me to grasp this is on the one hand getting distracted by the `let` and on the other hand having trouble
connecting the `(into final-body-parts (set [part (matching-part part)]))` of the `recur` with the `final-body-parts` of the `loop`. The former has three functions nested in each other, the latter is the name of a vector.


## into and conj

The example above also shows how the hobbit script uses an `into` to add a set of maps to a vector of maps inside a `recur`. That tripped me up, also when building my own loopers where I had to use `conj` instead. It's interesting how simple functions such as [`into`](https://clojuredocs.org/clojure.core/into) and [`conj`](https://clojuredocs.org/clojure.core/conj) become harder to undestand when they're part of a more difficult context.

In the end I found it helpful to try out a bunch of variations, starting with vectors containing integers, 
then replacing the integers with maps to get closer to what's in the hobbit script.

```clojure
(into [] [1 2 3])
; => [1 2 3]
(conj [] [1 2 3])
; => [[1 2 3]]
(into [9 8] [1 2 3])
; => [9 8 1 2 3]
(conj [9 8] [1 2 3])
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

My notes show it took me some effort to understand [`reduce`](https://clojuredocs.org/clojure.core/reduce). They say "struggling a bit with syntax" and "it's not obvious" and "had to re-read and re-learn", but I have no idea what it was that I found non-obvious. My best guess is that it was a bit of a leap for me to go from these examples

```clojure
(reduce + [1 2 3 4])
; => 10
(reduce + 15 [1 2 3 4])
; => 25
```

to a `reduce` that takes an anonymous function calling an other function to work on a vector of maps

```clojure
(reduce (fn [final-body-parts part]
	(into final-body-parts (set [part (matching-part part)])))
	[]
	asym-body-parts)
```

To be fair,
it is an improved implementation of a function that was explained earlier, so it is clear what this with `reduce` refactored
function is supposed to do.


## Comparing with python
Finally I wondered how I would write `hobbit.clj` in Python, [so I did](https://github.com/j19sch/clojure-brave-true/blob/master/python-comparisons/hobbit.py). I remember being somewhat disappointed with the result, as I had expected the differences to be
bigger. And that left me wondering if the differences would have been bigger, had I written the Python version before knowing
the Clojure version.

Comparing the two pieces of code now, the main difference seems to be how Clojure and Python deal with vectors and lists respectively.
Where in Clojure you use `reduce` and `loop` / `recur`, Python lets you use a for-loop on a list to go through the items one by one.
And where in Clojure you need `reduce` to sum a particular element in a vector of maps like this `(reduce + (map :size sym-parts))`, in Python list comprehension lets you do this like so `sum([part["size"] for part in sym_parts])`. And there's another difference in those two
pieces of code: where Python has both `+` and `sum()` depending on the number of things you want to add, Clojure's syntax with the operator
coming first, e.g. `(+ 1 2 3)`, lets you use `+` to adds as many things to each other as you want. I just tried `(+ 1)` and even that works.


And that almost concludes Chapter 3 of "Clojure for the Brave and True". There's only one thing left: the six exercises at the end.
