<!--
.. title: Implementing counterstring, fake it till you make it, step-by-step, TDD, incrementally
.. slug: counterstring
.. date: 2025-01-04
.. category: 
.. tags: counterstring
.. type: text
-->

Last week I started to implement [PerlClip](https://www.satisfice.com/download/perlclip)'s [counterstring](https://www.satisfice.com/blog/archives/22) in TypeScript using [Preact](https://preactjs.com/). A counterstring is a string that tells you how long it is. For example a counterstring with length 9 looks like this: "`*3*5*7*9*`" - each number being the position of the asterisk following it. My main goal with this project is to learn more about front-end development.

Before I could start doing interesting front-end stuff, however, I needed to write a function that correctly generates counterstrings. Since I approached that in a way that I really enjoyed, inspired by [Llewellyn Falco](https://www.linkedin.com/in/llewellynfalco/)'s ["Fake it till you make it"](https://youtu.be/O1h9ho2G85Q?t=155), I figured it would make a good first post about this project.

The idea behind *"fake it till you make it"* is simple. Start with an implementation covering a single case ("fake it") and then pull it apart little-by-little until it becomes an actual program ("make it"). As Llewellyn explains in the video, the value of this technique is that it's a lot easier to start from a working example and proceed from there than it is to get complete requirements.

I did approach counterstring from the opposite direction as Llewellyn did with Fizzbuzz in the video, though. Llewellyn starts with FizzBuzz length 20, so a case covering all the logic. Then he refactors it using different techniques, such as separation and encapsulation. While I started with counterstring length 0, the most simple case, and then started tackling bigger lengths.


<!-- TEASER_END -->


## Counterstring length 0 {.small}

A counterstring of length 0 is simple, it's an empty string. So implementing it is easy:

```TypeScript
export function counterstring(length:number) {
    return "";
}
```

And testing it is too:
```TypeScript
test("counterstring length 0", () => {
    const result = counterstring(0);
    expect(result).toBe("");
})
```

Of course that's the only test my implementation does pass, but that's the point. I'm still very solidly in the "faking it"-phase.


## Counterstring length 1 {.small}

A counterstring with length 1 is just the asterisk:

```TypeScript
let result = "";

while (length > 0) {
	result = "*" + result;
    length =- 1;
}

return result;
```

It would have been simpler to use an `if/then/else` on `length` here instead of the `while`-loop. I was already anticipating longer lengths, though.

And this also needs a test:

```TypeScript
test("counterstring length 1", () => {
    const result = counterstring(1);
    expect(result).toBe("*");
```

*To be fair to the [historical record](https://github.com/j19sch/counterstring/commits/main/) this is not exactly how I implemented it. I did something less performant with reversing an array, because I had looked at PerlClips's source code. How that came about and what I learned from it, is for another blog post.*


## Counterstring length 2 {.small}

A counterstring with length 2 looks like this: "`2*`". So that gives us our first challenge: in our `while`-loop we need to decide whether the next string to add is either a position or an asterisk.

My solution was to keep track of that through `latestTokenPosition`, where "token" refers to the asterisk. So the `else` adds the asterisk to the result and sets `latestTokenPosition` to the position of that asterisk. The `if` adds that `latestTokenPosition` to our result and sets it back to `null`.

```TypeScript
let result = "";
let latestTokenPosition;

while (length > 0) {
    if (latestTokenPosition) {
    	result = latestTokenPosition.toString() + result;
        latestTokenPosition = null;
    else {
    	result = "*" + result
    	latestTokenPosition = length;
    }
    length =- 1;
}

return result;
```

And again we add a test for this case:
```TypeScript
test("counterstring length 2", () => {
    const result = counterstring(2);
    expect(result).toBe("2*");
})
```

## Let's parametrize those tests {.small}
At this point I got annoyed with how I was writing the tests, so I refactored them a parametrized solution:

```TypeScript
test.each([
    [0, ""],
    [1, "*"],
    [2, "2*"]
])("counterstring length %i", (length, expected) => {
    expect(counterstring(length)).toBe(expected);
})
```

## Skipping a challenge because I anticipated it {.small}

Something interesting happens when you go from a counterstring of length 2 ("`2*`") to one of length 3 ("`*3*`"). The length 2 counterstring starts with a position (the `2`). The length 3 counterstring starts with the asterisk.

So if you construct your counterstring from left to right, you need to figure out how to start. If you construct it from right to left (or rather: from end to start), you don't have that problem. The last character of a counterstring is always the asterisk. That's why my implemenation prepends to the result (e.g. `result = "*" + result`), because it's easier to start at the end and work your way back.

Had I used the "fake it till you make it"-technique in the way described by Llewellyn in the video, this is also where I would have gotten into trouble. Then I would have started with a counterstring of length 20. First as a hard-coded string, then pulling it apart until it became an actual program. Most likely I would not have ended up with a program that would work for counterlength 19, since lengths 19 and 20 have the same problem as lengths 2 and 3.


## Counterstring length up to 100 {.small}

The next challenge in implementing counterstring is: what if the position takes up more than one integer? A counterstring with length 10 like this: "`*3*5*7*10*`". My current implementation with `length =- 1` outputs something different, however. A string of length 11 that claims to be of length 10: "`2*4*6*8*10*`".

So instead of subtracting `1` from `length`, I needed to subtract the length of the string I just added to `result`:

```TypeScript
let result = "";
let latestTokenPosition;
let insertLength;

while (length > 0) {
    if (latestTokenPosition) {
    	result = latestTokenPosition.toString() + result;
    	insertLength = latestTokenPosition.toString().length;
        latestTokenPosition = null;
    else {
    	result = "*" + result;
    	insertLength = tokenLength;
    	latestTokenPosition = length;
    }
    length =- insertLength;
}

return result;
```

I could have taken a smaller step here. First deal with lengths up to `99` through an `if/then/else` on `length` and save the general solution for the next step. Nesting an `if` in an `if` in a `while`-loop is getting a bit much, though. And the general solution is straightforward enough.

With the parametrized tests, expanding them was easy. Running them is cheap too, so instead of aiming for minimal but sufficient coverage, I added enough example to illustrate what `counterstring` does exactly:

```TypeScript
test.each([
    [0, ""],
    [1, "*"],
    [2, "2*"]
    [3, "*3*"],
    [4, "2*4*"],
    [9, "*3*5*7*9*"],
    [10, "*3*5*7*10*"],
    [100, "*3*5*7*9*12*15*18*21*24*27*30*33*36*39*42*45*48*51*54*57*60*63*66*69*72*75*78*81*84*87*90*93*96*100*"]
])("counterstring length %i", (length, expected) => {
    expect(counterstring(length)).toBe(expected);
})
```

## What about lots and oops? {.small}

zero/one/many/lots/oops

lots: issue with list implementation
oops: obvious next step, negative numbers, strings (types?), etc.


## Closing thought about code walkthroughs {.small}

Revisiting and describing my code like this, has given me several ideas for how to refactor it. Mostly to make it easier to read. Seems like a good argument for code walkthroughs, even if it's to a [rubber duck](https://en.wikipedia.org/wiki/Rubber_duck_debugging).
