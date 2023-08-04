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


Chapter 5 of "[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)" explores two core concepts of functional programming: pure functions and immutable data structures. It wraps up with walking you through the [code](https://github.com/flyingmachine/pegthing)[^1] of a game called ["Peg Thing"](https://www.braveclojure.com/functional-programming/#Peg_Thing), which uses *"everything you’ve learned so far: immutable data structures, lazy sequences, pure functions, recursion - everything!"*

[^1]: If you want to run it with `lein repl`, make sure to update the Clojure version in `project.clj`. I got the error message *"As of 2.8.2, the repl task is incompatible with Clojure versions older than 1.7.0."* while I have Clojure 1.10.2 installed. Luckily I came across a Stack Overflow post that mentioned there being a version number in `project.clj`.


# So what is this Peg Thing?

For a full description and the code of Peg Thing, you can follow the links in the paragraph above[^2]. In this post I'll only share what's relevant to describe what I learned about functional programming through Peg Thing.

[^2]: Do note there is at least one small difference between the code on GitHub and the code from the book. The GitHub code has `prompt-move` calling `successful-move` for valid moves and handling invalid moves itself. In the book, `prompt-move` calls `user-entered-valid-move` or `user-entered-invalid-move` for valid and invalid moves respectively. This post uses the code from GitHub.


<!-- TEASER_END -->


The code of Peg Thing consists of four parts:

- create the board, which contains 11 functions and 1 variable
- represent board textually and print, which contains 7 functions and 5 variables
- interaction, which contains 9 functions, including the `-main` function
- move pegs, which contains 8 functions

There are also calls to 3 side effect funtcions: `println`, `read-line`, and `System/exit`.

## A function call graph

Since that's quite a lot of functions and variables, I made a function call graph:

<figure class="figure">
  <a href="/images/2023/clj-12/clj-diagram.png" target="_blank">
    <img src="/images/2023/clj-12/clj-diagram.png" class="figure-img img-fluid rounded"
    alt="function call graph of Peg Thing"/>
  </a>
  <figcaption class="figure-caption text-center">Peg Thing function call graph (click for larger version)</figcaption>
</figure>

Every box is a function (normal font) or a variable (italicized). Every arrow is a call from a function or variable to another function or variable.

The blue arrows from `-main` to `prompt-rows` to `prompt-empty-peg` to `prompt-move` is what sets up the game. The purple calls back-and-forth between `prompt-move` and `succesful-move` are the main game loop, ending eventually with a call to `game-over`. The dashed lines are the calls to the three functions with side effects.


## Limits of the functional call graph: sequence
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

Let's walk through this code line-by-line:

1. `defn prompt-rows` tells Clojure we want to define a function called `prompt-rows`.
1. `[]` are the input paramers of our function, so in this case none.
1. `(println "How many rows? [5]")` prints the text in double quotes to the terminal.
1. `let` allows us to define to two variables in the current scope, `rows` and `board`.
1. `rows` is the number of rows entered by the user as an integer.
1. `board` is a new board with the number of `rows` specified, returned by the `new-board` function.
1. `(prompt-empty-peg board)` calls the `prompt-empty-peg` function with `board` as argument.

So while the function call graph shows four outgoing arrows from `prompt-rows`, the one to `prompt-empty-peg` is the most important one. To provide that call with its argument, however, we need the calls to `println`, `get-input`, and `new-board`.

I tried to make a sequence diagram, but that seemed to get messy too quickly. A second attempt some time later was more successful. It shows the board setup in detail with `prompt-rows`, `prompt-empty-peg`, and `prompt-move`. For context I also added the main game loop functions of Peg Thing. 

<figure class="figure">
  <a href="/images/2023/clj-12/clj-seq-diagram.png" target="_blank">
    <img src="/images/2023/clj-12/clj-seq-diagram.png" class="figure-img img-fluid rounded"
    alt="sequence diagram of Peg Thing"/>
  </a>
  <figcaption class="figure-caption text-center">Peg Thing sequence diagram (click for larger version)</figcaption>
</figure>


# What does Peg Thing teach about functional programming?

Before going into Peg Thing, chapter 5 of the book talks about pure functions and immutable data.

A pure function is a function that (1) returns the same result if given the same arguments; (2) does not cause any side effects. The advantage of a pure function is that if you know what arguments go into the function, you'll know what the function will return and you know it won't do anything else. So it allows you to think about the function without having to worry about anything else.

This is also where immutable data comes into play. Being allowed to change data (think about things like state and attributes here) is being allowed to create side effects. By not allowing this, i.e. by having immutable data, Clojure avoids these kinds of side effects.


## Function composition
That does lead to the question: if you can't change data, then how do you get anything done? The answer is function composition: combining functions so that the return value of one function is passed to another.

You can see this in both the call graph and the sequence diagram of Peg Thing. The pyramid shape of "create the board", "represent board textually and print it", and "move pegs" show how Peg Things consists of functions calling functions calling functions. There's not a big main function, doing things step-by-step. It's even clearer in the sequence diagram where we can see `prompt-empty-peg` calling `(prompt-move (remove-peg board (letter->pos (get-input "e"))))`, which goes four levels deep.

## But what about all the `board`s?

Another thing you may have noticed in the sequence diagram, is that `board` seems to get passed around a lot. It certainly did confuse me initially: if the board changes during a game of Peg Thing and `board` gets passed around, how is that immutable data?

Going through the code, made me realise that this question came from my non-functional programming intuitions. It's not the case that `board` gets passed around and changed. A lot of functions in Peg Thing require a board as argument and return a thing that's a board. It's however not true that a `board` variable gets passed into the function as argument and that same variable but changed, comes out as the return value.


```Clojure
; called by move-peg, called by make-move, called by prompt-move
(defn place-peg
  "Put a peg in the board at given position"
  [board pos]
  (assoc-in board [pos :pegged] true))
; assoc-in returns a new hash map with the change

(defn remove-peg
  "Take the peg at given position out of the board"
  [board pos]
  (assoc-in board [pos :pegged] false))
; assoc-in returns a new hash map with the change

(defn move-peg
  "Take peg out of p1 and place it in p2"
  [board p1 p2]
  (place-peg (remove-peg board p1) p2))
; returns what place-peg returns

(defn make-move
  "Move peg from p1 to p2, removing jumped peg"
  [board p1 p2]
  (if-let [jumped (valid-move? board p1 p2)]
    (move-peg (remove-peg board jumped) p1 p2)))
; returns what move-peg returns or nil because no explicit else

(defn prompt-move
  [board]
  (println "\nHere's your board:")
  (print-board board)
  (println "Move from where to where? Enter two letters:")
  (let [input (map letter->pos (characters-as-strings (get-input)))]
    (if-let [new-board (make-move board (first input) (second input))]
      (successful-move new-board)
      (do
        (println "\n!!! That was an invalid move :(\n")
        (prompt-move board)))))
; new-board is via let, so only in scope of function, is either board or nil, value determines next step is the then or the else

```

# Summary


## pure functions and immutable data

### pure functions

> A function is pure if it meets two qualifications:
> - It always returns the same result if given the same arguments. This is called *referential transparency*, and you can add it to your list of $5 programming terms.
> - It can’t cause any side effects. That is, the function can’t make any changes that are observable outside the function itself - for example, by changing an externally accessible mutable object or writing to a file.

> Lucky for you, Clojure makes your job easier by going to great lengths to limit side effects—all of its core data structures are immutable. You cannot change them in place, no matter how hard you try!

### immutable data

- Recursion Instead of for/while
- Function Composition Instead of Attribute Mutation

> Combining functions like this—so that the return value of one function is passed as an argument to another—is called function composition. In fact, this isn’t so different from the previous example, which used recursion, because recursion continually passes the result of a function to another function; it just happens to be the same function. In general, functional programming encourages you to build more complex functions by combining simpler functions.

### peg thing
> In our board creation functions, we saw how recursion was used to build up a value using immutable data structures. The same thing is happening here, only it involves two mutually recursive functions and some user input. No mutable attributes in sight!

### Summary
> Pure functions are referentially transparent and side-effect free, which makes them easy to reason about. To get the most from Clojure, try to keep your impure functions to a minimum. In an immutable world, you use recursion instead of for/while loops, and function composition instead of successions of mutations. Pure functions allow powerful techniques like function composition functions and memoization. They’re also super fun!



## A tree of `board`s
- three of the areas are tree-shaped in the call graph
  - each of the four parts has a pyramid structure
- `new-board` only called by `prompt-rows`
- side effects on the sides

You might have noticed in the sequence diagram that `board` seems to get passed around a lot.

- passing `board` but a different one

  - Clojures kind of hides its functional programming aka so much board
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


- two mutually recursive functions instead of a main function managing stuff

### two mutually recursive functions

> In our board creation functions, we saw how recursion was used to build up a value using immutable data structures. The same thing is happening here, only it involves two mutually recursive functions and some user input. No mutable attributes in sight!



```Clojure
; book version

(defn prompt-move
  [board]
  (println "\nHere's your board:")
  (print-board board)
  (println "Move from where to where? Enter two letters:")
  (let [input (map letter->pos (characters-as-strings (get-input)))]
    (if-let [new-board (make-move board (first input) (second input))]
      (user-entered-valid-move new-board)
      (user-entered-invalid-move board))))

(defn user-entered-valid-move
  "Handles the next step after a user has entered a valid move"
  [board]
  (if (can-move? board)
    (prompt-move board)
    (game-over board)))
```

```Clojure
; GitHub repo version

(defn prompt-move
  [board]
  (println "\nHere's your board:")
  (print-board board)
  (println "Move from where to where? Enter two letters:")
  (let [input (map letter->pos (characters-as-strings (get-input)))]
    (if-let [new-board (make-move board (first input) (second input))]
      (successful-move new-board)
      (do
        (println "\n!!! That was an invalid move :(\n")
        (prompt-move board)))))

(defn successful-move
  [board]
  (if (can-move? board)
    (prompt-move board)
    (game-over board)))
```



### move-peg: functional and only a little imperative

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
      - kind of hidden that board is not changed, but new data structures are created, partially because board is used as name


`remove-peg` returns `board`, same with `move-peg`




# Two other interesting things in Peg Thing's code

## `let` is surprising

The [Clojure docs say](https://clojuredocs.org/clojure.core/let) that `let`'s syntax is `(let [bindings*] exprs*)` and that it *"evaluates the exprs in a lexical context in which the symbols in the binding-forms are bound to their respective init-exprs or parts therein."* I did not find that particularly helpful.

The Brave Clojure-book does a better job by saying:

> So, `let` is a handy way to introduce local names for values, which helps simplify the code.

What surprised me about it, is that `let` doesn't just let you assign a local name to a variable[^3]. It lets you assign a local name to what's returned by an expression and then use that return value within the `let`. For example, in Peg Thing, there's the `add-pos` function:

[^3]: Which would be a curious concept anyway, with the immutable data structures.

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

The `[pegged-board (assoc-in board [pos :pegged] true)]` makes the return value of `(assoc-in board [pos :pegged] true)` available as `pegged-board`, which is then used in the `reduce` function. So, you can 'hide' quite some logic in a `let`.



## `triangular?` is cool

As you can see in the call graph, there are quite some functions whose name ends with a question mark, for example `triangular?` and `valid-move?`. I really like this is possible and prefer it over an alternative like `is_triangular`.

Turns out it's not only possible, but it's [part of the Clojure style guide](https://guide.clojure.style/#naming-predicates) and they're called predicate functions. I also found a blog post by [vlaaad](https://github.com/vlaaad/) about ["Question marks in Clojure"](https://vlaaad.github.io/2019-03-30/question-marks-in-clojure) going a bit deeper into this topic.



---

# (post script) Plantuml is more powerful than I thought

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