<!--
.. title: (clj 12) Core concepts of functional programming with Peg Thing
.. slug: clj-12-core-concepts-of-functional-programming-with-peg-thing
.. date: 2023-06-02 20:55:36 UTC+02:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description: 
.. type: text
-->

Chapter 5 of "[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)" explores two core concepts of functional programming: pure functions and immutable data structures. It wraps up with walking you through the [code of a game called "Peg Thing"](https://github.com/flyingmachine/pegthing), which uses *"[...] everything you’ve learned so far: immutable data structures, lazy sequences, pure functions, recursion—everything!"*


<!-- TEASER_END -->


# Clojures kind of hides its functional programming

- `board` is used everywhere, in each function's scope, but also suggests it's the same thing (which it is conceptually, but not in the code)
- functions return result of final statement. no explicit `return`
	- *"Clojure automatically returns the last form evaluated."* (Ch. 3, Functions, Defining functions, Function Body)
- my note: I don't understand how immutable data works if multiple pieces of code can reference the same variable
	- do they though?

```Clojure
(defn illustrative-function
  []
  (+ 1 304)
  30
  "joe")


(illustrative-function)
; => "joe"
```

# function call graph

<figure class="figure">
	<a href="/images/2023/clj-12/clj-diagram.png" target="_blank">
		<img src="/images/2023/clj-12/clj-diagram.png" class="figure-img img-fluid rounded"
		alt="function call graph of Peg Thing"/>
	</a>
	<figcaption class="figure-caption text-center">Peg Thing function call graph (click for larger version)</figcaption>
</figure>


# Exercises

skipped them

# Loose notes

- yay for good documentation to look up what certain built-in functions do
- `let` is interesting
- `add-pos` interesting because it actually reduces on a vector of functions
- `make-move`: interesting that this uses move-peg and remove-peg instead of two removes and one place -> to what level have domain knowledge?
- `can-move?`: The question mark at the end of this function name indicates it’s a predicate function, a function that’s meant to be used in Boolean expressions.


# so what about this chapter
> Let’s take a moment to appreciate how neat this code is. This is where you would usually perform mutation in an object-oriented program; after all, how else would you change the board? However, these are all pure functions, and they do the job admirably. I also like that you don’t need the overhead of classes to use these little guys. It feels somehow lighter to program like this.

kind of an oversell, but what else can you do if example needs to be simple enough for the book

---

# some good links on plantuml
