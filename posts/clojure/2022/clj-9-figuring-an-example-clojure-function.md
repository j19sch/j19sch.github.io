<!--
.. title: (clj 9) Figuring out an example Clojure function
.. slug: clj-9-figuring-an-example-clojure-function
.. date: 2022-06-05 13:16:36 UTC+02:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description: 
.. type: text
-->

Chapter 4 of "[Clojure for the Brave and True](https://www.braveclojure.com/clojure-for-the-brave-and-true/)" concluded with a Vampire Data Analysis Program, serving as a summary of the chapter. The book shows some code, explains it, moved on to the next bit of code, etc. I'm not sure why, but I decided I wanted to figure out the code on my own and then read the explanation to see if I got it right. An extra challenge here is that it's taken my more than two years to get to this far in the book and I started chapter 4 six months ago - as you can see on my [Learning Clojure](link://slug/learning-clojure) page.

The largest function of the pogram is the `mapify` function:

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
Since it took me some effort to figure out, I thought it might make a good blog if I explained how I went about it. That did take me a fair number of words, so for the tl;dr you can skip ahead to the [conclusion](#conclusion) and/or the [reflection](#reflection).

<!-- TEASER_END -->

# Breaking the function up in its parts
To figure out what this `mapify` function does, we need to know where it is in a Clojure function that things are being done, i.e. know the syntax of function definitions. So let's go through the code above step by step.

## Function definitions on Clojure
The function definition starts and ends with a parenthesis, because that makes it a list and Clojure is part of the [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language))-family of languages, so then you have to have lots of lists and thus parenthesis. Next we have `defn` which tells Clojure we want to define a function. Then there's `mapify`, where we name the funtion. The part between double quotes is a docstring, describing what the function does. The line after that, `[rows]`, is the input parameter of the function. So if we want to call the `mapify` function, we need to provide with an argument for this `rows` argument. And all the rest after that is the function body, the part that defines what the functional actually does.

## Breaking up the function body
To figure out how to break up the function body, we need two things. We need to match opening brackets with closing brackets and we need to look up the documentation of the functions being used inside the function body.

The function body starts with a `map`. On [its ClojureDocs page](https://clojuredocs.org/clojure.core/map) we can see that `map` takes two 'groups' of arguments. The first argument needs to be a function. The second and any additional arguments need to be [collections](https://clojure.org/guides/learn/sequential_colls). Collections are things like lists and maps, so things that collect multiple values. Applying this to the code snippet, this means that our `mapify` function is basically a function that performs `map` on `rows` using a function that spans five lines in the snippet.

So now we have to figure out what this function used by the `map` is:

```clojure
(fn [unmapped-row]
         (reduce (fn [row-map [vamp-key value]]
                   (assoc row-map vamp-key (convert vamp-key value)))
                 {}
                 (map vector vamp-keys unmapped-row)))
```

You might have noticed that this function looks a bit different than the `mapify` function. That's because this is a an anonymous function, while `mapify` is a named function. An anonymous function does not have a name[^1], so it's used in-place instead of being called from somewhere else in the code. Most of the syntax is the same though. `[unmaped-row]` is the function parameter and all that follows is the function body.

This function body start with a `reduce`. We can also see it takes three parameters: an anonymous function (first two lines), an empty map (the `{}`), and whatever is returned by the last line. `reduce`'s [ClojureDocs page](https://clojuredocs.org/clojure.core/reduce) tell us is that `reduce` either takes the form of `(reduce f coll)` or `(reduce f val coll)`, so that last line must be returning a collection. And the [`map` ClojureDocs](https://clojuredocs.org/clojure.core/map) confirm this, as they say that `map` returns a lazy sequence, which is a collection[^2].

Where does all of this leave us? We have the `mapify` function, which does a `map`, which does a `reduce`. And this `reduce` does something with a function and two pieces of data. Let's figure out what exactly that is.


# Understanding what the `reduce` does
The [`reduce` ClojureDocs](https://clojuredocs.org/clojure.core/reduce) almost are a piece of code by itself:
> (reduce f coll) (reduce f val coll)  
>If should be a function of 2 arguments. If val is not supplied, returns the result of applying f to the first 2 items in coll, then applying f to that result and the 3rd item, etc. If coll contains no items, f must accept no arguments as well, and reduce returns the result of calling f with no arguments.  If coll has only 1 item, it is returned and f is not called. If val is supplied, returns the result of applying f to val and the first item in coll, then applying f to that result and the 2nd item, etc. If coll contains no items, returns val and f is not called.

We can ignore most of it, though. We do supply a `val` and our `coll` should not be empty. That leaves us with a single relevant sentence: *"If val is supplied, returns the result of applying f to val and the first item in coll, then applying f to that result and the 2nd item, etc."* Moreover, the `val` is an empty map and the [book's explanation of `reduce`](https://www.braveclojure.com/core-functions-in-depth/#reduce) is two examples with an empty map as `val`. Both examples are about taking an existing map and creating either a map with updated values, or a filtered map.

So that leaves us with two questions. How does the `f` parameters transform the data? What data is being provided to the `coll` parameter?

## What's the `coll` of the `reduce`?
The `coll` of our `reduce` is whatever is returned by:
```clojure
(map vector vamp-keys unmapped-row)
```

### `vamp-keys` and `umapped-row`
`vamp-keys` was defined earlier in the example as:
```clojure
(def vamp-keys [:name :glitter-index])
```

For `unmapped-row` we need to track back a bit to the `map` in the `mapify` function. This `map` has two parameters: an anonymous function and a collection called `rows`. What `map` will [do in this case](https://clojuredocs.org/clojure.core/map), is apply the fuction to the first item in the collection, then to second, etc. returing a lazy sequence. So the anonymous function will get one row from `rows` at a time. Combined with the name of the function, `mapify`, the name of the parameter of the anonymous function makes a lot of sense: `unmapped-row`.

That still leaves the question what's in these `rows`. The answer to that is vampire names and their glitter index:

```
Edward Cullen,10
Bella Swan,0
Charlie Swan,0
Jacob Black,3
Carlisle Cullen,6
```

Or that's what's in the `.csv` file, which after parsing[^3] is provided to the `mapify` function like this:
```clojure
(["Edward Cullen" "10"] ["Bella Swan" "0"] ["Charlie Swan" "0"] ["Jacob Black" "3"] ["Carlisle Cullen" "6"])
```

### `vector` and `map`
`vector` takes whatever you give it and puts it in a vector (basically a list or array):

```clojure
(def unmapped-row ["Edward Cullen" "10"])
(vector vamp-keys unmapped-row)
; => [[:name :glitter-index] ["Edward Cullen" "10"]]
```

However that's not what the piece of code `(map vector vamp-keys unmapped-row)` does. What's not happening here is that `map` is applied to what's returned by `vector`. Then there should have been parantheses around `vector vamp-keys unmapped-row`. What is happening is that `vector`, `vamp-keys`, and `unmapped-row` are arguments for the `map` function.

So `map` will take the first item in `vamp-keys` and the first item in `unmapped-row` and apply `vector` to it. Then it'll do the same for the second items, etc. until one of the collections with items is exhausted:
```clojure
(map vector vamp-keys unmapped-row)
; => ([:name "Edward Cullen"] [:glitter-index "10"])
```

So... why were we figuring all of this out? To recap, the `mapify` function is using a `reduce` to create a new map based on some data it's getting, the `coll` or collection, and a function. We now know what that collection of data looks like. It's a set of rows with a single row looking like `([:name "Edward Cullen"] [:glitter-index "10"])`. Next step is figuring out what the function provided to the `reduce` does with these rows.


## What's the `f` of the `reduce`?
The function of our `reduce` is:
```clojure
(fn [row-map [vamp-key value]]
                   (assoc row-map vamp-key (convert vamp-key value)))
```

To understand what this function does, it's helpful to have some idea about where its arguments, the `[row-map [vamp-key value]]` are coming from. With this function being used in the `reduce`, we need to understand waht `reduce` does to some degree. I'm not going to explain that here, but in the next section. For now, we can say (simplified so slightly wrong) that `row-map` is the second argument provided to the `reduce`, i.e. the empty map `{}`. And that `[vamp-key value]` is the first item in our collection (see above) `[:name "Edward Cullen"]`.

That leaves us with two words to explain, `assoc` and `convert`.

The `convert` function was defined earlier in the example. What it does, is that if `vamp-key` is `:glitter-index`, it convers the `value` from a string to an integer, e.g. from `"10"` to `10`.

[`assoc`](https://clojuredocs.org/clojure.core/assoc) is way to add or update an existing map. (Note: `assoc` returns a new map, so the original map is unchanged.) For example:

```clojure
(assoc {} :name "Edward Cullen")
; => {:name "Edward Cullen"}
```

Now we have all the elements to figure out what this function used by the `reduce` does. It takes an existing map (`row-map`) and a key-value pair (e.g. `:name "Edward Cullen"`). It converts the value of the key-value pair to an integer if the key equals `:glitter-index`. Then it creates a new map that contains both the existing map and the post-converion key-value pair.



## Putting the pieces of the `reduce` back together
```clojure
(assoc {:name "Edward Cullen"} :glitter-index 3)
; => {:name "Edward Cullen", :glitter-index 3}
```

# <a name="conclusion"></a>Conclusion

# <a name="reflection"></a>Reflection


---
# notes

- things are nested instead of in an order like in Python (functional vs ?imperative?)
- longer post than I thought because hadn't thought about the need to explain function definition syntax
- so long, so helpful for me to learn
- way harder than I thought

## tools I used
- breaking things up in smaller parts
	- break things down, understand the things, put them together again
  - forget the specifics of the lower level when looking at the higher level
- write experiment code
- ClojureDocs both parameters and return values
- not worry too much about abstract data structures
- writing this is educational
- make a mistake in doing just vector while it was part of map, only realized when writing this post
- understand a function, e.g. the reduce, in its specific context instead of in a general way
- figure out what the first iteration of a loop, e.g. for the reduce, does and not bother with the rest


[^1]: Although it turns out you can [name an anonymous function](https://clojuredocs.org/clojure.core/fn#example-542692c7c026201cdc326977). This can be [useful](https://stackoverflow.com/questions/41683672/clojure-named-anonymous-function) for readability and in stack traces.

[^2]: Writing all of this out makes me appreciate how complicated and multi-layered all of this is. As *"Clojure for the Brave and True"* says in chapter 4:  
*"The collection abstraction is closely related to the sequence abstraction. All of Clojure’s core data structures—vectors, maps, lists, and sets—take part in both abstractions. The sequence abstraction is about operating on members individually, whereas the collection abstraction is about the data structure as a whole."*  
<br />
So we're dealing with an abstract data structure, the collection, which tells us something about what we can do with it as a whole. We're also dealing with a different abstract data structure, the lazy sequence, which tells us something about what we can do with its individual members, while it also tells us something about how this is implemented, i.e. [lazily](https://clojuredocs.org/clojure.core/lazy-seq). So now I'm wondering if I am correct in calling a lazy sequence a collection... I wrote about the sequence abstraction in [(clj 7)](link://slug/clj7-programming-to-abstractions-with-sequence-functions) and about the lazy sequences in [(clj 8)](link://slug/clj-8-some-notes-on-lazy-sequences-and-function-parameters).

[^3]: If you want to know how the parsing works, you can read it in the [online version of the book](https://www.braveclojure.com/core-functions-in-depth/#A_Vampire_Data_Analysis_Program_for_the_FWPD).

[^4]: Again, see the [online version of the book](https://www.braveclojure.com/core-functions-in-depth/#A_Vampire_Data_Analysis_Program_for_the_FWPD), if you're curious.
