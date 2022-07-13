<!--
.. title: (clj 10) The mapify function of (clj 9) revisited
.. slug: clj-10-the-mapify-function-of-clj-9-revisited
.. date: 2022-07-13 21:02:36 UTC+02:00
.. tags: clojure, programming, brave clojure
.. category: clojure
.. link: 
.. description: 
.. type: text
-->

In my [previous Clojure post](link://slug/clj-9-how-to-figure-out-what-a-function-does) I covered the code example at the end of Chapter 4 of ["Clojure for the Brave and True"](https://www.braveclojure.com/clojure-for-the-brave-and-true/). Or rather, I focused on a single function in the example, called `mapify`, and described how I figured out what it does. At the [end of that post](link://slug/clj-9-how-to-figure-out-what-a-function-does#the-mapify-function) I shared my disappointment:

> Having done all this work (and writing) I can't help but feel a bit disappointed. In the end, the function does not seem to do a lot.

And I shared a Python version of that same function, claiming that it basically does the same thing[^1].

However, less than a week after publishing the post, I got a very kind email by someone named Martin. And *"in defence of clojure and to maybe reduce your disappointment"* Martin pointed out the two versions are not as equivalent as I claimed, because the Clojure version is more general than the Python version. So I looked at the two version again and the way they are different turned out to be quite interesting - interesting enough to write a follow-up post.

<!-- TEASER_END -->

# The Cojure version of `mapify`
The Clojure version looks like this:

```clojure
(defn mapify
  [rows]
  (map (fn [unmapped-row]
         (reduce (fn [row-map [vamp-key value]]
                   (assoc row-map vamp-key (convert vamp-key value)))
                 {}
                 (map vector vamp-keys unmapped-row)))
       rows))
```

It expects an argument similar to:
```clojure
(["Edward Cullen" "10"] ["Bella Swan" "0"])
```
and transforms it into a sequence of maps:
```clojure
[{:name "Edward Cullen" :glitter-index 10} {:name "Bella Swan" :glitter-index 0}]
```

The main thing to note about the Clojure version are the `vamp-keys` and the `convert`, which were defined earlier in [the example](https://www.braveclojure.com/core-functions-in-depth/#A_Vampire_Data_Analysis_Program_for_the_FWPD).

The `vamp-keys` lists the keys that are used to transform each sequence of the input argument to a map:
```clojure
(def vamp-keys [:name :glitter-index])
```
So this variable describes our expectations of the input: a name and a glitter index.

The `convert` function uses the `conversions` variable to convert a value in our map:
```clojure
(def conversions {:name identity
                  :glitter-index str->int})

(defn convert
  [vamp-key value]
  ((get conversions vamp-key) value))

```

If the key is `:name`, it applies the [`identity`](https://clojuredocs.org/clojure.core/identity) function, i.e. the value is unchanged. If they key is `:glitter-index`, it converts the value from a string to an integer. That's needed, because as you can see above, the argument to `mapify` has the glitter index still as a string. So the `conversions` variable describes if/how we want to convert the values in our map.

The result of having `vamp-keys` and `convert` defined separately in this way is that, as Martin writes:

> The clojure code is more general and allows to add new columns/keys by just adding the key to the vamp-keys and the column to the data - and probably a conversion to conversions.



# The Python version of `mapify`
My Python version looks like this:
```python
vamp_keys = ["name", "glitter-index"]

def mapify(rows):
  return [
    {
      vamp_keys[0]: row[0],
      vamp_keys[1]: int(row[1])
    }
    for row in rows
  ]
```
Let's start with the conversion: there is no separate `convert` function in my Python version. The conversion happens inside the function. (Inside the `return` statement even!)

There is a separate `vamp_keys` variable as in the Clojure version, but that variable is not used in the same way. The Python version refers to the items in `vamp_keys` by their index, e.g. `vamp_keys[0]`. The Clojure version on the other hand, uses `map` to loop through the `vamp-keys` and the `unmapped-row`.

What this means is that if you'd want to add for instance "age" to the data, in the Clojure version you'd only need to add `"age"` to `vamp-keys` and `:age str->int` to `conversions`. The `mapify` function can remain exactly the same. That would not be the case in the Python version. There you'd need to update both `vamp_keys` and the `mapify` function. A truly equivalent version in Python would provide that same flexibility, instead of taking the shortcut as in my version[^2].


# Why does this difference matter?

So the Clojure version is more general and can accommodate changes in the data structure without any changes to the `mapify` function. Does that matter?

In a weird sense it doesn't. The whole code example is meant as a summary of chapter 4 of ["Clojure for the Brave and True"](https://www.braveclojure.com/clojure-for-the-brave-and-true/). So it doesn't need to be general, it needs to illustrate the contents of that chapter.

And yet I find the difference between the two versions intriguing. Not as in my previous post where I was a little disappointed that my simpler Python version basically does the same thing as the Clojure version[^3]. It's clear to me now that that's not true. (Unless you want to make the "basically" do a lot of work.) Rather, I'm intrigued by the difference in what information is stored where in the two versions.

The Clojure version has the information about what kind of argument the `mapify` function expects, in `vamp-keys` and `conversions`. This means that once you understand the code, you can forget most of it again. All you have to remember is what `mapify` does on a very high level and that changes to the function's argument require changes to `vamp-keys` and `conversions`.

That's not the case with the Python version. There you do have to understand what the `mapify` function does in detail, so you can update it together with the `vamp_keys`. For this particular code example that might not be that big a deal, because the function is rather straightforward. Yet it does still illustrate an important question about structuring your code: where do you put the key elements?



[^1]: I did also add this footnote: *"The Python code does do the `convert` in a separate function. It would also return a different result than the Clojure code if the data would have more than two items per row."*

[^2]: In my defense, this difference did cross my mind very briefly. I dismissed it without giving it much thought, though. Which is a valuable reminder to not just dismiss that little voice in the back of your head.

[^3]: Martin also shared a Clojure code equivalent to my Python version, so without that flexibility, and lo and behold, they look very similar.
