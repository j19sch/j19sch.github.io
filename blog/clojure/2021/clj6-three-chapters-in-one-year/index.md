<!--
.. title: (clj 6) Three chapters in one year
.. slug: clj6-three-chapters-in-one-year
.. date: 2021-05-08 10:53:25 UTC+02:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description:
.. type: text
-->

It's been a bit more than a year since I posted my [first blog post](link://slug/clj0-diving-straight-in) about learning Clojure. And it's been five months since my [last blog post](link://slug/clj5-loop-and-recur-into-and-conj) about it. So far I've made it through the first three chapters[^1] of "[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)". Instead of commenting on my learning pace at the start of every post, I've decided that this pace is the pace that works for me at this time, so there's no need to keep revisiting the topic.

Something I do want to mention is that one thing that triggered me to do some more Clojure was [this episode](https://itrevolution.com/the-idealcast-episode-10/) of Gene Kim's excellent [Idealcast](https://itrevolution.com/the-idealcast-podcast/) podcast with [Michael Nygard](https://www.michaelnygard.com/), in which they spend some time talking about Clojure.


## Vim macros
The exercises at the end of chapter 3 got me to try out a lot of things, so I got bored having to type in the commands to copy a line (`yy`), paste it (`p`), replace it by its evaluation (`c!$`), comment it out (`gcc`), and add a "`=>`" to mark it as output. So I learned about Vim macros and recorded that sequence to run when I hit `@c`. At the end of my [(clj 4)](link://slug/clj4-learning-when-maps-closures) post I mentioned I might have to do this. Guess that moment came sooner than I expected.

<!-- TEASER_END -->

The macro works great as long as you don't try to evaluate a line that throws an exception. You do get the same weird line of output every time (i.e. `a =>`), so it's easy enough to recognize. Wondering if and how Vim macros are stored, I was glad to discover they are stored automatically if you run Vim in noncompatible mode (which I do). So I haven't bothered yet to store the macro in my `.vimrc` with the `let` command.


## Exercise 1 - using some functions
The first exercise asks you to use the `str`, `vector`, `list`, `hash-map`, and `hash-set` functions. I remembered to hit `shift+k` to read the documentation on `str` and that reminded me to try using these functions with different numbers of arguments:

```clojure
(str) 
; => ""
(str 1)
; => "1" 
(str 1 "a")
; => "1a"
```

I'm still amazed by this behavior. It gives me a feeling of simplicity and clarity.

### Lists and list literals
One problem I ran into is applying those functions on a list:

```clojure
(str 1 (2 3)) 
; ClassCastException class java.lang.Long cannot be cast to class clojure.lang.IFn
```

Luckily, I wanted to double-check I was using the word "list" correctly in this blog post, which led me to the Clojure documentation on [lists](https://clojure.org/guides/learn/sequential_colls#_lists) and to the solution[^2]. Lists are evaluated by invoking the first element as a function, so you need to quote it to prevent evaluation:

```clojure
(str 1 '(2 3))
; => "1(2 3)"
```

### Non-keywords as keys in hash maps
Using the `hash-map` function had me wonder why the book consistenly uses keywords (e.g. `:name`) as the key in a hash map and not something else like a string or an integer. So I tried it out:

```clojure
(hash-map 1 2)
; => {1 2}
(hash-map :1 2)
; => {:1 2}
(hash-map "a" "b")
; => {"a" "b"}
```

Seems to work just fine, right? But then I remembered there are different ways to retrieve something from a hash map, so I tried those out.

```clojure
(def my-hash (hash-map 1 2))

my-hash
; => {1 2}
(my-hash 1)
; => 2
(get my-hash 1)
; => 2
(1 my-hash)
; ClassCastException class java.lang.Long cannot be cast to class clojure.lang.IFn
```

```clojure
(def my-other-hash (hash-map :1 2))

my-other-hash
; => {:1 2}
(:1 my-other-hash)
; => 2
```

In [(clj 4)](link://slug/clj4-learning-when-maps-closures) I mentioned I was surprised about the three different ways to get a value from a map in Clojure. I don't think the example above explains why there's three, but it does show that by using keywords as keys in hash maps, at least you keep your options open.


## Exercise 2 - writing a simple function
Exercise 2 asks you to write function that takes a number and adds 100 to it. It had me think briefly if I should write `(+ 100 number)` or `(+ number 100)`. The former made more sense to me. I'm doing `+ 100` to the number rather than `+` the number to `100`, but that might just be how my mind works.

### Arity overloading
I ended up with this function:

```clojure
(defn plus-100-arity-overloading
  " add 100 to a number; return 100 if no argument given"
  ([number]
    (+ 100 number))
  ([]
    (plus-100-arity-overloading 0))
  )
```

As you can see, inspired by some of the functions from Exercise 1, I used arity overloading so that if you call the function without any arguments, it returns `100`. In my first version I returned `100` directly if the function was called withour arguments. After checking the section about arity overloading in the book, I realized that you want the function to call itself, filling in the omitted argument (`number` in this case). Not that it doesn't work if you don't, but you could get some unexpected behaviors:

```clojure
(defn plus-100-messed-up
  ([]
   "one hundred")
  ([number]
   (+ 100 number)
   )
  )

(plus-100-messed-up)
; => "one hundred"
(plus-100-messed-up 0)
; => 100
```


## Exercise 3 - change the function inc-maker to dec-maker

Exercise 3 wants you to take the `inc-maker` function shown earlier in the chapter and change it into a `dec-maker`. That's easy enough: copy-paste the `inc-maker`, rename it, and change a `+` into a `-`:[^3]

```clojure
(defn dec-maker
  [dec-by]
  #(- % dec-by))

(def dec9 (dec-maker 9))

(dec9 10)
; => 1
```

### Revisiting the concept of closures

However, the book shows you the `inc-maker` function to illustrate how a returned function is a "closure". And as you can read in [(clj 4)](link://slug/clj4-learning-when-maps-closures), I did not understand the explanation, when I first came across it. Since it still bugged me that I don't understand, I decided to give it another try.

The explanation in the book is as follows:
> By now you’ve seen that functions can return other functions. The returned functions are *closures*, which means that they can access all the variables that were in scope when the function was created.

> Here, `inc-by` is in scope, so the returned function has access to it even when the returned function is used outside `inc-maker`.

What I noticed back then and re-noticed just now is that `inc-maker` and `dec-maker` are defined with `defn`, so as a function. However, `inc3` from the book and `dec9` from the exercise (see above) are defined with `def`, which is used to bind a name to a value. So I checked the [Clojure documentation on `defn`](https://clojuredocs.org/clojure.core/defn) and it says `defn` is the same as `(def name (fn [params* ] exprs*))`:

```clojure
(def def-dec9 (fn [num] (- num 9)))
(def-dec9 10)
; => 1
```

So that's a different syntax from the `inc-maker`/`dec-maker` example. Using Clojure's [`type`](https://clojuredocs.org/clojure.core/type) confirms this difference, but I have no idea what it means exactly:

```clojure
(type dec9)
; => clojure_noob.core$dec_maker$fn__1458

(type def-dec9)
=> clojure_noob.core$def_dec9

```

Having revisited all of this, the concept "closures" of does make a little more sense to me, although I still wouldn't be able to really explain it. I did a search in the book and "closure" occurs twice: once in the explanation of `inc-maker` and once in the index. So I should be fine with my current understanding - or my lack thereof.



[^1]: I've only done the first three exercises at the end of chapter 3, but the authors said it's fine to skip the other three exercises and revisit them after chapters 4 and 5. I tried solving exercise 4 for a bit and decided it's better to skip and revisit.

[^2]: I checked the explanation on lists in "Clojure for the Brave and True". It does tell you to use the single quote, but it also says the explanation won't be covered until Chapter 7.

[^3]: Which got me curious about providing more than two arguments to the `-` function. Turns out it works as you'd expect. `(- 10 1 2)` gives you 7. `(- 10 1 -2)` gives you 11. `(- 10 -1 2)` gives you 9.[^4]

[^4]: Turns out code blocks do not work in footnotes, but footnotes in footnotes do.
