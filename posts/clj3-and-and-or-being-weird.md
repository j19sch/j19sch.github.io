<!--
.. title: (clj 3) Clojure's 'and' and 'or' are weird (but not really)
.. slug: clj3-and-or-being-weird
.. date: 2020-05-16 21:25:15 UTC+02:00
.. tags: clojure
.. category: clojure
.. link: 
.. description:
.. type: text
-->

## The basics of Clojure's `and` and `or`

Early in [chapter 3](https://www.braveclojure.com/do-things/#Control_Flow) of the [Brave and True](https://www.braveclojure.com/)-book the Boolean operators `and` and `or` are introduced:
> Clojure uses the Boolean operators `or` and `and`. `or` returns either the first truthy value or the last value. `and` returns the first falsey value or, if no values are falsey, the last truthy value.

This explanation is followed by some examples:
```clojure
(or false nil :large_I_mean_venti :why_cant_I_just_say_large)
; => :large_I_mean_venti

(or (= 0 1) (= "yes" "no"))
; => false

(or nil)
; => nil
```
```clojure
(and :free_wifi :hot_coffee)
; => :hot_coffee

(and :feelin_super_cool nil false)
; => nil
```

What I found remarkable about this is that `and` and `or` do not return booleans in all cases. Before I go into that, let's back up a second.

<!-- TEASER_END -->

After reading the above description of `and` and `or`'s behavarior, reading [their](https://clojuredocs.org/clojure.core/and) [official](https://clojuredocs.org/clojure.core/or) documentation, and playing around a bit with code, I discovered a description of their behavior that works better for me:

- both `and` and `or` return the last value they evaluate;
- `or` stops evaluating at the first truthy value it evaluates, since an `or` needs only one true value to evaluate to true;
- `and` stops evaluating at the first falsy value it evaluates, since an `and` needs only one false value to evaluate to false.

In Clojure only `false` and `nil` are falsy, everything else is truthy - as demonstrated by the following examples.

```clojure
(and true true)        ; => true
(and true :tree)       ; => :tree
(and true false true)  ; => false
(and true nil true)    ; => nil
```

```clojure
(or false true false)     ; => true
(or false :falcon false)  ; => :falcon
(or false false)          ; => false
(or false nil)            ; => nil
```

 Finally, there's `(and)` evaluating to `true`, while `(or)` evaluates to `nil`, which is mentioned in [their](https://clojuredocs.org/clojure.core/and) [respective](https://clojuredocs.org/clojure.core/or) doc pages. Not exactly sure why they do that, but who am I to disagree?


## Yet they don't only return `true` or `false`

Since `and` and `or` are boolean operators, I figured they would always return either `true` or `false`. That is how you use them, right? Give them some expressions that evaluate either to `true` or `false` and then depending if you string them together with `and` or `or`, you get `true` or `false` back. And that turns out to be not the case: `and` and `or` return the result of their last evaluation. If that's `true`, you get `true` back, but if it's `"tree"` or `:falcon`, that's what you get. So I started to think why these operators behaved that way.


### A theoretical argument
Earlier in the Brave and True-book it explained that Clojure only has two types of things: literal representations of data structures (like numbers, maps, and vectors) and operations. With these two you create expressions (aka forms) and "Clojure evaluates every form to produce a value. (p 91)" Combine this with the basic idea of functional programming, i.e. functions as mathemetical functions, you expect functions - and that's what the `and` and `or` operations are - to take input, transform it, and return the transformed input as their output.

Looking at it that way, in some vague intuitive conceptual way, it does make sense to me that `and` and `or` return the last form they evaluated instead of the last form they evaluated converted to either `true` or `false`. If you need that conversion, you can do that yourself.

Also Clojure's [`println`](https://clojuredocs.org/clojure.core/println) returns `nil`, so...

### A practical argument
I'm ok with their being only a theoretical reason for this, keeping the language conceptually consistent. Yet I wondered if there was a practical usage for this behavior of `and` and `or`. A possible use I saw was that you could chain functions. For instance, with `and` the first function will either return a `truthy` value, making the `and` return that value; or that first function returns `false` or `nil`, meaning the second function would be evaluated. And so on, until either a function returns something truthy or you get a `false` or `nil` from the last one.

So that's what I built here:
```Clojure
(defn mult2_if_int [input]
	(and 
		(if (integer? input) true)
		(* input 2)
	)
)
```

Which does the following:
```Clojure
(mult2_if_int 4)       ; => 8
(mult2_if_int "four")  ; => nil
```

However, this way of doing the same thing looks more readable to me:
```Clojure
(defn mult3_if_int [input]
	(if (integer? input)
		(* input 3)
	)
)

(mult3_if_int 4)       ; => 12
(mult3_if_int "four")  ; => nil

```

That wouldn't work as well with multiple conditions, but a quick search showed that that's what Clojure's [`cond`](http://clojuredocs.org/clojure.core/cond) and [`case`](http://clojuredocs.org/clojure.core/case) are for. So doing the same as above with `cond`:
```Clojure
(defn mult4_if_int [input]
	(cond
		(integer? input) (* input 4)
	:else nil)
)
(mult4_if_int 2)      ; => 8
(mult4_if_int "two")  ; => nil
```

So for `and` I have trouble seeing a use case for this behavior. For `or`, based on an [example](https://clojuredocs.org/clojure.core/or#example-5e4010ebe4b0ca44402ef82d) in the Clojure docs, we can use it to return a default value if our function returns `nil`:
```Clojure
(or (mult2_if_int 4) "that was not a number")       ; => 4
(or (mult2_if_int "four") "that was not a number")  ; => "that was not a number"
```

### Surely Python does something different
Python is my point of reference for programming languages, because it's the one I'm most familiar with. Throughout this exploration of Clojure's `and` and `or`, I was thinking that Python does not show this behavior. That is, until I checked:
``` Python
True and True            # => True
True and "tree"          # => 'tree'
True and False and True  # => False
True and None and True   # => None
```

```Python
False or True or False      # => True
False or "falcon" or False  # => 'falcon'
False or False              # => False
False or None               # => None
```

And in the [Python docs](https://docs.python.org/3/reference/expressions.html#boolean-operations), which I must say are excellent as always, I found:
> Note that neither `and` nor `or` restrict the value and type they return to `False` and `True`, but rather return the last evaluated argument. This is sometimes useful, e.g., if `s` is a string that should be replaced by a default value if it is empty, the expression `s or 'foo'` yields the desired value. Because `not` has to create a new value, it returns a boolean value regardless of the type of its argument (for example, `not 'foo'` produces `False` rather than `''`.)

And this behavior of `not` is also present in Clojure:
```Clojure
(not "foo")  ; => false
```

So I suppose the conclusion is that even though it may feel a bit weird to have `and` and `or` not only returning `true` or `false`, Clojure is not any weirder in this respect than some other languages.


## Some notes on Clojure, Vim, and blogging
To close off this post, I'd like to share some smaller things I noticed and/or learned about Clojure and vim.

### Clojure
In a previous post [(clj 1)](/blog/clj1-deciding-on-an-editor/) I wrote I have a vague notion of what a "form" is, but wouldn't be able to explain it. Well, chapter 3 of the Brave and True-book explains "form" refers to valid code and that it will sometimes use "expression" as a synonym. I had actually read this before writing that earlier blog post, so that shows the value of re-reading.

When trying to evaluate a form in a new file I created to play around in with `and` and `or`, I got the following error:  
`FileNotFoundException Could not locate clojure_noob/namespace__init.class or clojure_noob/namespace.clj on classpath. 
Please check that namespaces with dashes use underscores in the Clojure file name.  clojure.lang.RT.load (RT.java:456)`  
I fixed it by copy-pasting the namespace declaration of my `core.clj` file `(ns clojure-noob.core (:gen-class))` to the top of the new file. I have no idea if that's the proper way to use namespaces, but I'll learn that in [chapter 6](https://www.braveclojure.com/organization/#Creating_and_Switching_to_Namespaces) of the Brave and True-book.

It surprised me that after making changes to a function definition and using `:Require` or `Require!` to reload a namespace, I still first had to evaluate the function definition (`cpp`) to be able to use the update version.

Function definitions go in parantheses. Everything is a list!


### Vim
I switched to the [gruvbox](https://github.com/morhetz/gruvbox) color scheme, since it provides more contrast than [minimalist](https://github.com/dikiaap/minimalist).

It's great to have [my own cheatsheet](/my-projects/clojure-vim-cheatsheet) to look things up in.

If vim-fireplace can evaluate a form and add it to the buffer as a comment, I haven't found out how.

I had to install `vim-gtk3` to be able to copy from vim to my system's clipboard.

Highlighting the line the cursor is in with `set cursorline` looks good, until it seems to introduce lag in file navigation.

Instead of looking up the Clojure docs on the internet, I should hit `K`. Thank you, vim-fireplace!

The parantheses help from vim-sexp is helpful, except when it isn't. I still need to find the best way to add a matching paranthesis or bracket to an orphaned one.


### Blogging
Writing these blog posts is slowing me donw significantly, but it is also forcing (encouraging?) me to engage deeper with Clojure. So for now, I'm seeing that as a good thing. Also, it can't hurt to spend some extra time on the basics. I've heard too many experts say when asked how to become excellent at something: "basics, basics, basics".
