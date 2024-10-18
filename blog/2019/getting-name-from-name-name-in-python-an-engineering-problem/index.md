<!--
.. title: Getting [name] from "Name: [name]" in Python - an engineering problem
.. slug: getting-name-from-name-name-in-python-an-engineering-problem
.. date: 2019-08-26 21:27:38 UTC+02:00
.. tags: python, programming, semantics
.. category: programming & test automation
.. link: 
.. description:
.. type: text
-->

Today I was presented with an interesting engineering problem. (Important later: context was the code of an auto-test.) Given a string of the format "Name: [name]", what's the best way to get the [name] in Python?

There are several options:

- `lstrip()`
- `split()`
- `replace()`
- string slicing
- regex

So let's look at each of them and then I'll explain which one I prefer and why. All examples are in Python 3.6, using the [Python Interpreter](https://docs.python.org/3.6/tutorial/interpreter.html).

<!-- TEASER_END -->

## lstrip()

```python
>>> our_string = "Name: this-is-the-name"
>>> our_string.lstrip("Name: ")
'this-is-the-name'
```

That seems to work until we try a different string:

```python
>>> our_other_string = "Name: a name"
>>> our_other_string.lstrip("Name: ")
'name'
```

This may seem weird, but `lstrip()` is doing exactly [what it says it will do](https://docs.python.org/3.6/library/stdtypes.html#str.lstrip): "The chars argument is not a prefix; rather, all combinations of its values are stripped." So it will continue stripping until it encounters the first character that doesn't match any character in the string we gave to `lstrip()`.

To fix that, we can do:

```python
>>> our_other_string = "Name: a name"
>>> our_other_string.lstrip("Name:").lstrip()
'a name'
```

Where the first `lstrip()` won't get beyond the space and the second `lstrip()` will get rid of that space for us.


## split()

```python
>>> our_string = "Name: this-is-the-name"
>>> our_string.split(":")[1].lstrip()
'this-is-the-name'

>>> our_other_string = "Name: a name"
>>> our_other_string.split(":")[1].lstrip()
'a name'
```

The `split()` method will [split the string](https://docs.python.org/3.6/library/stdtypes.html#str.split) on the colon (:) into a list with two items. We get the second item with the `[1]` (list indices start at 0). We strip off the leading space.


## replace()

```python
>>> our_string = "Name: this-is-the-name"
>>> our_string.replace("Name: ", "", 1)
'this-is-the-name'
 
>>> our_other_string = "Name: a name"
>>> our_other_string.replace("Name: ", "", 1)
'a name'
```

The `replace()` method replaces parts of a string. So here we replace "Name: " with an empty string - deleting it. The '1' argument at the end tells `replace()` to only replace the first occurrence:

```python
>>> too_many = "Name: more Name: please"
>>> too_many.replace("Name: ", "")
'more please'
 
>>> too_many.replace("Name: ", "", 1)
'more Name: please'
```


## string slicing

Python allows you to grab slices from a string similar to what you do from a list (as we did for the `split()` above).

```python
>>> our_string = "Name: this-is-the-name"
>>> our_string[6:]
'this-is-the-name'
 
>>> our_other_string = "Name: a name"
>>> our_other_string[6:]
'a name'
```

The number before the colon tells Python where to start, the one after the colon where to end. So `[6:]` means to start after the 6th character (or rather from index 6, since indices start at 0) and continue until the end of the string (because no number was given).


## regex

```python
>>> import re
>>> regex = "(^Name: )(.+)"
 
>>> our_string = "Name: this-is-the-name"
>>> re.match(regex, our_string).group(2)
'this-is-the-name'
 
>>> our_other_string = "Name: a name"
>>> re.match(regex, our_other_string).group(2)
'a name'
```

The regular expression is defined in the `regex` variable. It describes a string that starts with "Name: " and is followed by at least one other character. The parentheses define groups, which we'll use to get the part we're interested in, i.e. the part after "Name: ".

`match()` will return a [match object](https://docs.python.org/3.6/library/re.html#match-objects) if zero or more characters at the beginning of the string [match](https://docs.python.org/3.6/library/re.html#re.match) the regular expression pattern. Which means we don't actually need the '^' at the start of our regex to only match the start of the string.

`group()` will return [one or more subgroups](https://docs.python.org/3.6/library/re.html#re.match.group) of the match. The zeroth group is the entire match. Thanks to the parentheses in our regex definition we also have a first group ("Name: ") and a second group (the thing we're after).


## which one to use

Going through the options they all have disadvantages:

- `lstrip()` strips characters not strings, but we want to strip a certain string.
- `split()` returns two things of which we need only one after we have `lstrip()`-ed it.
- `replace()` returns a changed copy of a string, while we just want to parse the original string.
- string slicing ditches the first 6 characters not caring what they are.
- regex feels like a bit too much.

However, two of them have a distinct advantage over the others.

As I said in the introduction, the context of this problem was the code of an auto-test. More specifically, the "Name: [name]" is returned by Selenium WebDriver as the content of an html tag. So without knowing or seeing the application, just from reading the code that retrieves the content of the tag, you have no idea what this string is that we are manipulating.

So that's the first thing we want from our solution: it should give as much information about the string we are manipulating as possible. This means that `split()` and string slicing are not an option. The `split()` solution only tells you there's a colon followed by a whitespace in the string. The string slicing solution only tells you there are at least 7 characters in the string.

Secondly, the solution should capture our intention as clearly as possible, which is getting the [name] from the string "Name: [name]". That means `lstrip()` is out, because it strips characters, not a specific string.

You could argue something similar for `replace()`, since the "replace with empty string" is a somewhat clever hack to use something intended for editing to retrieve a specific part of a string. On the other hand, the code is clear enough - unlike `lstrip()` where the characters-not-string might become a bit of a surprise down the line.

So basically we're left with `replace()` and regex. At the office we hadn't figured out that `replace()` has a count argument, so based on ‘But what if there's a "Name: " in the content of the tag?', we went with the regex solution. Regardless, I still think that the regex solution is the clearest one.


## conclusion
The [Zen of Python](https://www.python.org/dev/peps/pep-0020/) states: "Explicit is better than implicit." This one sentence is the reason I can write a whole blog post about what the best way is to get [name] from "Name: [name]". Code being explicit about what it's doing and what it is trying to do, matters. The more explicit it is, the better it can serve as documentation.

But what if you have to choose? The regex solution is indeed the clearest - assuming you know some regex, that is. So the solution that's most explicit about what the string is and what our intentions with it are, is the least explicit about how it does what it does. (Also, if you have trouble understanding what it does, it will be hard to determine the intentions behind the code.) So what now?

Personally I will always trade the code being less explicit about what it does for being more explicit about the thing-under-test and what my intentions are. Because figuring out what the thing-under-test exactly does and what someone's intentions were, are hard things to do. Learning some new things about a programming language or tool, significantly less so - even if it's regex.

---

*This post was originally published on my old blog.*
