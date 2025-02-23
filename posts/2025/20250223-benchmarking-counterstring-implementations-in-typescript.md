<!--
.. title: Benchmarking counterstring implementations in TypeScript
.. slug: benchmarking-counterstring-implementations-in-typescript
.. date: 2025-02-23
.. category: programming & test automation
.. tags: counterstring, programming
.. type: text
.. description: You can concatenate faster than you can reverse.
-->

Earlier this year I posted about how I [implemented a counterstring function](link://slug/using-fake-it-till-you-make-it-to-implement-counterstring) using "fake it till you make it". I also posted about [different ways](link://slug/comparing-counterstring-implementations-in-typescript) to implement counterstrings. In this post, I want to share how those different implementations compare performance-wise.

To do this, I used both [Tinybench](https://github.com/tinylibs/tinybench) and [vitest bench](https://vitest.dev/guide/features.html#benchmarking) (which uses Tinybench). The results are basically the same, but their default output is slightly different.


# The nine implementations

Before I present the results, I should describe the different implementations and how they differ from each other. The [actual code of each implementation](https://github.com/j19sch/counterstring/blob/04883b7bb2f3e99f7be81ffa58e4ac5f934d276b/src/alt-counterstrings.ts) is available on GitHub. Here I'll only mention what makes each implementation interesting compared to the others:

<!-- TEASER_END -->

- `createListAndReverseIt`: creates the counterstring as a list, starting at the end of the string, appending the token and the numbers as separate element, then reverses the list and turns it into a string.
- `evilTester`: creates the counterstring as a string, but backwards, adding token and number in the same operation, then reverses the whole string. This version is copied from [EvilTester's blog post](https://www.eviltester.com/blog/eviltester/chrome-extensions/2019-02-19-counterstring-snippets/#counterstring-generation-function) about his counterstring Chrome extension.
- `evilTesterCreateListAndReverseIt`: creates the counterstring as a list instead of a string, starting at the end, adding token and number in the same operation, then reverses the list and turns it into a string.
- `perClipInTS`: essentially the same as `evilTester`, translated by me from [the original Perl](https://www.satisfice.com/download/perlclip) to TypeScript.
- `recursiveFunction`: completely different from all other implementation, because recursion, runs out of stack for long counterstrings.
- `whileAndIfButSeparate`: prepends to a string instead of reversing a list, but adds token and number separately.
- `whileAndIfWithPlus`: prepends to a string, adding token and number in the same operation, uses `+` for string concatenation.
- `whileAndIfWithConcat`: prepends to a string, adding token and number in the same operation, uses `concat()` for string concatenation.
- `whileAndIfWithTemplateString`: prepends to a string, adding token and number in the same operation, uses template strings for string concatenation.


# The results

Below are the results of running benchmarks on those nine implementations. Since it's a measurement over a number of samples, I ran the benchmarks twice with each of the two tools, Tinybench and Vitest bench. This way you can see for yourself what variations there are and how meaningful they are.

All benchmarks were run for a counterstring with length 1.000. 


## Tinybench

```
┌─────────┬────────────────────────────────────┬──────────────────┬────────────────────┬────────────────────────┬────────────────────────┬─────────┐
│ (index) │ Task name                          │ Latency avg (ns) │ Latency med (ns)   │ Throughput avg (ops/s) │ Throughput med (ops/s) │ Samples │
├─────────┼────────────────────────────────────┼──────────────────┼────────────────────┼────────────────────────┼────────────────────────┼─────────┤
│ 0       │ 'createListAndReverseIt'           │ '89422 ± 1.04%'  │ '87715 ± 1254.00'  │ '11307 ± 0.39%'        │ '11401 ± 164'          │ 1119    │
│ 1       │ 'evilTester'                       │ '354031 ± 1.65%' │ '341984 ± 2804.00' │ '2859 ± 1.02%'         │ '2924 ± 24'            │ 283     │
│ 2       │ 'evilTesterCreateListAndReverseIt' │ '58279 ± 1.34%'  │ '56386 ± 1068.50'  │ '17523 ± 0.39%'        │ '17735 ± 335'          │ 1716    │
│ 3       │ 'perClipInTS'                      │ '362797 ± 0.83%' │ '355694 ± 2303.50' │ '2767 ± 0.64%'         │ '2811 ± 18'            │ 276     │
│ 4       │ 'recursive'                        │ '45464 ± 1.31%'  │ '44154 ± 774.00'   │ '22457 ± 0.32%'        │ '22648 ± 393'          │ 2200    │
│ 5       │ 'whileAndIfButSeparate'            │ '36134 ± 1.15%'  │ '34983 ± 613.00'   │ '28304 ± 0.28%'        │ '28586 ± 501'          │ 2768    │
│ 6       │ 'whileAndIfWithConcat'             │ '27716 ± 1.72%'  │ '26323 ± 662.00'   │ '37452 ± 0.29%'        │ '37990 ± 951'          │ 3609    │
│ 7       │ 'whileAndIfWithTemplateString'     │ '28945 ± 1.57%'  │ '27704 ± 305.00'   │ '35656 ± 0.26%'        │ '36096 ± 399'          │ 3455    │
│ 8       │ 'whileAndIfWithPlus'               │ '27142 ± 1.44%'  │ '26099 ± 552.00'   │ '37953 ± 0.25%'        │ '38316 ± 812'          │ 3685    │
└─────────┴────────────────────────────────────┴──────────────────┴────────────────────┴────────────────────────┴────────────────────────┴─────────┘

```

```

┌─────────┬────────────────────────────────────┬──────────────────┬────────────────────┬────────────────────────┬────────────────────────┬─────────┐
│ (index) │ Task name                          │ Latency avg (ns) │ Latency med (ns)   │ Throughput avg (ops/s) │ Throughput med (ops/s) │ Samples │
├─────────┼────────────────────────────────────┼──────────────────┼────────────────────┼────────────────────────┼────────────────────────┼─────────┤
│ 0       │ 'createListAndReverseIt'           │ '89954 ± 1.49%'  │ '87752 ± 1141.50'  │ '11308 ± 0.42%'        │ '11396 ± 148'          │ 1112    │
│ 1       │ 'evilTester'                       │ '352842 ± 1.61%' │ '342107 ± 2563.00' │ '2867 ± 0.98%'         │ '2923 ± 22'            │ 285     │
│ 2       │ 'evilTesterCreateListAndReverseIt' │ '58529 ± 1.69%'  │ '56206 ± 1137.00'  │ '17566 ± 0.41%'        │ '17792 ± 361'          │ 1709    │
│ 3       │ 'perClipInTS'                      │ '365456 ± 0.90%' │ '357899 ± 3029.50' │ '2748 ± 0.69%'         │ '2794 ± 24'            │ 274     │
│ 4       │ 'recursive'                        │ '45562 ± 1.41%'  │ '44280 ± 781.00'   │ '22420 ± 0.31%'        │ '22584 ± 400'          │ 2195    │
│ 5       │ 'whileAndIfButSeparate'            │ '36294 ± 1.14%'  │ '35100 ± 602.50'   │ '28199 ± 0.30%'        │ '28490 ± 489'          │ 2756    │
│ 6       │ 'whileAndIfWithConcat'             │ '27504 ± 1.70%'  │ '26254 ± 631.00'   │ '37615 ± 0.27%'        │ '38089 ± 917'          │ 3636    │
│ 7       │ 'whileAndIfWithTemplateString'     │ '29045 ± 1.76%'  │ '27712 ± 331.00'   │ '35663 ± 0.26%'        │ '36085 ± 432'          │ 3443    │
│ 8       │ 'whileAndIfWithPlus'               │ '27438 ± 1.55%'  │ '26266 ± 587.00'   │ '37657 ± 0.27%'        │ '38072 ± 852'          │ 3645    │
└─────────┴────────────────────────────────────┴──────────────────┴────────────────────┴────────────────────────┴────────────────────────┴─────────┘

```


## Vitest bench


```
 ✓ src/counterstring.bench.ts > counterstring 10.000 5463ms
     name                                     hz     min     max    mean     p75     p99    p995    p999     rme  samples
   · createListAndReverseIt            11,316.91  0.0806  0.5631  0.0884  0.0873  0.1769  0.2184  0.4049  ±0.60%     5659
   · evilTester                         2,880.72  0.3286  0.7000  0.3471  0.3425  0.5902  0.6176  0.6949  ±0.58%     1441
   · evilTesterCreateListAndReverseIt  17,479.24  0.0516  0.5128  0.0572  0.0559  0.0830  0.2087  0.4172  ±0.78%     8740
   · perClipInTS                        2,762.65  0.3419  0.9007  0.3620  0.3558  0.6097  0.6700  0.7529  ±0.63%     1382   slowest
   · recursiveFunction                 21,164.81  0.0431  0.5269  0.0472  0.0457  0.0638  0.2458  0.3985  ±0.92%    10583
   · whileAndIfButSeparate             24,820.37  0.0365  0.4621  0.0403  0.0391  0.0611  0.1877  0.2385  ±0.71%    12411
   · whileAndIfWithConcat              32,319.46  0.0281  0.3969  0.0309  0.0301  0.0477  0.1586  0.1956  ±0.65%    16160   fastest
   · whileAndIfWithPlus                32,102.33  0.0281  0.4157  0.0312  0.0304  0.0475  0.1600  0.1885  ±0.67%    16052
   · whileAndIfWithTemplateString      30,220.66  0.0306  0.4595  0.0331  0.0319  0.0496  0.1621  0.1983  ±0.65%    15111

 BENCH  Summary

  whileAndIfWithConcat - src/counterstring.bench.ts > counterstring 10.000
    1.01x faster than whileAndIfWithPlus
    1.07x faster than whileAndIfWithTemplateString
    1.30x faster than whileAndIfButSeparate
    1.53x faster than recursiveFunction
    1.85x faster than evilTesterCreateListAndReverseIt
    2.86x faster than createListAndReverseIt
    11.22x faster than evilTester
    11.70x faster than perClipInTS
```

```
 ✓ src/counterstring.bench.ts > counterstring 10.000 5462ms
     name                                     hz     min     max    mean     p75     p99    p995    p999     rme  samples
   · createListAndReverseIt            11,320.29  0.0805  0.4932  0.0883  0.0879  0.1312  0.2157  0.2720  ±0.47%     5661
   · evilTester                         2,819.11  0.3270  0.7586  0.3547  0.3523  0.6031  0.6753  0.7465  ±0.70%     1410
   · evilTesterCreateListAndReverseIt  17,548.40  0.0515  0.4589  0.0570  0.0559  0.0882  0.2108  0.2662  ±0.62%     8775
   · perClipInTS                        2,767.61  0.3416  0.7966  0.3613  0.3554  0.6125  0.6740  0.7954  ±0.62%     1384   slowest
   · recursiveFunction                 20,695.35  0.0433  0.5776  0.0483  0.0459  0.0778  0.2725  0.4199  ±1.02%    10348
   · whileAndIfButSeparate             24,847.09  0.0366  1.9748  0.0402  0.0390  0.0586  0.1832  0.2334  ±1.02%    12424
   · whileAndIfWithConcat              30,877.64  0.0288  0.3930  0.0324  0.0312  0.0518  0.1659  0.2273  ±0.68%    15439
   · whileAndIfWithPlus                31,497.11  0.0289  0.3876  0.0317  0.0310  0.0463  0.1624  0.2088  ±0.65%    15749   fastest
   · whileAndIfWithTemplateString      30,109.89  0.0307  0.4864  0.0332  0.0324  0.0478  0.1629  0.2018  ±0.65%    15056

 BENCH  Summary

  whileAndIfWithPlus - src/counterstring.bench.ts > counterstring 10.000
    1.02x faster than whileAndIfWithConcat
    1.05x faster than whileAndIfWithTemplateString
    1.27x faster than whileAndIfButSeparate
    1.52x faster than recursiveFunction
    1.79x faster than evilTesterCreateListAndReverseIt
    2.78x faster than createListAndReverseIt
    11.17x faster than evilTester
    11.38x faster than perClipInTS
```

## The ranking

If we use these results to rank the implementations from slowest to fastest, we get:

1. `perClipInTS`
1. `evilTester`
1. `createListAndReverseIt`
1. `evilTesterCreateListAndReverseIt`
1. `recursiveFunction`
1. `whileAndIfButSeparate`
1. `whileAndIfWithTemplateString`
1. `whileAndIfWithConcat and whileAndIfWithPlus`


# My reflections on the results

## Don't reverse a string if you don't have to

The four slowest implementations all involve reversing either lists or strings. The slowest ones by far, `perClipInTS` and `evilTester`, reverse strings in two places: when creating the string to add to the intermediate result and right before returning the complete string.

The reason for the slowness is that there isn't an optimized way to reverse a string in TypeScript (or JavaScript). So you end up doing this: `.split("").reverse().join("")`. You split the string into an array, reverse the array, and join the array into a string again. A quick search shows there are plenty of other ways to do this, but the fact there is a discussion at all, with differences in performance across browsers, is enough reason for me to conclude: If you don't have to reverse a string in TypeScript/JavaScript, then don't.

This is demonstrated by the performance of the next two slowest implementations, `createListAndReverseIt` and `evilTesterCreateListAndReverseIt`. The only difference between the latter one and the original `evilTester` one is that it pushes each sub-string directly to a list, then reverses the list, and joins it into a string. Because of that we also no longer have to reverse each sub-string. The result is an implementation that's about six times faster.

## Recursion performs ok until you run out of stack

The recursive implementation is not the fastest, but it doesn't perform horribly. Until you try to run the benchmark creating a counterstring of length 100.000. That is, untill you run out of stack.

Tinybench drops a `'Maximum call stack size exceeded'` and a `'RangeError: Maximum call stack size exceeded\n    at Number.toString (<anonymous>)\n ...'` in the output. Vitest bench omits the table with results, only giving you the comparisons, with the fastest implementation being `NaNx faster than recursiveFunction`.

## Less is more

The four fastest implementations are the `whileAndIf`-variations. The main thing they have in common is that they don't reverse any lists or strings. They still construct the counterstring starting at the end and working backwards. But they do this by prepending each sub-string to the intermediate result.

Of these four, `whileAndIfButSeparate` is the slowest. That makes sense. It prepends the token and the number separately to the intermediate result, so it has to go through the `while`-loop for every token and every number instead of for every combined token and number. Prepending the token and the number together makes the other three `whileAndIf`-variations almost a third faster than `whileAndIfButSeparate`.

The difference between the three fastest implementations is in how the token and the number are concatenated: by a template string, with the `+` operator, or by using `concat()`. Here the results show that template string is slower than the other two, but that there isn't a real difference between the the `+` operator and `concat()`.


# Closing thoughts

I really enjoyed [figuring out these different implementations](link://slug/comparing-counterstring-implementations-in-typescript) and seeing the significant difference in performance between (some of) them.

And I'm quite happy that the most performant version, also scores well on readability:


```TypeScript
export function counterstring(length: number) {
  let counterString = "";

  while (length > 1) {
    const prependThis = length.toString() + "*";
    counterString = prependThis + counterString;
    length -= prependThis.length;
  }

  // At this point length is either 1 (the while-loop prepended 3*) or 0 ( the while-loop prepended 2*).
  // If length is 1, we need to prepend "*" to get the correct counterstring. If it's 0, we're done.
  if (length === 1) {
    counterString = "*" + counterString;
  }

  return counterString;
}
```
