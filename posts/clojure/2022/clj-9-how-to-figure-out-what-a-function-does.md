<!--
.. title: (clj 9) How to figure out what a function does
.. slug: clj-9-how-to-figure-out-what-a-function-does
.. date: 2022-06-12 15:01:36 UTC+02:00
.. tags: clojure, programming, brave clojure, python
.. category: clojure
.. link: 
.. description: 
.. type: text
-->

Chapter 4 of "[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)" concludes with a *Vampire Data Analysis Program*, serving as a summary of the chapter. The book shows some code, explains it, moves on to the next bit of code, etc. I'm not sure why, but I decided I wanted to figure out the code on my own and then read the explanation to see if I got it right. Afterwards I realized it might make a good blog post: both explaining what the program does and what techniques (for lack of a better word) I used to figure it out.

With most of the work in the program being done by a function called `mapify`, this blog post will focus on that single function. As it turns out, it took me more than 2000 words (footnotes not included) to describe what this function consisting of only 9 lines does. So feel free to read all of it, skim through it, or skip straight ahead to the [techniques](#techniques) and some [reflections](#reflections).

<!-- TEASER_END -->

# The function
This is `mapify`, the main function of the *Vampire Data Analysis Program* program:

```clojure
(defn mapify
  "Return a seq of maps like {:name \"Edward Cullen\" :glitter-index 10}"
  [rows]
  (map (fn [unmapped-row]
         (reduce (fn [row-map [vamp-key value]]
                   (assoc row-map vamp-key (convert vamp-key value)))
                 {}
                 (map vector vamp-keys unmapped-row)))
       rows))
```


# Breaking up the function in its parts
To figure out what this `mapify` function does, we need to break it up into parts. For that we need to know how you write a function in Clojure, i.e. the syntax of a function in Clojure. So let's go through the function step-by-step and identify its parts.


## Clojure function syntax
The function definition starts and ends with a parenthesis, making it a list. Clojure is part of the [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language))-family of languages and that means almost everything is a list and thus you get lots of parentheses. Next we have `defn` which tells Clojure we want to define a function. Then there's `mapify`, the name of the function. The part between double quotes is a docstring, describing what the function does. The line after that, `[rows]`, is the input parameter of the function. So if we want to call the `mapify` function, we need to provide it with an argument for this `rows` parameter[^8]. And everything after that is the function body, the part that defines what the functional actually does.


## <a id="breaking-up-the-function-body">Breaking up the function body
To figure out how to break up the function body, we need to do two things. We need to match opening parentheses with closing parentheses, so we know the overall structure. We need to look up the syntax of the functions being used in the different part, so we can make sense of the different parts - similar to what we did with `mapify` and the function syntax.

