<!--
.. title: Tackling test automation in a new language
.. slug: tackling-test-automation-in-a-new-language
.. date: 2024-02-11
.. category: programming & test automation
.. tags: agile, programming, test automation, communication
.. type: text
-->


While there's value in learning all the ins-and-outs of one particular language, its ecosystem and its testing libraries, I think there's also a lot of value in having experience in several. Or at least, in two. If you only know one, you don't really know what's essential and what's incidental to the one set of tools you know. You don't know from experience in what ways things could be different.

Picking up a new language is not trivial though, especially if it's your second one. There will be a lot to learn. You will notice similarities between the new language and the one(s) you already know. Sometimes those similarities will help you, sometimes they will mislead you.

Also, it's more than picking up a new language. There are also the testing libraries you will use
and the language's ecosystem (e.g. how to install those libraries[^1] or how to set up a pre-commit hook with a linter). That's quite a package.

[^1]: Looking at you, npm, yarn, and pnpm!

<!-- TEASER_END -->

As someone who has [used a few languages](https://smallsheds.garden/blog/2023/a-lesson-from-every-language-ive-used/) already and is now learning Playwright in TypeScript, here's my advice for tackling test automation in a new language:

- start with a test, not with the framework
- let code complexity keep pace with your skill level
- compare and contrast with what you already know


# Start with a test, not with the framework {.small}
The easiest way to fail with test automation is to spend three months building a framework and building zero tests. Or perhaps one test to show off the framework.That's a lot of code with little immediate value. That's why an important metric to me is: “How many (reliable) tests do you have on your main branch?” Not that more is always better, but initially you do want to see that number creep upwards, slowly but surely.

So start with a single test. In a single file. Don't worry about page objects or API clients. Don't worry about doing something data-driven. Forget about separation of concerns for now. Just build a single running test.

Then add another test. And another one. By now - or at least by the time you hit five tests - it will be obvious where you will need to refactor to make sure your code is maintainable. Where your code needs some design attention. And where it doesn't need it - yet.

Once you've taken care of the most important improvements, add some more tests. Let the framework grow organically with your tests. They should evolve hand-in-hand, not one before the other. In this sense, test automation is no different from any other software development.


# Let code complexity grow with your skill level {.small}
As you're building this test automation in a new language, in the beginning your skill in that language will be low. You might not yet know for instance how to iterate through a list or array. Or you might not yet know what you can and can't do within a class constructor. That's ok.

This is another place where the previous tip of evolving the framework in parallel with the tests shows its value. At the start, when you know the least about the language, you also have the least code. You have some tests and a very minimal framework. You might see possible design optimizations, but don't know yet how you could implement them. Since you still have a small codebase, you can let most of those be. Take it step-by-step. Pick the most important ones. Learn what you need to tackle those, leaving the rest for another day.


# Compare and contrast with what you already know {.small}
Building test automation in a new language, is a great journey of discovery. In some ways this new language will be different from the one you know. In others it will be the same. Seeing similarities between two languages can be helpful or it can be a trap, as [Felienne Hermans](https://www.felienne.com/) describes in her book ["The Programmer's Brain"](https://www.manning.com/books/the-programmers-brain).

The academic term for seeing such similarities is "transfer". Positive transfer is when you think there's a similarity and there actually is one. In such cases, transfer is helpful. Unfortunately, there's also negative transfer: seeing a similarity when there isn't one. For example, in both Python and TypeScript you can for item in list. They don't do the same thing, though. Python will iterate through the items in the list, TypeScript through the indices of the list.

So be on the lookout for where your knowledge of another language (or languages) can help you in learning the new one. But don't accept similarities at face value. See them as an opportunity to dive a bit deeper into the new language and explore how deep the similarities go.

# Increment, iterate, and learn {.small}

These three pieces of advice can be summarized as increment, iterate, and learn:

- increment: let the tests and the framework evolve hand-in-hand
- iterate: let code complexity grow with your skill level
- learn: compare and contrast with what you already know

That sounds a lot like Agile software development and I don't think that's a coincidence.
