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


Is the maroon in the diagram needed to talk about `board` being passed around?

---

Chapter 5 of "[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)" explores two core concepts of functional programming: pure functions and immutable data structures. It wraps up with walking you through the [code](https://github.com/flyingmachine/pegthing)[^1] of a game called ["Peg Thing"](https://www.braveclojure.com/functional-programming/#Peg_Thing), which uses *"everything you’ve learned so far: immutable data structures, lazy sequences, pure functions, recursion - everything!"*

[^1]: If you want to run it with `lein repl`, make sure to update the Clojure version in `project.clj`. I got the error message *"As of 2.8.2, the repl task is incompatible with Clojure versions older than 1.7.0."* while I have Clojure 1.10.2 installed. Luckily I came across a Stack Overflow post that mentioned there being a version number in `project.clj`.

<!-- TEASER_END -->

# So what is this Peg Thing?

For a full description and the code of Peg Thing, you can follow the links in the paragraph above[^2]. In this post I'll only share what's relevant to describe what I learned about functional programming through Peg Thing.

[^2]: Do note there is at least one small difference between the code on GitHub and the code from the book. The GitHub code has `prompt-move` calling `successful-move` for valid moves and handling invalid moves itself. In the book, `prompt-move` calls `user-entered-valid-move` or `user-entered-invalid-move` for valid and invalid moves respectively. This post uses the code from GitHub.

The code of Peg Thing consists of four parts:

- create the board, which contains 11 functions and 1 variable
- represent board textually and print, which contains 7 functions and 5 variables
- interaction, which contains 9 functions, including the `-main` function
- move pegs, which contains 8 functions

There are also calls to 3 side effect funtcions: `println`, `read-line`, and `System/exit`.

## A function call graph

Since that's quite a lot, I made a function call graph:

<figure class="figure">
  <a href="/images/2023/clj-12/clj-diagram.png" target="_blank">
    <img src="/images/2023/clj-12/clj-diagram.png" class="figure-img img-fluid rounded"
    alt="function call graph of Peg Thing"/>
  </a>
  <figcaption class="figure-caption text-center">Peg Thing function call graph (click for larger version)</figcaption>
</figure>

Every box is a function (normal font) or a variable (italicized). Every arrow is a call from a function or variable to another function or variable. The blue arrows from `-main` to `prompt-rows` to `prompt-empty-peg` to `prompt-move` is what sets up the game. The purple calls back-and-forth between `prompt-move` and `succesful-move` are the main game loop, ending eventually with a call to `game-over`. The dashed lines are the calls to the three functions with side effects. Finally, the functions in maroon are functions that take `board` as an input parameter.


### Limits of this graph
One important thing to note is that the graph does not communicate the order in which one function calls other functions. For example, here's the code of `prompt-rows`:

``` {.Clojure linenos=true}
(defn prompt-rows
  []
  (println "How many rows? [5]")
  (let
      [rows (Integer. (get-input 5))
        board (new-board rows)]
      (prompt-empty-peg board)))

```

Let me walk you through this code line-by-line:

1. `defn prompt-rows` tells Clojure we want to define a function called `prompt-rows`
1. `[]` are the input paramers of our function, so in this case none
1. `(println "How many rows? [5]")` prints the text in double quotes to the terminal
1. `let` allows us to define to two variables in the current scope, `rows` and `board`
1. `rows` is the number of rows as entered by the user
1. `board` is a new board returned by the `new-board` function, with the number of `rows` specified
1. `prompt-empty-peg board` calls the `prompt-empty-peg` function with `board` as argument

So while the diagram shows three outgoing arrows from `prompt-rows`, the one to `prompt-empty-peg` is the most important one. To provide that call with its argument, however, we need the calls to `get-input` and `new-board`. I tried to make a sequence diagram to complement the function call diagram, but that got too messy too quickly to be helpful.




---

structure: eg `prompt-rows`



What is it trying to show? pure functions and immutable data structures

pure function:
  same input -> same output (referentially transparent);
  no side effects (no changes observable outside the function itself)

immutable data
  Recursion Instead of for/while
  Function Composition Instead of Attribute Mutation

- function call graph with explanation
- `board` being passed around, but data immutable
- side effects on the sides




# What did I learn from Peg Thing?

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

## move-peg

- `(place-peg (remove-peg board p1) p2))`
- remove-peg returns board!
  - instead of returning nothing
  - returning nothing would be side-effect and non-immutable data
  - option 1
    - board
    - remove_peg(board)
  - option 2
    - board
    - board = remove_peg(board)
  - both don't use classes, but are still object-oriented in their approach as opposed to functional, except
    - board
    - board2 = remove_peg(board)
    - avoided through immutable data, no need for `board` and `board2`, just functions calling functions, so no `main` in that sense fron which everything branches AND returns (imperative programming)


> In computer science, functional programming is a programming paradigm where programs are constructed by applying and composing functions. It is a declarative programming paradigm in which function definitions are trees of expressions that map values to other values, rather than a sequence of imperative statements which update the running state of the program. - https://en.wikipedia.org/wiki/Functional_programming

or is it declaritive? or a specific kind of imperative, i.e. functional, i.e. function trees


  - I don't understand how immutable data works if multiple pieces of code can reference the same variable
    - perhaps clearer after knowing the whole program
    - => it's all linearly/recursively functions calling functions
      - see explanation prompt-rows
      - make a diagram? with plantuml? done
        - change color of error handling
        - highlight main loop: prompt-move, succesful-move, game-over
        - only one thing calls new-board
      - kind of hidden that board is not changed, but new data structures are created, partially because board is used as name
      - each of the four parts has a pyramid structure


- `make-move` is interesting
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


# Two other, smaller interesting things

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




---

# (bonus) Plantuml is more powerful than I thought

some good links on plantuml

see comments in plantuml file

see file

lot more powerful than I thought


---

# Exercises

skipped them

for now?

also looked into one early



# so what about this chapter
> Let’s take a moment to appreciate how neat this code is. This is where you would usually perform mutation in an object-oriented program; after all, how else would you change the board? However, these are all pure functions, and they do the job admirably. I also like that you don’t need the overhead of classes to use these little guys. It feels somehow lighter to program like this.

kind of an oversell, but what else can you do if example needs to be simple enough for the book

what does this add to my post?