<!--
.. title: (clj 4) Learning about when, maps and closures
.. slug: clj4-learning-when-maps-closures
.. date: 2020-07-31 22:25:15 UTC+02:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description:
.. type: text
-->

It's been more than two months since I did any Clojure - for the obvious reasons. Luckily I did take notes as I proceeded with chapter 3 of "[Clojure for the Brave and True](https://www.braveclojure.com/)". So the plan is to process these notes into a blog post, which means this post will cover the sections "Data Structures" and "Functions" of that third chapter. Leaving me ready to proceed with the rest of the chapter, i.e. "Pulling It All Together" and the summary and exercises.


## Why is there a `when`?
The part about control flow is actually before the part about `and` and `or` which I talked about in my [previous post](link://slug/clj3-and-or-being-weird), but according to my notes I returned to it. I don't remember why to be honest.

The book provides the following example of `when`:
```clojure
(when true
	(println "Success!")
	"abra cadabra")
; => Success!
; => "abra cadabra"
```

<!-- TEASER_END -->

And if the condition is `false`, you get:
```clojure
(when false
	(println "First do!")
	"By Odin's Elbow!")
; => nil
```

So `when` allows you to do several things and return something when the condition is `true`, while it will return `nil` if the condition is `false`. The thing that got me curious is that you can do the same thing almost as easily with `if` and `do`:
```clojure
(if true
  (do (println "Success!")
      "abra cadabra")
  )
; => Success!
; => "abra cadabra"

(if false
  (do (println "First do!")
      "By Odin's Elbow!")
  )
; => nil
```

I can see two advantages to having the `when`. It needs fewer characters: two brackets and a space. It's also more readable, since there is no `do` and no indentation decisions because of that `do`. Is that enough reason? I honestly don't know, because I haven't written enough Clojure to decide if you use `when` often enough to make it worth it having it.

There is another difference, however, which I found out thanks to [vim-fireplace](https://github.com/tpope/vim-fireplace)'s `K` command, which looks up the symbol under the cursor with `doc`. `if` and `do` are Special Forms, while `when` is a Macro. What difference that makes, I don't know yet. In the section about functions in the same chapter, it does say on page 126:
> You’ll learn everything there is to know about macro calls and special forms in Chapter 7. For now, the main feature that makes special forms “special” is that, unlike function calls, they don’t always evaluate all of their operands.

And on page 127:
> Macros are similar to special forms in that they evaluate their operands differently from function calls, and they also can’t be passed as arguments to functions.

I made a note to revisit this when I get to Chapter 7. So one day there should be a link to that post here.


## Maps
With my Python background I had some trouble with the syntax of maps. With keywords being used as keys, they look like this:
```clojure
{:first-name "Charlie"
 :last-name "McFishwich"}
```
So the same characters as a Python dictionary but in a different order. This made me appreciate the value of practice. I won't be enjoying writing Clojure if I mess up the syntax of maps every time because of Python muscle memory.

Practice wasn't without its hurdles, though. When I defined a map and evaluated it like this:
```clojure
(def my-other-map (hash-map :a 100 :b 101 :c 102))
(my-other-map)
```
I got the error `ArityException Wrong number of args (0) passed to: PersistentArrayMap  clojure.lang.AFn.throwArity (AFn.java:429)`. 

Removing ther parantheses around the map's name resulted in:
```text
Error detected while processing function <SNR>48_printop[1]..<SNR>48_opfunc[40]..function <SNR>48_printop[1]..<SNR>48_opfunc:
line   21:
E20: Mark not set
E20: Mark not set
Press ENTER or type command to continue
```

The solution turned out to be to not have the parantheses (so just `my-other-map` on its own line), but then not use `cpp` to evaluate the statement, which evaluates the innermost statement, but use `cp$` (evaluate until end of the line) or `cp_` (evaluate current line).

Trying to evaluate the innermost form of a string in parantheses, gave me an impressive error message as well:
```text
ClassCastException class java.lang.String cannot be cast to class clojure.lang.IFn (java.lang.String is in module java.base of loader 'bootstrap'; clojure.lang.IFn is in unnamed module of loader 'app')  clojure-noob.core/eval6974 (form-init11099437324952859876.clj:5)
```

My notes tell me I didn't understand what exactly was going on here. Today, while writing this blog post, I went back in the book to the start of the chapter and there it explains that Clojure recognizes two kinds of structures: literal representations of data structures and operations. All operations take the form of opening parenthesis, operator, operands, closing parenthesis. Me putting the name of my hash map or a string literal in parantheses is neither of those structures, so makes sense I get an error.

Then for the scope of evaluation, `cpp` evaluates the innermost form. However I am on a line with just the name of my map, so I'm not sure what it tries to evaluate. Perhaps the whole file? In any case it's not what I want to evaluate, so it's ok that it throws an error instead of working.

Finally, I was surprised that all these three ways to get a value from a map are part of the language:
```clojure
(def my-map {:a 0 :b {:c "ho hum"}})

(get my-map :a)
; => 0

(my-map :a)
; => 0

(:a my-map)
; => 0
```

## Functions and returning functions
The section about functions ends with the following explanation about returning functions:
>By now you’ve seen that functions can return other functions. The returned functions are _closures_, which means that they can access all the variables that were in scope when the function was created. Here’s a standard example:

```clojure
(defn inc-maker
  "Create a custom incrementor"
  [inc-by]
  #(+ % inc-by))


(def inc3 (inc-maker 3))
(inc3 7)
; => 10
```

> Here, `inc-by` is in scope, so the returned function has access to it even when the returned function is used outside `inc-maker`.

I do not understand this explanation. In my mind the `inc-maker` returns a function that adds 3 to a number, so basically `(defn inc3 [number] (+ number 3))`, and I don't see how the scope of `inc-by` comes into play. (I am noticing now though that in the example `def` is used, not `defn` to create the `inc3` function.) So now I have some code that does make sense to me, while the explanation of the code doesn't, which is a somewhat weird place to be in.

In the hope of figuring this out I checked Wikipedia which says about [clojures](https://en.wikipedia.org/wiki/Closure_(computer_programming)): "Operationally, a closure is a record storing a function together with an environment." Which is in line with the explanation quoted above, but it doesn't help me understand.

It doesn't help either that the name of this language, Clojure, is a pun on the term 'closure', which makes me feel it is important to understand them. Some more searching didn't get me anything useful, although I did find [this post](https://groups.google.com/forum/#!msg/clojure/4uDxeOS8pwY/UHiYp7p1a3YJ) from [Rich Hickey](https://twitter.com/richhickey) about naming Clojure "Clojure":
> The name was chosen to be unique. I wanted to involve c (c#), l (lisp)
and j (java).

> Once I came up with Clojure, given the pun on closure, the available
domains and vast emptiness of the googlespace, it was an easy
decision.

And that's where I decided to accept I would not be understanding why closures are important when functions return other functions. Except that after writing the previous sentence, I started wondering if I could construct a more complicated function that returns a function, that would help me understand. I failed to construct such a function, since it wouldn't accept me binding a variable in either of the ways I tried to.

In any case, hopefully I will understand this one day. It does leave me with the feeling that the explanation about closures doesn't need to be in this part of the book. Perhaps it would be more in its place in chapter 7 which describes how Clojure runs your code.

---

As I did in my previous post, this postscript contains some smaller things I noticed and/or learned.

### Notes on blogging
Thanks to the combination of my notes, my play-around files and some re-playing around, it was fairly easy to write this blog post. I don't like leaving such a gap between learning and blogging, but it's good to know that when it happens, it's not a problem.

### Notes on Vim
I had to relearn a few things. Vim-fireplace will not connect to the REPL if you don't start one with `lein repl` first. Use `"+` in Vim to copy-paste to the system clipboard (thank you past me for the [cheatsheet](link://slug/clojure-vim-cheatsheet)).

Changing to gruvbox as Vim theme was a good idea. I did have to move the colorscheme line in my `.vimrc` because the statusbar was not green in normal mode.

In my previous post's postscrpit I was wondering how to get the result of an evaluation into my file. I have found a way, but it's quite a few keystrokes: copy the thing, paste the thing, evaluate it with `c!{motion}` which replaces it with the result of the evaluation, then `gcc` to make it into a comment. I might need to make a custom vim command to make that easier.

According to my notes I used `ctrl+n` (next match) and `ctrl+p` (previous match) for auto-completion, so I added those to my cheatsheet.
