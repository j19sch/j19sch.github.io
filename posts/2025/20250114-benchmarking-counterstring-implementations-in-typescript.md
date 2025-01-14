<!--
.. title: Benchmarking counterstring implementations in TypeScript
.. slug: benchmarking-counterstring-implementations-in-typescript
.. date: 2025-01-14
.. category: programming & test automation
.. tags: counterstring, programming
.. type: text
.. description: Some things are faster than others.
-->

In my previous post "[Using "fake it till you make it" to implement counterstring](link://slug/using-fake-it-till-you-make-it-to-implement-counterstring)" I mentioned the implementation I included there, wasn't my initial implementation:

>  I did something less performant with reversing an array, because I had looked at PerlClips's source code. How that came about and what I learned from it, is for another blog post.

This is that blog post.

As a matter of fact, I currently have [8 different implementations](https://github.com/j19sch/counterstring/blob/951548092330182355401bbae3c9cc3776b52c01/src/alt-counterstrings.ts) of counterstring in TypeScript. And there are some interesting lessons to take, both from comparing the code of the different implementations, as from comparing the differences in performance.

<!-- TEASER_END -->

Before we do that, a quick recap of what a counterstring is. A counterstring is a string that tells you how long it is. For example a counterstring with length 9 looks like this: `*3*5*7*9*`. Each number tells you the position of the asterisk following the number.


# How I got to looking at PerlClip's implementation

[PerlClip](https://www.satisfice.com/download/perlclip) is the original implementation of counterstring by James Bach and Danny Faught. So when I wanted to write my own implementation and more importantly wanted to write tests for it, I tried to run PerlClip. Unfortunately that did not work.

If you try to get PerlClip to generate a counterstring on Linux, you get:

```
Can't call method "Set" on an undefined value at perlclip.pl line 180, <STDIN> line 1.
```

The PerlClip function that copies the counterstring to your clipboard, checks if you're on a Mac. If not, it assumes you're on Windows and does `$clip->Set($text);` As a quick fix, I changed the code to print to the console instead.

However, that got me to read the function that generates the counterstring. And while [it's been](https://www.perlmonks.org/?node_id=928829) [a while](https://github.com/j19sch/learning-perl-6th-edition) since I last did anything in Perl, I couldn't not see the `reverse()` in the line just above the one that called the past-to-clipboard function.

And that's how I ended up with a counterstring implementation that pushes each element of the counterstring to an array, then reverses it, and then joins it all into a string. Which is not exactly what PerlClip does, actually.


# The different choices in a counterstring implementation

## How to loop or shall we recurse?
EvilTester mentions in coding kata post: write a recursive version
remarkably easy after writing all the other ones
too long a counterstring and you run out of call stack
mostly a fun exercise


## one at a time or both at once

I did one at a time initially. Not as nice, because need to keep track of which one you're adding.
Both at once is the better solution.
one at a time does have the advantage you don't have the "what to do at the end"-problem described below


## do we actually need to reverse anything?

PerlClip and EvilTester reverse the thing to be added and reverse the result at the end
neither is necessary
TypeScript/JavaScript reverse strings through lists -> performance!
just concatenate the thing
EvilTester and elegance
but how to concatenate?


## What to do at the ~end~ ~beginning~ end

The tricky bit about counterstrings is that they can start in either of two ways. So you're working your way backwards generating the counterstring. If you're lucky, you get to add `2*` and you're done. The asterisk is on the second position, as indicated by the `2` on the first position in the string. If you're not so lucky, you add `3*` and then what? If you apply the logic you've been using so far, you should add `1*` resulting in `1*3*...` as the counterstring. That would not be a correct counterstring, though, since the `1` is at the zeroth position in the string. Making the counterstring one character longer than it says it is. So instead you need to add only the `*`, resulting in the counterstring `*3*...`.

### PerlClip
The PerlClip version (translated to TypeScript by me) does something clever:

```TypeScript
text = text + pip.repeat(target - text.length);
```

The `target` is the length of the counterstring you want, `text.length` is the length of the counterstring you have at that point. As we can deduce from my explanation above, either `text.length` will be one shorter than `target` or they will be equal. So the difference between the two will be either `1` or `0`. And that's the number of times a `pip` (the asterisk) will be added to the string. (The string will be reversed after this, hence the order of the concatenation.)


### EvilTester's version

EvilTester chose a different solution:

```TypeScript
let appendThis = count.toString() + "*";

if (appendThis.length > count) {
  appendThis = appendThis.substring(count, appendThis.length);
}
````

If the thing we want to add, is longer than the `count`, we append only part of `appendThis`. The `count` starts as the length of the counterstring you want and then gets decremented in a `while`-loop with the length of `appendThis`.

This `if`-statement can only resolve to true at the very end of the counterstring generation. Because `count` is the length of the string we want, while `appendThis.length` is the number of digits of `count` plus one (for the asterisk). So if `count` is for example `372`, then `appendThis.length` is `4`. If `count` is `37`, `appendThis.length` is `3`. Once we get to the single digits of `count`, e.g. `6`, `appendThis.length` is still smaller, i.e. `2`. It's only when `count` is either `0` or `1`, that the corresponding `appendThis.length` of `2` is larger. And `count` can't be `0`, because the condition of the `while`-loop is `count > 0`. So within the `if`-block, `count` has to be `1`.

The [`substring()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring) method, when given two arguments, will return the part of the string from the start index up to and excluding the end index. So what happens in the code above is that of the `appendThis` string, i.e. `1*`, the substring is taken, starting from position 1 and ending before position 2, i.e. `*`.


### My simpler implementation

Having reasoned through all of that, because I wanted to understand both PerClip's and EvilTester's implemenation, I was able to make my own solution a lot simpler:

```TypeScript
if (count === 1) {
	counterString = "*" + counterString;
}
```

The `count` works in the same way as in EvilTester's version. It starts as the desired length of the counterstring and then the length of each string added to the counterstring, is subtracted from it. Either `count` will go from `2` to `0` and we have our full counterstring. Or `count` will go from `3` to `1` and then we prepend one more asterisk.

Since that's not obvious just from the code, I added the following comment:

``` TypeScript
// At this point length is either 1 (the while-loop prepended 3*) or 0 ( the while-loop prepended 2*).
// If length is 1, we need to prepend "*" to get the correct counterstring. If it's 0, we're done.
``


# Performance of the different implementations

PerlClip performance does not say anything about performance in Perl.