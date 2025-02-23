<!--
.. title: Benchmarking counterstring implementations in TypeScript
.. slug: benchmarking-counterstring-implementations-in-typescript
.. date: 2025-02-23
.. category: programming & test automation
.. tags: counterstring, programming
.. type: text
.. description:
-->

TODO:
- add links to the other two posts pointing to this one

Earlier this year I posted about how I implemented a counterstring function using "fake it till you make it". I also posted about different ways to implement counterstrings. In this post, I want to share how those different implementations compare performance-wise.

To do this, I used both [tinybench](https://github.com/tinylibs/tinybench) and [vitest bench](https://vitest.dev/guide/features.html#benchmarking) (which uses tinybench). The results are basically the same, but their default output is slightly different.

Before I present the results, I should describe the different implementations and how they differ from each other.


<!-- TEASER_END -->

# The nine implementations {.small}

The [actual code of each implementation](https://github.com/j19sch/counterstring/blob/04883b7bb2f3e99f7be81ffa58e4ac5f934d276b/src/alt-counterstrings.ts) is available on GitHub. In this post I'll only mention what makes each implementation interesting:

- `createListAndReverseIt`: creates the counterstring as a list starting at the end of the string with the token and the numbers as separate elements, then reverses the list and turns it into a string
- `evilTester`: creates the counterstring as a string, but backwards, adding token and number in the same operation, then reverses the whole string, copied from [EvilTester's blog post](https://www.eviltester.com/blog/eviltester/chrome-extensions/2019-02-19-counterstring-snippets/#counterstring-generation-function) about his counterstring Chrome extension
- `evilTesterCreateListAndReverseIt`: creates the counterstring as a list, starting at the end, adding token and number in the same opereation, then reverses the list and turns it into a string
- `perClipInTS`: essentially the same as `evilTester`, translated from [the original Perl](https://www.satisfice.com/download/perlclip) to TypeScript by me
- `recursiveFunction`: completely different from all other implementation, because recursion, runs out of stack for long counterstrings
- `whileAndIfButSeparate`: prepends to a string instead of having to reverse a list, but adds token and number separately
- `whileAndIfWithPlus`: prepends to a string, adding token and number in the same operation, uses `+` for string concatenation
- `whileAndIfWithConcat`: prepends to a string, adding token and number in the same operation, uses `concat()` for string concatenation
- `whileAndIfWithTemplateString`: prepends to a string, adding token and number in the same operation, uses template strings for string concatenation


# The results {.small}

```
counterstring length 10.000
┌─────────┬────────────────────────────────────┬──────────────────┬────────────────────┬────────────────────────┬────────────────────────┬─────────┐
│ (index) │ Task name                          │ Latency avg (ns) │ Latency med (ns)   │ Throughput avg (ops/s) │ Throughput med (ops/s) │ Samples │
├─────────┼────────────────────────────────────┼──────────────────┼────────────────────┼────────────────────────┼────────────────────────┼─────────┤
│ 0       │ 'createListAndReverseIt'           │ '91218 ± 1.40%'  │ '87906 ± 1496.00'  │ '11186 ± 0.54%'        │ '11376 ± 194'          │ 1097    │
│ 1       │ 'evilTester'                       │ '353526 ± 1.35%' │ '342284 ± 3029.00' │ '2853 ± 0.90%'         │ '2922 ± 26'            │ 283     │
│ 2       │ 'evilTesterCreateListAndReverseIt' │ '58369 ± 1.59%'  │ '56225 ± 1104.50'  │ '17577 ± 0.39%'        │ '17786 ± 349'          │ 1714    │
│ 3       │ 'perClipInTS'                      │ '374922 ± 1.97%' │ '356913 ± 3836.00' │ '2710 ± 1.18%'         │ '2802 ± 30'            │ 267     │
│ 4       │ 'recursive'                        │ '49254 ± 1.46%'  │ '44673 ± 1033.00'  │ '21210 ± 0.66%'        │ '22385 ± 525'          │ 2031    │
│ 5       │ 'whileAndIfButSeparate'            │ '37028 ± 1.59%'  │ '35370 ± 687.00'   │ '27888 ± 0.33%'        │ '28273 ± 548'          │ 2701    │
│ 6       │ 'whileAndIfWithConcat'             │ '27399 ± 1.17%'  │ '26329 ± 725.00'   │ '37465 ± 0.27%'        │ '37980 ± 1055'         │ 3650    │
│ 7       │ 'whileAndIfWithTemplateString'     │ '28903 ± 1.23%'  │ '27701 ± 326.00'   │ '35552 ± 0.28%'        │ '36100 ± 427'          │ 3464    │
│ 8       │ 'whileAndIfWithPlus'               │ '27434 ± 1.66%'  │ '26163 ± 642.50'   │ '37776 ± 0.28%'        │ '38222 ± 947'          │ 3646    │
└─────────┴────────────────────────────────────┴──────────────────┴────────────────────┴────────────────────────┴────────────────────────┴─────────┘
```

```
┌─────────┬────────────────────────────────────┬──────────────────┬────────────────────┬────────────────────────┬────────────────────────┬─────────┐
│ (index) │ Task name                          │ Latency avg (ns) │ Latency med (ns)   │ Throughput avg (ops/s) │ Throughput med (ops/s) │ Samples │
├─────────┼────────────────────────────────────┼──────────────────┼────────────────────┼────────────────────────┼────────────────────────┼─────────┤
│ 0       │ 'createListAndReverseIt'           │ '90821 ± 1.34%'  │ '87773 ± 1365.50'  │ '11223 ± 0.52%'        │ '11393 ± 178'          │ 1102    │
│ 1       │ 'evilTester'                       │ '354971 ± 1.42%' │ '345634 ± 2522.00' │ '2844 ± 0.90%'         │ '2893 ± 21'            │ 282     │
│ 2       │ 'evilTesterCreateListAndReverseIt' │ '58630 ± 1.63%'  │ '56269 ± 1117.00'  │ '17527 ± 0.41%'        │ '17772 ± 352'          │ 1706    │
│ 3       │ 'perClipInTS'                      │ '368610 ± 1.99%' │ '356006 ± 3031.50' │ '2751 ± 1.04%'         │ '2809 ± 24'            │ 272     │
│ 4       │ 'recursive'                        │ '46438 ± 1.99%'  │ '44419 ± 773.00'   │ '22288 ± 0.36%'        │ '22513 ± 391'          │ 2154    │
│ 5       │ 'whileAndIfButSeparate'            │ '36642 ± 1.37%'  │ '35335 ± 653.50'   │ '28037 ± 0.30%'        │ '28301 ± 523'          │ 2730    │
│ 6       │ 'whileAndIfWithConcat'             │ '27512 ± 1.49%'  │ '26121 ± 552.00'   │ '37679 ± 0.31%'        │ '38283 ± 810'          │ 3635    │
│ 7       │ 'whileAndIfWithTemplateString'     │ '31571 ± 1.90%'  │ '27996 ± 487.00'   │ '33756 ± 0.54%'        │ '35720 ± 626'          │ 3168    │
│ 8       │ 'whileAndIfWithPlus'               │ '27376 ± 1.63%'  │ '26058 ± 564.00'   │ '37910 ± 0.28%'        │ '38376 ± 834'          │ 3653    │
└─────────┴────────────────────────────────────┴──────────────────┴────────────────────┴────────────────────────┴────────────────────────┴─────────┘
```



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

# My thoughts on the results {.small}
