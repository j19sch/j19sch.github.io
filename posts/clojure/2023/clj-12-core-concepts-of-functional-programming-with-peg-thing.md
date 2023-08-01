<!--
.. title: (clj 12) Core concepts of functional programming with Peg Thing
.. slug: clj-12-core-concepts-of-functional-programming-with-peg-thing
.. date: 2023-08-01 10:01:36 UTC+02:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description: 
.. type: text
-->

Chapter 5 of "[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)" explores two core concepts of functional programming: pure functions and immutable data structures. It wraps up with walking you through the [code of a game called "Peg Thing"](https://github.com/flyingmachine/pegthing)[^1], which uses *"everything you’ve learned so far: immutable data structures, lazy sequences, pure functions, recursion - everything!"*

[^1]: If you want to run it with `lein repl`, make sure to update the Clojure version in `project.clj`. I got the error message *"As of 2.8.2, the repl task is incompatible with Clojure versions older than 1.7.0."* while I have Clojure 1.10.2 installed. Luckily I came across a Stack Overflow post that mentioned there being a version number in `project.clj`.

<!-- TEASER_END -->

# so how does this whole Peg Thing work?

## function call graph

<figure class="figure">
	<a href="/images/2023/clj-12/clj-diagram.png" target="_blank">
		<img src="/images/2023/clj-12/clj-diagram.png" class="figure-img img-fluid rounded"
		alt="function call graph of Peg Thing"/>
	</a>
	<figcaption class="figure-caption text-center">Peg Thing function call graph (click for larger version)</figcaption>
</figure>


should I also make a sequence diagram? or a partial one for the `board` as arg? tried it, too messy

`prompt-rows` gets a board from `new-board` and passes it on to `prompt-empty-peg`


## two mutually recursive functions

> In our board creation functions, we saw how recursion was used to build up a value using immutable data structures. The same thing is happening here, only it involves two mutually recursive functions and some user input. No mutable attributes in sight!


```Clojure
(defn prompt-move
  [board]
  (println "\nHere's your board:")
  (print-board board)
  (println "Move from where to where? Enter two letters:")
  (let [input (map letter->pos (characters-as-strings (get-input)))]
    (if-let [new-board (make-move board (first input) (second input))]
      (user-entered-valid-move new-board)
      (user-entered-invalid-move board))))
```

```Clojure
(defn user-entered-valid-move
  "Handles the next step after a user has entered a valid move"
  [board]
  (if (can-move? board)
    (prompt-move board)
    (game-over board)))
```





## `make-move` is interesting
this uses move-peg and remove-peg instead of two removes and one place -> to what level have domain knowledge?

```Clojure
(defn make-move
  "Move peg from p1 to p2, removing jumped peg"
  [board p1 p2]
  (if-let [jumped (valid-move? board p1 p2)]
    (move-peg (remove-peg board jumped) p1 p2)))
```

`remove-peg` returns `board`, same with `move-peg`

see call graph: lots of board going around


## Clojures kind of hides its functional programming aka so much board

- `board` is used everywhere, in each function's scope, but also suggests it's the same thing (which it is conceptually, but not in the code)
- functions return result of final statement. no explicit `return`
	- *"Clojure automatically returns the last form evaluated."* (Ch. 3, Functions, Defining functions, Function Body)
- my note: I don't understand how immutable data works if multiple pieces of code can reference the same variable
	- do they though?

```Clojure
; from chapter 3
; Clojure automatically returns the last form evaluated.

(defn illustrative-function
  []
  (+ 1 304)
  30
  "joe")


(illustrative-function)
; => "joe"
```


## Other interesting things

## `let` is interesting

```Clojure
(defn add-pos
  "Pegs the position and performs connections"
  [board max-pos pos]
  (let [pegged-board (assoc-in board [pos :pegged] true)]
    (reduce (fn [new-board connection-creation-fn]
              (connection-creation-fn new-board max-pos pos))
            pegged-board
            [connect-right connect-down-left connect-down-right])))
```

https://clojuredocs.org/clojure.core/let
`(let [bindings*] exprs*)`
>  Evaluates the exprs in a lexical context in which the symbols in the binding-forms are bound to their respective init-exprs or parts therein.

explained in chapter 3
> `let` forms have two main uses. First, they provide clarity by allowing you to name things. Second, they allow you to evaluate an expression only once and reuse the result. 

> So, `let` is a handy way to introduce local names for values, which helps simplify the code.


## `triangular?` is cool

`triangular?` like `empty?`, cool to be able to use question marks

`can-move?`

> The question mark at the end of this function name indicates it’s a predicate function, a function that’s meant to be used in Boolean expressions.

mandatory when using question mark?
https://guide.clojure.style/#naming-predicates
The names of predicate methods (methods that return a boolean value) should end in a question mark (e.g., even?).
https://vlaaad.github.io/2019-03-30/question-marks-in-clojure



# Exercises

skipped them

for now?

also looked into one early



# so what about this chapter
> Let’s take a moment to appreciate how neat this code is. This is where you would usually perform mutation in an object-oriented program; after all, how else would you change the board? However, these are all pure functions, and they do the job admirably. I also like that you don’t need the overhead of classes to use these little guys. It feels somehow lighter to program like this.

kind of an oversell, but what else can you do if example needs to be simple enough for the book

what does this add to my post?

---

# Plantuml is more powerful than I thought

some good links on plantuml

see comments in plantuml file

see file

lot more powerful than I thought
