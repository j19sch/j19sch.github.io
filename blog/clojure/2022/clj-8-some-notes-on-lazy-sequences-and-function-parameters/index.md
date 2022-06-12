<!--
.. title: (clj 8) Some notes on lazy sequences and function parameters
.. slug: clj-8-some-notes-on-lazy-sequences-and-function-parameters
.. date: 2022-04-18 14:16:36 UTC+02:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description: 
.. type: text
-->

Almost done with the chapter 4 *"Core Functions in Depth"* of "[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)"! Before wrapping up the chapter with a longer example, a summary, and some exercises, the book goes into lazy sequences, the collection abstraction, and function functions. In this post I will share some notes on infinite lazy sequences and function parameters, making comparisons between Clojure and Python.


# Infinite lazy sequences
A lazy sequence is a sequence whose members aren't computed until you try to access them. One advantage is that it's more efficient: the whole sequence doesn't have to be calculated and kept in memory from the start. Another advantage is that it allows you to create infinite sequences. Do that with a normal sequence and your program would never want to stop calculating.

<!-- TEASER_END -->

The book has the following example of an infinite sequence to calculate all even numbers:

```clojure
(defn even-numbers
  ([] (even-numbers 0))
  ([n] (cons n (lazy-seq (even-numbers (+ n 2))))))


(take 10 (even-numbers))
; => (0 2 4 6 8 10 12 14 16 18)
```

I wondered how to do the same in Python and with [some help from stackoverflow](https://stackoverflow.com/questions/51858765/generating-an-infinite-list/51859030#51859030), I got:


```python
def even_numbers(numb=None):
  numb = 0 if numb is None else numb

  while True:
    yield numb
    numb = numb + 2

top10 = itertools.islice(even_numbers(), 10)
list(top10)
# => [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

What I find interesting is how they accomplish the same thing but in a different way.

Clojure's [`lazy-seq`](https://clojuredocs.org/clojure.core/lazy-seq) is a function that: *"Takes a body of expressions that returns an ISeq or nil, and yields a Seqable object that will invoke the body only the first time seq is called, and will cache the result and return it on all subsequent seq calls."*

Python's [`yield`](https://docs.python.org/3/reference/expressions.html#yieldexpr) is used inside a function instead of the `return`, which makes that function a [generator function](https://docs.python.org/3/glossary.html#term-generator), which means the function returns a [generator iterator](https://docs.python.org/3/glossary.html#term-generator-iterator):  
*"Each yield temporarily suspends processing, remembering the location execution state (including local variables and pending try-statements). When the generator iterator resumes, it picks up where it left off (in contrast to functions which start fresh on every invocation)."*

So in essence, they do the same thing. Calculate the next step and cache. Rinse and repeat on demand. The syntax you need is a little different, though.

Clojure uses a recursive function. I tried a similar implementation in Python, but that didn't work. If I use `yield`, it only returns the result of the first step, not of multiple. If I use a `return` instead, I get a `RecursionError`. That makes sense, since I needed the `yield` to not have an infinitely recursive function.

The working solution in Python is to create an infinite loop with a `yield`, so that it's an infinite loop you actually have some control over. I thought about trying to implement something similar in Clojure, but decided that wouldn't work. Clojure does not have a `yield`, it does not even have a `return`. Clojure returns the last form in the function it evaluates[^1].


## Function parameters

"[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)" has the following example for the [`apply`](https://clojure.org/guides/learn/functions#_apply) function:

```clojure
(max 0 1 2)
; => 2

(max [0 1 2])
; => [0 1 2]

(apply max [0 1 2])
; => 2)

```

As usual, I wondered how Python approached this and turns out it doesn't care for [`max()`](https://docs.python.org/3/library/functions.html#max):

```python
>>> max(0,1,2)
2

>>> max([0,1,2])
2
```

Python does care for [`sum()`](https://docs.python.org/3/library/functions.html#sum), although I don't see why the decision was made to have it behave differently from `max()`:
```python
>>> sum(0,1,2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: sum() takes at most 2 arguments (3 given)

>>> sum([0,1,2])
3
```


## Rest parameters

The examples in the book used an `&` in the function parameters. I had forgotten what that did, but quickly relearned that the parameter after the `&` is a rest parameter. Let's say you call a function with 4 arguments. The function has one parameter and a rest parameter. The first argument will be mapped to the one parameter, all the other arguments will be put in the rest parameter:

```clojure
(defn favorite-things
  [name & things]
  (str "Hi, " name ", here are my favorite things: "
       (clojure.string/join ", " things)))


(favorite-things "Doreen" "gum" "shoes" "kara-te")
; => "Hi, Doreen, here are my favorite things: gum, shoes, kara-te"
```

My first thought was that Python does not have such a thing as rest parameters, but then I remembered `*args`. And looking it up, I found out [you don't even need to name the rest parameter `args`](https://docs.python.org/3/glossary.html#term-parameter)!

```python
>>> def favorite_things(name, *things):
...     return f"Hi, {name}, here are my favorite things: {', '.join(things)}"
... 
>>> favorite_things("Doreen", "gum", "shoes", "kara-te")
'Hi, Doreen, here are my favorite things: gum, shoes, kara-te'
```

My instincts tell me that Clojure has more use of such a rest parameter than Python, but I could be completely wrong. Time will tell as I learn more.



[^1]: Which is an interesting choice. In languages such as Python that do have a `return`, there is the question if it's ok to use a `return` somewhere else than in the last line of the function. The argument against it is that you don't want to make people look for all the `return`s in a function. It should be easy to find them and be sure you have found them all. Looks like Clojure solved the problem by avoiding the problem altogether: you don't get to decide where to `return` (or `yield`) what.
