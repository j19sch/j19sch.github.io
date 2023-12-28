<!--
.. title: One lesson from every programming language I've used
.. slug: one-lesson-from-every-programming-language-ive-used
.. date: 2023-12-28
.. tags: programming, python, clojure
.. category: programming & test automation
.. link: 
.. description: 
.. type: text
-->

Twelve to be exact. 

---

Throughout the years I've used quite a few different programming languages. Listing these for myself made me wonder what I had learned - beyond being able to write some code in them. Turns out I did learn at least one more general lesson from each language.

Before I share those lessons, I need to make one disclaimer. I am being generous with the meaning of "use". Some of these I've only done coding exercises in. One of them (PHP) I've used for a total of 10 minutes, but that did save the day for a whole team.

Python is probably the only one on the list I can claim a proper level of proficiency in. As you can see Python is about halfway down the list, which I did my best to put in chronological order. I think that does a great job of showing that (1) it's ok to explore different languages before diving deeper into a single one; 2) having one "base language" helps

briefer explorations both before and after profiecency, learn from





bigger lesson of this post:
- ok to explore before diving deeper
- value in short excursions after a base in a language
- chronologically

<!-- TEASER_END -->


# Perl: languages have a personality.
The Perl motto is *"There's more than one way to do it."*[^1] and it lives up to that motto. Compare that with Python's *"There should be one-- and preferably only one --obvious way to do it."*[^2] They might be similar in some areas, e.g. both are considered easy to learn scripting languages, using one or the other definitely feels different.

[^1]: https://perldoc.perl.org/perl#NOTEShttps://perldoc.perl.org/perl#NOTES
[^2]: https://peps.python.org/pep-0020/


# SQL: you don't need to know all of the language.
My SQL is very limited. I know how to get data from one or more tables. I can sort and group data. I can get distinct values. And that's about it. The times I've added or updated data, or dropped a table, I can probably count on the fingers of one hand.


# PHP: sometimes you don't need to know the language all.
Many years ago I was the lead for testing an enterprise service bus. It wrote its logs to a database, so we used SQL to look up log entries. The end-to-end test team wasn't comfortable using SQL, so the project's test automation engineer had built a simple PHP front-end to the logging database.

One day, well after the test automation engineer had left, because they had delivered their framework, the end-to-end team was in a light panic. A new service was available in the service bus, but it was not present in the PHP front-end. No one had an idea how to fix that.

So I asked if someone had the PHP code. I had no idea if I'd be able to do anything, but I figured looking at the code whould tell me if there's anything I could do. Luckily the code was short and well-structured. At the top of the file an array of services was defined. I added the new one and the tool was working again.


# VBA for Excel: documentation matters.



  - documentation matters


# Java: it's not because it's hidden that it doesn't happen.
Java is verbose and feels clunky (at least to me). One thing I do appreciate about its verbosity, is that it shows you a lot about what happens in Java. In a less verbose language, those things are either done for you, or aren't done at all / very differently.


# Python: language design matters.
I'm a big fan of the [list](https://realpython.com/list-comprehension-python/) and [dictionary comprehension](https://realpython.com/iterate-through-dictionary-python/#iterating-through-dictionaries-comprehension-examples) in Python. I really miss them when I'm working in a different language and have to use `filter` or `map` instead.

Guido van Rossum, the creator of Python, even [proposed to cut](https://www.artima.com/weblogs/viewpost.jsp?thread=98196) Python's `filter()` and `map()` from Python 3. That did not end up happening, but Guido's post is still great to get an insight in how he thought about what Python should be.


# Javascript: it's not only about language design.
JavaScript as a language is not great[^3]. It is widely popular, though. It started in the browser in the '90s and by now it runs basically everywhere. 


[^3]: The lightning talk ["Wat" by Gary Bernhardt](https://www.destroyallsoftware.com/talks/wat) from CodeMash 2012 has some great examples. Skip to 1:21 in the video for the JavaScript weirdness.


# Bash: sometimes there isn't a lesson.
In a previous job I had a laptop running Linux. Mirroring my screen to an external display in meetings was a pain, because scaling didn't work. So I wrote a Bash script to calculate the correct scaling and apply it through `xrandr`.

I did enjoy spending some time in Bash, but I'm not really sure I learned anything from it. And while I no longer use a Linux machine at work, I do still use the script on my personal laptop. So it seems the thing I learned the least from, is the thing I've had to most use from.


# Clojure: things can be different.
  - languages can be different
  - functional programming in Lisp family

# TypeScript: design time and run time are not the same.
  - design time and run time are not the same

# Lua: testability matters.
  - layer for testability
  - tests have to run inside simulator, because Lua changes and SDK (I think, works well enough)
  - linter needed extension for lua changes

# Rust: compiler errors can be helpful.
  - compiler errors can be great