The function body starts with a `map`. On [`map`'s ClojureDocs page](https://clojuredocs.org/clojure.core/map) we can see that `map` takes two 'groups' of parameters: a function and one or more [collections](https://clojure.org/guides/learn/sequential_colls). Collections are things like lists and maps, so things that collect multiple values. To apply this to our code snippet, we need to take a good look at which opening parenthesis match with which closing ones. The opening parenthesis after `map` has its matching closing parenthesis at the end of the second-to-last line of the snippet. So `(fn ... unmapped-row)))` is the first argument of `map`. The `rows` on the last line is the second argument, followed by two closing parentheses: one for the function body and one for the whole function definition.

In summary, our `mapify` function is a function that performs `map` on `rows` using a function that spans most of the lines in the code snippet. So now we have to figure out what happens inside this function:

```clojure
(fn [unmapped-row]
         (reduce (fn [row-map [vamp-key value]]
                   (assoc row-map vamp-key (convert vamp-key value)))
                 {}
                 (map vector vamp-keys unmapped-row)))
```

You might have noticed that this function looks a bit different than the `mapify` function. That's because this is a an anonymous function, while `mapify` is a named function. An anonymous function does not have a name[^1], so it's used in-place instead of being called from somewhere else in the code. Most of the syntax is the same though. `[unmapped-row]` is the function parameter and all that follows is the function body.

The function body start with a `reduce`. We can also see it takes three parameters (because matching brackets): an anonymous function (first two lines), an empty map (the `{}`), and whatever is returned by the last line (`map vector ...`). `reduce`'s [ClojureDocs page](https://clojuredocs.org/clojure.core/reduce) tells us that `reduce` either takes the form of `(reduce f coll)` or `(reduce f val coll)`, so that last line must be returning a collection. And [`map`'s ClojureDocs](https://clojuredocs.org/clojure.core/map) confirms this: `map` returns a lazy sequence, which is a collection[^2].

So what have we figured out so far? We have the `mapify` function, which does a `map`, which does a `reduce`. And this `reduce` does something with a function and two pieces of data. Let's figure out what exactly that is.



# Understanding what the `reduce` does
The [`reduce` ClojureDocs](https://clojuredocs.org/clojure.core/reduce) almost are a piece of code by itself:

*`(reduce f coll) (reduce f val coll)`*  
*f should be a function of 2 arguments. If val is not supplied, returns the result of applying f to the first 2 items in coll, then applying f to that result and the 3rd item, etc. If coll contains no items, f must accept no arguments as well, and reduce returns the result of calling f with no arguments.  If coll has only 1 item, it is returned and f is not called. If val is supplied, returns the result of applying f to val and the first item in coll, then applying f to that result and the 2nd item, etc. If coll contains no items, returns val and f is not called.*

We can ignore most of it, though. We do supply a `val` and our `coll` should not be empty. That leaves us with a single relevant sentence: *"If val is supplied, returns the result of applying f to val and the first item in coll, then applying f to that result and the 2nd item, etc."* Moreover, the `val` is an empty map and the [book's explanation of `reduce`](https://www.braveclojure.com/core-functions-in-depth/#reduce) is two examples with an empty map as `val`. Both examples are about taking an existing map and creating either a map with updated values, or filtering an existing map. So this `reduce` must be doing something similar.

That leaves us with two questions:

- What does the function of the `reduce` do?
- What data does the `reduce` operate on?

Let's start with the second one, figuring out what data the `reduce` is operating on and then see how the function transforms that data.


## What data does the `reduce` operate on?
The data provided to the `reduce` (the `coll` in the paragraph above), is whatever is returned by:
```clojure
(map vector vamp-keys unmapped-row)
```
 Ideally we'd break this up in parts as we have been doing. That's now what I did however. I first looked into the last two things, `vamp-keys` and `unmapped-row`, and then moved to the `map` and `vector`.


### The `vamp-keys` and the `unmapped-row`
`vamp-keys` was defined earlier in the example code as:
```clojure
(def vamp-keys [:name :glitter-index])
```

For `unmapped-row` we need to track back a bit to the `map` in the `mapify` function:
```clojure
(map (fn [unmapped-row]
       (reduce (fn ...)
               {}
               (map vector vamp-keys unmapped-row)))
     rows)
```
As mentioned above, this `map` has two parameters: an anonymous function and a collection called `rows`. What `map` will do in case of a [single collection argument](https://clojuredocs.org/clojure.core/map), is apply the function to the first item in the collection, then to second, etc. So the anonymous function will get one row from `rows` at a time from `map`, i.e. the `unmapped-row` parameter on the first line in the snippet above.

That still leaves the question what these `rows` are. The answer to that is vampire names and their glitter index:

```
Edward Cullen,10
Bella Swan,0
Charlie Swan,0
Jacob Black,3
Carlisle Cullen,6
```

Or rather, that's what's in the `.csv` file, which after parsing[^3] is provided to the `mapify` function like this:
```clojure
(["Edward Cullen" "10"] ["Bella Swan" "0"] ["Charlie Swan" "0"]
  ["Jacob Black" "3"] ["Carlisle Cullen" "6"])
```

### The `vector` and the `map`
`vector` takes whatever you give it and puts it in a vector (a vector is basically a list or array):

```clojure
(def unmapped-row ["Edward Cullen" "10"])
(vector vamp-keys unmapped-row)
; => [[:name :glitter-index] ["Edward Cullen" "10"]]
```

However that's not what `(map vector vamp-keys unmapped-row)` does. Hence my comment earlier that I should have broken down this function based on its syntax and not simply started at the end and work my way to the front. What's not happening here is that `map` is applied to what's returned by `vector`. Then the code should have been `(map (vector vamp-keys unmapped-row))`. What's happening instead is that `vector`, `vamp-keys`, and `unmapped-row` are arguments for the `map` function.

Earlier we had a `map` with a function and one collection as parameters. Now we have a function (`vector`) and two collections (`vamp-keys`, and `unmapped-row`). How `map` [works in this case](https://clojuredocs.org/clojure.core/map) is that it will take the first item in `vamp-keys` and the first item in `unmapped-row` and apply `vector` to it. Then it'll do the same for the second items, etc. until one of the two collections is exhausted:
```clojure
(map vector vamp-keys unmapped-row)
; => ([:name "Edward Cullen"] [:glitter-index "10"])
```

### Recap
The `mapify` function is using a `reduce` to create a new map based on some data it's getting and a function. We now know what that data looks like. It's a set of rows with a single row looking like this: `([:name "Edward Cullen"] [:glitter-index "10"])`. Next step is figuring out what the function provided to the `reduce` does with these rows.



## What does the function of the `reduce` do?
The function of our `reduce` is:
```clojure
(fn [row-map [vamp-key value]]
                   (assoc row-map vamp-key (convert vamp-key value)))
```

To understand what this function does, it's helpful to know what arguments will be provided to it, i.e. what will be used for `[row-map [vamp-key value]]`. With this function being used in the `reduce` that means its arguments are provided by that `reduce`. So we're a bit stuck in a loop: to understand this function we need to understand the `reduce` and to understand the `reduce` we need to understand this function.

To escape that loop, we're not going into how `reduce` works just yet. Instead, I'm going to say (simplified so not entirely correct) that `row-map` is the second argument provided to the `reduce`, i.e. the empty map `{}`. And that `[vamp-key value]` is the first item in our collection (see above), i.e. `[:name "Edward Cullen"]`.

That leaves us with two words to explain in this anonymous function: `assoc` and `convert`.

The `convert` function was defined earlier in the code example[^4]. What it does, is that if `vamp-key` is `:glitter-index`, it converts the `value` from a string to an integer, e.g. from `"10"` to `10`.

[`assoc`](https://clojuredocs.org/clojure.core/assoc) is a way to add or update an existing map[^5]. For example:

```clojure
(assoc {} :name "Edward Cullen")
; => {:name "Edward Cullen"}
(assoc {:name "Edward Cullen"} :glitter-index 10 )
; => {:name "Edward Cullen" :glitter-index 10}
```

Now we have all the elements to figure out what this function used by the `reduce` does. It takes an existing map (`row-map`) and a key-value pair (e.g. `:name "Edward Cullen"`). It converts the value of the key-value pair to an integer if the key equals `:glitter-index`. Then it creates a new map that contains both the existing map and the post-conversion key-value pair.


## Putting the pieces of the `reduce` back together
Now that we understand the parts of the `reduce`, we should be able to put them together again to understand the whole:

```clojure
(fn [unmapped-row]
         (reduce (fn [row-map [vamp-key value]]
                   (assoc row-map vamp-key (convert vamp-key value)))
                 {}
                 (map vector vamp-keys unmapped-row)))
```

To summarize, those parts are:

- `reduce` takes an `f`, a `val`, and a `coll`. It returns the result of applying `f` to `val` and the first item in `coll`, then applying `f` to that result and the 2nd item, etc.
- the `f` converts the `:glitter-index` value from a string to an integer
- the `val` is an empty map, `{}`, at least initially
- the `coll` is a parsed row from the `.csv` file, e.g. `([:name "Edward Cullen"] [:glitter-index "10"])`

This means `reduce` will execute the function twice. The first time it adds the `name` key-value pair to the empty map[^6]. The second time it adds the `glitter-index` key-value pair (including converting the value to an integer) to that same map. So we end up with both the `name` and `glitter-index` key-value pairs in the map.

We can check our understanding, by isolating the `reduce` function and providing it with an `unmapped-row`:

```clojure
(def unmapped-row ["Edward Cullen" "10"])
(reduce (fn [row-map [vamp-key value]]
         (assoc row-map vamp-key (convert vamp-key value)))
       {}
       (map vector vamp-keys unmapped-row))
; => {:name "Edward Cullen", :glitter-index 10}
```



# <a id="the-mapify-function">The `mapify` function, `map`ping the `reduce`
Now that we understand the `reduce`, we can actually guess what the `map` that uses this `reduce`, does. The `reduce` works on a single row, but our data consists of several rows. So the `map` must be the thing that loops through the rows, providing them one-by-one to the `reduce`.

Of course, we want to do better than guessing. So let's revisit [`map`](https://clojuredocs.org/clojure.core/map). It takes a function and at least one collection. It will apply the function to the set of first items in the collections, then to the second, etc. The function is the `reduce` we just figured out. And as we saw when [breaking up the function body](#breaking-up-the-function-body), the `map` in the `mapify` has only one collection-parameter, called `rows`. So that confirms our guess: `map` loops through the `rows`[^7] and transforms them via the `reduce`.

In conclusion, all this figuring out let's us look at this:

```clojure
(defn mapify
  "Return a seq of maps like {:name \"Edward Cullen\" :glitter-index 10}"
  [rows]
  (map (fn [unmapped-row]
         (reduce (fn [row-map [vamp-key value]]
                   (assoc row-map vamp-key (convert vamp-key value)))
                 {}
                 (map vector vamp-keys unmapped-row)))
       rows))

```
and think of it like this:

```clojure
(defn mapify
  "Return a seq of maps like {:name \"Edward Cullen\" :glitter-index 10}"
  [rows]
  (map (do-stuff)
       rows))

```

Where we know that `do-stuff` changes the rows into maps with keys `:name` and `:glitter-index` and that it converts the value of the `:glitter-index` from a string to an integer. Looking at the function fully written out, we'll probably remember that the `(map vector vamp-keys unmapped-row)` does the former and that the function of the `reduce` does the latter. And if we want to know how exactly it does these things, we'll have to re-figure it out. Or scroll back up a bit and read it there.

Having done all this work (and writing) I can't help but feel a bit disappointed. In the end, the function does not seem to do a lot. To illustrate, in Python you'd write this to do basically[^9] the same thing:

```python
def mapify(rows):
  return [
    {
      vamp_keys[0]: row[0],
      vamp_keys[1]: int(row[1])
    }
    for row in rows
  ]

rows = [["Edward Cullen", "10"], ["Bella Swan", "0"], ["Charlie Swan", "0"],
  ["Jacob Black", "3"], ["Carlisle Cullen", "6"]]

vamp_keys = ["name", "glitter-index"]

mapify(rows)
# => [{'name': 'Edward Cullen', 'glitter-index': 10}, {'name': 'Bella Swan', 'glitter-index': 0},
# {'name': 'Charlie Swan', 'glitter-index': 0}, {'name': 'Jacob Black', 'glitter-index': 3},
# {'name': 'Carlisle Cullen', 'glitter-index': 6}]
```
**edit 13 July 2022**  
The Clojure and Python versions are not as equivalent as I thought, see my follow-up post [(clj 10) The mapify function of (clj 9) revisited](link://slug/clj-10-the-mapify-function-of-clj-9-revisited).


# <a id="techniques"></a>Techniques I used in figuring all of this out
1. break things down in parts, understand the parts, put it all back together again
1. focus on the current level and ignore the specifics of the levels above and below
1. read ClojureDocs
1. decide what the argument provided to a function is, because I know what the function expects as parameter
1. make an educated guess to fill in a gap (this `map` must be how the code loops trough the rows)
1. understand the code in context, i.e. with the data provided in the example, instead of in a more general way
1. not worry too much about abstract data structures (collections and sequences)
1. figure out the first iteration of a loop (for the `reduce`) before looking into the looping
1. simplify what a function does based on the number of parameters, e.g. think of `map` with one `col` as a loop
1. recognize patterns, e.g. a `reduce` with an empty map as `val` is a way to transform an existing map
1. take part of the function and run it to see what it does
1. rewrite the code in a different language
1. write this blog post (arguable also a rewrite in a different language)

# <a id="reflections"></a>Reflections
Writing this blog post was harder and took a lot more time (and words) than I thought. Luckily, I also learned a lot.

The Clojure code is very nested with functions inside of functions inside of functions. It looks and feels different from the Python code I'm used to. The explanation must be the difference in programming paradigms: [functional](https://en.wikipedia.org/wiki/Functional_programming) ([Clojure](https://en.wikipedia.org/wiki/Clojure)) versus [procedural](https://en.wikipedia.org/wiki/Procedural_programming) ([Python](https://en.wikipedia.org/wiki/Python_(programming_language))). In procedural programming you define a sequence of steps, in functional programming you have functions nested in other functions. (Note: Python supports more paradigms than procedural, but I've mostly used in a procedural paradigm.)

Another related difference between the two versions is that to me the Clojure version looks more complicated than the Python version[^10]. Part of the explanation is the difference in paradigm I mentioned above. Another part is a difference in how the syntactical work happens. Not just for example parentheses (Clojure) and whitespace (Python), but also [`filter`](https://clojuredocs.org/clojure.core/filter) and [`map`](https://clojuredocs.org/clojure.core/map) (Clojure) and [list comprehension](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions) (Python). A great illustration of this is [Guido van Rossum arguing](https://www.artima.com/weblogs/viewpost.jsp?thread=98196) to remove `reduce()`, `filter()`, and `map()` from Python's standard library.  
A third part of the explanation - and I think the most interesting part, is that I read them in a different way. For example, when I came across `(map vector vamp-keys unmapped-row)` in Clojure, I had to figure it out step-by-step. In Python on the other hand, I can read and understand e.g. a list comprehension (the `[ { ... } for row in rows]`) without much effort. I immediately see the whole, I recognize the pattern of a list comprehension. So the main difference might be that I need more practice reading Clojure, until there too I can see the patterns.



[^8]: It probably does not aid in readability, but I've decided to maintain the distinction between parameters and arguments. A parameter is a variable that's part of the function definition. An argument is a variable or expression that's used when calling a function. Bonus points to you if you find a place where I missed this up in this blog post.

[^1]: Although it turns out you can [name an anonymous function](https://clojuredocs.org/clojure.core/fn#example-542692c7c026201cdc326977). This can be [useful](https://stackoverflow.com/questions/41683672/clojure-named-anonymous-function) for readability and in stack traces.

[^2]: Writing all of this out makes me appreciate how complicated and multi-layered all of this is. As *"Clojure for the Brave and True"* says in chapter 4:  
*"The collection abstraction is closely related to the sequence abstraction. All of Clojure’s core data structures - vectors, maps, lists, and sets - take part in both abstractions. The sequence abstraction is about operating on members individually, whereas the collection abstraction is about the data structure as a whole."*  
<br />
So we're dealing with an abstract data structure, the collection, which tells us something about what we can do with it as a whole. We're also dealing with a different abstract data structure, the lazy sequence, which tells us something about what we can do with its individual members, i.e. [sequencey](https://clojure.org/reference/sequences) things, while it also tells us something about how this is implemented, i.e. [lazily](https://clojuredocs.org/clojure.core/lazy-seq). So now I'm wondering if I am correct in calling a lazy sequence a collection...  
I wrote about the sequence abstraction in [(clj 7)](link://slug/clj7-programming-to-abstractions-with-sequence-functions) and about the lazy sequences in [(clj 8)](link://slug/clj-8-some-notes-on-lazy-sequences-and-function-parameters).

[^3]: If you want to know how the parsing works, you can read it in the [online version of the book](https://www.braveclojure.com/core-functions-in-depth/#A_Vampire_Data_Analysis_Program_for_the_FWPD).

[^4]: See the [online version of the book](https://www.braveclojure.com/core-functions-in-depth/#A_Vampire_Data_Analysis_Program_for_the_FWPD), if you're curious about the `convert`.

[^5]: For completeness sake: data in Clojure is immutable, so `assoc` will not change the existing map, it returns a new one.

[^6]: Data is immutable in Clojure, so to be correct I should say that Clojure creates a new map. I don't think this matters here and conceptually it's easier to think of things being added to the map.

[^7]: In this sense `map` with one `coll` parameter feels different to me than with multiple `coll` parameters. With a single one, it acts like a for-loop. Take the first thing and apply the function, take the second thing and apply the function, etc. With multiple `coll`s it takes all the first things and applies the function to them, then all the second things, etc. until one of the `coll`s is exhausted. Described like this, these are two different things. However, from a more abstract viewpoint, I also see that the single `coll` is not fundamentally different, it's a kind of special case of the multiple `coll` situation.

[^9]: The Python code does do the `convert` in a separate function. It would also return a different result than the Clojure code if the data would have more than two items per row.

[^10]: It makes me wonder if the example is fully idiomatic Clojure. It probably is, though, because it's from a book teaching Clojure.