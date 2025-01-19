<!--
.. title: Benchmarking counterstring implementations in TypeScript
.. slug: benchmarking-counterstring-implementations-in-typescript
.. date: 2025-01-14
.. category: programming & test automation
.. tags: counterstring, programming
.. type: text
.. description: Perl was right: there's more than one way to do it.
-->


TODO:
- nine implementations: added optimizedButSeparate
- name of optimizedButSeparate
- post title and description if no benchmark
- next post: where does the performance difference of optimizedButSeparate come from?
  - the extra if? the extra subtraction? the two large concats instead of a small one and a large one


---

In my previous post "[Using "fake it till you make it" to implement counterstring](link://slug/using-fake-it-till-you-make-it-to-implement-counterstring)" I mentioned the implementation I included there, wasn't my initial implementation:

>  I did something less performant with reversing an array, because I had looked at PerlClips's source code. How that came about and what I learned from it, is for another blog post.

This is that blog post.

As a matter of fact, I currently have [8 different implementations](https://github.com/j19sch/counterstring/blob/951548092330182355401bbae3c9cc3776b52c01/src/alt-counterstrings.ts) of counterstring in TypeScript. Including two that are not mine: one is from PerClip but translated to TypeScript, the other is EvilTester's implementation. There are some interesting lessons to take, both from comparing the code of the different implementations, as from comparing the differences in performance.

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

### Looping up or looping down

The most straightforward way to construct a counterstring is by using a decrementing `while`-loop. You take the desired length of the counterstring, add a number and an asterisk to your counterstring, then subtract the length of what you added from the desired length, rinse and repeat. At least while that desired length is larger than 0. (Or larger than 1, but that's for later in this post.)

That's not what PerlClip does however. The Perl version of PerClip use an `if`-statement with [`last`](https://perldoc.perl.org/functions/last) and [`redo`](https://perldoc.perl.org/functions/redo):

```Perl
{
	if (length($text)+length($pos)+1 > $target)
	{
		$text .= $pip x ($target - length($text));
		last;
	}
	$text .= $pip.reverse($pos);
	$pos -= length($pos)+1;
	redo;
}
```

For my translation to TypeScript I decided to refactor it a little:

```TypeScript
while (text.length + pos.toString().length + 1 <= target) {
  text = text + pip + pos.toString().split("").reverse().join("");
  pos = pos - (pos.toString().length + 1);
}

text = text + pip.repeat(target - text.length);
```

What I find interesting about this implementation is the condition: comparing `text.length + pos.toString().length + 1` to `target`. This only makes sense when you realize that `pos.toString().length + 1` is the length of next element you plan to add to the counterstring. So `text.length + pos.toString().length + 1` is the length of our counterstring after adding the next element. If that's still smaller than the `target`, we add it. If it's not, we do something else, which I'll cover in a later section.

I think PerlClip's way of implementing this loop is significantly harder to understand than the implementation I describe at the start of this section. The reason for that is that the condition in the `while` (or in the `if` in the Perl version) only makes sense, once you understand the rest of the function and return to the condition. I'm not sure if this anti-pattern has a name. If not, I'd name it used-before-meaningful or something.


### Recursion

In EvilTester's blog post "[Testing Related Code Katas](https://www.eviltester.com/blog/eviltester/programming/2019-02-27-programming-katas-for-testers/)" he lists a number of programming exercises based on counterstrings. The sixth one tells you to *"find a different implementation approach e.g. if you used recursion change it to do something else, if you didn’t use recursion try that, if you were reversing strings try doing it without reversing strings"*.

So I did:

```TypeScript
function recursiveFunction(length: number, counterString = "") {
  if (length > 1) {
    const prependThis = length.toString() + "*";
    counterString = prependThis + counterString;
    return recursiveFunction(length - prependThis.length, counterString);
  } else if (length === 1) {
    return "*" + counterString;
  } else if (length === 0) {
    return counterString;
  }
}
````

I wouldn't recommend this as a solution. If you try to generate a really long counterstring, you'll run out of call stack. It was a fun exercise, though. And I pleasantly surprised myself by getting it right immediately. I wrote the code, ran the tests, and they were all green. Having worked through all the other implementations first, really paid off in that way.


## Add one at a time or both at once

In my initial implementation I used the variable `latestTokenPosition` to decide if I should add a number of an asterisk to the counterstring. If `latestTokenPosition` was `null`, I added the asterisk, i.e. "the token", and I set `latestTokenPosition` to the position of the token. If `latestTokenPosition` was not `null`, I added the value of `latestTokenPosition` to the counterstring and then set it to `null`.

Then I looked at PerlClip's and EvilTester's implementation and noticed that they added the number and the asterisk at the same time. So I changed my approach to doing the same, because it saves you from introducing the `latestTokenPosition` variable that persist outside the `while`-loop and that you use to keep track what's the next thing you need to add to the counterstring.

Looking back at my initial implemenation, I do like how it captures really well how a counterstring works. You add an asterisk, then the position of that asterisk, etc. etc. You also don't run into the problem of [how to end the counterstring](link://slug/benchmarking-counterstring-implementations-in-typescript#what-to-do-at-the-end).


So I updated my initial implementation with the other things I've learned:

```TypeScript
function optimizedButSeparate(length: number) {
  let counterString = "";

  let latestTokenPosition: number = null;

  while (length > 0) {
    if (latestTokenPosition === null ) {
      counterString = "*" + counterString
      latestTokenPosition = length
      length = length - 1
    } else {
      counterString = latestTokenPosition.toString() + counterString
      length = length - latestTokenPosition.toString().length
      latestTokenPosition = null
      
    }
  }

  return counterString;
}
```

Then I ran my performance benchmarks (more on those later) and it does come with a performance cost.


## Do we actually need to reverse anything?

Both PerlClip's and EvilTester's implementation build the string in reverse order. So for a counterstring with length 9, they append `*9` to the then still empty counterstring, then they append `*7` etc., until they have `*9*7*5*3*`. Then these implementations reverse the whole string, resulting in the correct counterstring of `*3*5*7*9*`.

Unfortunately in TypeScript there's no great way to reverse a string. A common way to do this - and the one used in EvilTester's implementation - is to transform the string to an array, reverse the array, and then join the array back into a string: `counterString.split("").reverse().join("")`. More on performance in the next post, but for now let's just say performance is not great. (Note that I'm not making a claim here about performance of PerlClip in Perl. Perl has `reverse()` to reverse a string, which presumably performs a lot better than the whole array-route.)

Instead of reversing strings, you can concatenate them, still building up the counterstring in reverse. There are multiple ways to do this: the `+` operator, the `concat()` method, or template strings (the ones with the backticks). All of these perform better than reversing strings.

So ignoring the problem of what to do at the end (see the next section), I'm very much in favor of basically building up your counterstring like this:

```TypeScript
counterString = count.toString() + "*" + counterString
return counterString
````

over doing it like this:

```TypeScript
appendThis = "*" + count.toString().split("").reverse().join("");
counterString = counterString + appendThis;
return counterString.split("").reverse().join("");
```


## What to do at the ~end~ ~beginning~ end <a id=what-to-do-at-the-end/>

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

Having reasoned through all of that, because I wanted to understand both PerClip's and EvilTester's implementation, I was able to make my own solution a lot simpler:

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
````


## The implementation I ended up with

Having worked through all of these different options, I ended up with the following implementation:

```TypeScript
function counterString(length: number) {
  let counterString = "";

  while (length > 1) {
    const prependThis = length.toString() + "*";
    counterString = prependThis + counterString;
    length -= prependThis.length;
  }

  if (length === 1) {
    counterString = "*" + counterString;
  }

  return counterString;
}

```

And looking at it, makes me think there's one more change I'd like to make. Changing the condition of the `while`-loop to `length >= 2`, because it better captures the intent of the code.


# Performance of the different implementations

next post?

PerlClip performance does not say anything about performance in Perl.