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

Looking at my progress so far, I realized it's time re-evaluate this whole learning Clojure-thing. After looking through the table of contents of "[Clojure for the Brave and True](https://www.braveclojure.com/)" and giving it some thought, I decided to make two changes to how I'll proceed:

- I will start writing shorter posts and write them more often.
- My goal is to finish *"Part II: Language Fundamentals"*. I don't have to do *"Part III: Advanced Topics"*.

Completing Part II will still take quite some work. I've worked through the two first sections of chapter 4 (5 sections left in that chapter) and Part II goes up to chapter 8. So no time to waste: let's take a look at sequence functions and programming to abstractions.

<!-- TEASER_END -->


## Programming to abstractions

Sequence functions are functions such as `map`, `filter`, and `reduce` that work on anything that Clojure considers to be a sequence. In practice those sequences will be lists, vectors, sets, or maps. They could be other data structures, though, since the only thing Clojure cares about is that the data structure responds to the functions `first`, `rest`, and `cons`. `first` returns the first item of a sequence. `rest` returns everything after the first item. `cons` adds a new item to the beginning of the sequence (or rather: it returns a new sequence).[^1]

This way of doing things is called programming to abstractions. And apparently it’s a central tenet of Clojure philosophy. Luckily I was familiar with this concept (not with the name though) from Python and its [magic methods](https://rszalski.github.io/magicmethods/)[^2].

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
After explaining the idea of programming to abstractions, the Brave and True-book goes through a list of functions that rely on Clojure’s sequence abstraction: `map`, `reduce`, `take`, `drop`, `take-while`, `drop-while`, `filter`, `some`, `sort`, `sort-by`, and `concat`. I'm not going to cover all of these; I will just share some notes I made on `map` and `drop-while`/`take-while`.


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

`"123"` is the result of applying `str` to `1 2 3` and `6` is the result of applying `+` to `1 2 3`. Although this result is the other way around - as if we `map`ped two functions to a sequence of data -, syntactically that's not the case. `#(% 1 2 3)` is a function (an anonymous one) and `[str +]` is a sequence. To illustrate, here's the first example but rewritten with this syntax:
```clojure
(map #(str %) [1 2 3])
; => ("1" "2" "3")
```

I think that's a really cool feature of Clojure.


### `drop-while` before `take-while` or the other way around?

After explaining `take-while` (take items from a sequence while a condition is true) and `drop-while` (drop items from a sequence while a condition is true), the book shares an example of how to use the two together. After making it work on a vector of numbers instead of on a hash map, it looks like this:
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

As you can see, the result is the same. I wonder if performance could be a consideration, that you first want to do the operation that reduces the length of the sequence the most. Might be that the next section about lazy sequences sheds some light on that.

Another way to look at this, is from a readability perspective. Conceptually it makes sense to `drop-while` first to get to the first number you want to keep, then use `take-while` to stop at the last number of the sequence you need. So reading from left-to-right the second example makes more sense, because you read the `drop-while` before the `take-while`. However, reading in order of execution the first example makes more sense for exactly the same reason: `drop-while` before the `take-while`[^4]. It was interesting to notice myself making that transition from reading left-to-right to reading in order of execution, and then deciding the example in the book made more sense than the alternative I had come up with.

Finally, these examples with `drop-while` and `take-while` made me wonder what data being immutable means for operations like this. That's something the book will cover in [chapter 5](https://www.braveclojure.com/functional-programming/).



## Implementing `map`, `filter` and `some` using `reduce`
After explaining `reduce` the book says:

> The takeaway here is that `reduce` is a more flexible function than it first appears. Whenever you want to derive a new value from a seqable data structure, `reduce` will usually be able to do what you need. If you want an exercise that will really blow your hair back, try implementing `map` using `reduce`, and then do the same for `filter` and `some` after you read about them later in this chapter.

So I gave that a try.

### `map` using `reduce`
For `map` I wrote the following function, deciding being able to deal with a single collection was sufficient:

```clojure
(defn my-map [func inp]
  (reduce (fn [vect number]
            (concat vect [(func number)]))
            ()
            inp)
  )

(my-map inc [1 2 3])
; => (2 3 4)
(my-map dec [4 5 6])
; => (3 4 5)
```

### `filter` using `reduce`
Implementing `filter` was quite a struggle. As a starting point I took an example from the book: it turned out that the explanation about `reduce` already contained `filter` implemented with `reduce`. Simplified to work on a vector of numbers instead of on a hash map, it looks like this:
```clojure
(defn my-simple-filter [inp]
  (reduce (fn [vect numb]
            (if (< numb 4)
              (concat vect [numb])
              vect))
          ()
          inp)
  )

(my-simple-filter [1 2 3 4 5])
=> (1 2 3)

```
What I wanted to do, was to have the `(< numb 4)` as one of the arguments to a `filter-as-reduce` function. I tried to do that in numerous different ways, but none of them worked. The function would run, but the output was `(1 2 3 4 5)` instead of `(1 2 3)`. My best guess as to why is that my input argument was not executed as a function, but evaluated as truthy.

What I did get to work, was to have the whole function for the `reduce` as an argument to the `filter-as-reduce` function. So that's close, but not exactly what I set out to do. And I'm sure it can be done, just not by me right at this moment.

### `some` using `reduce`
Finally, for `some` I decided not to bother, because I started to feel this exercise does not mesh well with the way I'm working through this book. So I figured that `some` would be very similar to `filter`, with the exception that it should not return a collection of values matching the filter, but instead return `true` on the first match (if any) and else return `false`.



## Some vim stuff related to macros
I added the macro I mentioned in [my previous post](link://slug/clj6-three-chapters-in-one-year), to my `.vimrc` file: `let @c='yypc!$gcca =>`. The biggest challenge was to figure out how to put an `escape` in the macro to switch from command mode to insert mode, so that I could type the "=>". The solution turned out to be `ctrl+v Esc`, where `ctrl+v` is "insert next non-digit literally".

Another thing I figured out about the macro is that there's an issue with indentation. You should run it on the last line of a function to get the result on the line right below the function. However, if that line has indentation, the result has that same indentation. Something to fix some other time...



[^1]: The book explains this further through linked lists, which I am going to use as an excuse to point you to this excellent article by 
[Hillel Wayne](https://twitter.com/hillelogram): [Why do interviewers ask linked list questions?](https://www.hillelwayne.com/post/linked-lists/)

[^2]: They're also called dunder methods, short for "double underscore methods", because their names start and end with a double underscore.

[^3]: The sensible recommendation here would be to have `+` then do something that is some sort of addition, but I must admit I'm tempted to recommend doing the opposite.

[^4]: Going through my cryptic notes on this from several months ago, it looks like I came to the same conclusion about this as my past self.
