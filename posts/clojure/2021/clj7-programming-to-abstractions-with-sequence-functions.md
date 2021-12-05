<!--
.. title: (clj 7) Programming to abstractions with sequence functions
.. slug: clj7-programming-to-abstractions-with-sequence-functions
.. date: 2021-12-05 13:40:36 UTC+01:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description:
.. type: text
-->

Looking at my progress so far, I realized it's time re-evaluate this whole thing of learning Clojure thing. After looking through the table of contents of "[Clojure for the Brave and True]((https://www.braveclojure.com/))" and giving it some thought, I decided to make two changes:

- I will start writing shorter posts and write them more often.
- My goal is to finish "Part II: Language Fundamentals". I don't have to do "Part III: Advanced Topics".

Completing Part II will still take quite some work. I've worked through the two first sections of chapter 4 (so 5 sections left in that chapter) and Part II goes up to chapter 8. So no time to waste: let's take a look at sequence functions and how they use the idea of programming to abstractions.

<!-- TEASER_END -->


## Programming to abstractions

Sequence functions are functions such as `map`, `filter`, and `reduce` that work on anything that Clojure considers to be a sequence. In practice those sequences will be lists, vectors, sets, and maps. They could be other data structures, though, since the only thing Clojure cares about is that the data structure responds to the functions `first`, `rest`, and `cons`. `first` return the first item of a sequence. `rest` returns everything after the first item. `cons` adds a new item to the beginning of the sequence (or rather: it returns a new sequence).[^1]

This way of doing things is called programming to abstractions. And apparantly it’s a central tenet of Clojure philosophy. Luckily I was familiar with this concept (although not with the name) from Python and its [magic methods](https://rszalski.github.io/magicmethods/)[^2].

In Python you can use the `+` operator on several data structures, but not on all of them:
```python
>>> "a" + "b"
'ab'

>>> 1 + 2
3

>>> [1] + [2]
[1, 2]

>>> (1,) + (2,)
(1, 2)

>>> {"a": 1} + {"b": 2}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'dict' and 'dict'

>>> {1} + {2}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'set' and 'set'

```

If `+` works or not, depends on the data structure having implemented the magic method `__add__(self, other)`. And yes, that means you can create your own custom class, implement `__add__` for it and then `+` two instances of it[^3]. 



## Sequence functions
After explaining the idea of programming to abstractions, the Brave and True-book goes through a list of functions that rely on Clojure’s sequence abstraction: `map`, `reduce`, `take`, `drop`, `take-while`, `drop-while`, `filter`, `some`, `sort`, `sort-by`, and `concat`. I'm not going to cover all of these; I will just share notes I made on a few of these.


### `map` works either way
The most obvious usage of the `map` function is to apply a function to a sequence of items:

```clojure
(map str [1 2 3])
; => ("1" "2" "3")
```

Applying it to multiple sequences works as well:
```clojure
(map str [1 2 3] [6 7 8])
; => ("16" "27" "38")

(map str [1 2 3 4] [6 7 8])
; => ("16" "27" "38")

(map str [1 2 3] [6 7 8 9])
; => ("16" "27" "38")
```

However, instead of applying a function to one or more sequences, you can also do it the other way around:
```clojure
(map #(% 1 2 3) [str +])
; => ("123" 6)
```

`"123"` is the result of applying `str` to `1 2 3` and `6` is the result of applying `+` to `1 2 3`. Syntactically it's not the other way around, however: `#(% 1 2 3)` is a function (an anonymous one) and `[str +]` is a sequence. To illustrate, here's the first example but rewritten with this syntax:
```clojure
(map #(str %) [1 2 3])
; => ("1" "2" "3")
```

I think that's a really cool feature of Clojure.


### take-while/drop-while

After explaining `take-while` (take items from a sequence while a condition is true) and `drop-while` (drop items from a sequence while a condition is true), the book shares an example of how to use the two together. A simplified version of that example looks like this:
```clojure
(take-while #(< % 6)
  (drop-while #(< % 2) [1 2 3 4 5 6 7]))
; => (2 3 4 5)
```

Which made me wonder, why not do it the other way around:
```clojure
(drop-while #(< % 2)
  (take-while #(< % 6) [1 2 3 4 5 6 7]))
; => (2 3 4 5)
```

As you can see, for the results it does not matter.

From a readability perspective, I think something interesting is happening. Conceptually it makes sense to `drop-while` first to get to the first number you want to keep, then use `take-while` to stop at the last number of the sequence you want to keep. So reading from left-to-right the second example makes more sense, because you read the `drop-while` comes before the `take-while`. However, reading in order of execution the first example makes more sense for exactly the same reason[^4]. So that illustrates a nice step in learning how to read Clojure: moving from reading direction to order of execution.

As a closing thought, I wonder if performance can be a reason to decide whether to do the `take-while` first or the `drop-while`. Might be that the next section about lazy sequences sheds some light on that.

Finally, these examples also made me wonder what data being immutable means for operations like this. That's something the book will cover in [chapter 5](https://www.braveclojure.com/functional-programming/).


### some
some: return the value by using the behavior of and of returning the last evaluated value (see clj ???)


## Implementing `map`, `filter` and `some` using `reduce`



## Some vim stuff
I added the macro I mentioned in [my previous post](link://slug/clj6-three-chapters-in-one-year), to my `.vimrc` file: `let @c='yypc!$gcca =>`. The biggest challenge was to figure out how to put an `escape` in the macro to switch from command mode to insert mode, so that I could type the "=>". The solution turned out to be `ctrl+v Esc`, where `ctrl+v` is "insert next non-digit literally".

Another thing I figured out about the macro is that it keeps the indentation if you run it on an indented line. Something to fix some other time...



[^1]: The book explains this further through linked lists, which I am going to use as an excuse to point you to this excellent article by 
[Hillel Wayne](https://twitter.com/hillelogram): [Why do interviewers ask linked list questions?](https://www.hillelwayne.com/post/linked-lists/)

[^2]: Magic methods are also called dunder methods, which is short for "double underscore methods".

[^3]: Am tempted to recommend both to have `+` do something that can be interpreted as some kind of addition and to instead make it do something completely bizarre that does not relate to addition at all.

[^4]: Going through my cryptic notes on this from several months ago, it looks like I came to the same conclusion about this as my past self.
