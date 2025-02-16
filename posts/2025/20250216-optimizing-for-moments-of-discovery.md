<!--
.. title: Optimizing for moments of discovery
.. slug: optimizing-for-moments-of-discovery
.. date: 2025-02-16
.. category: quality engineering
.. tags: quality engineering, software development, software testing, agile, elephant carpaccio
.. type: text
.. description: Design later and test earlier for better software.
-->

*This is the third post in a three-part series about my statement "The difference between a test case and a requirement is the moment of discovery."*

Last year I wrote about how [the difference between a requirement and a test case is the moment of discovery](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery). And how that means that we should [be intentional about our exploratory testing](link://slug/being-intentional-about-exploratory-testing). Exploratory testing is just one example of a bigger idea, though: optimizing for moments of discovery.

So what does that mean, optimizing for moments of discovery? Don't those moments just happen? Isn't that what serendipity is all about? I think it's fair to say that you can't make moments of discovery happen. You *can* make them more likely to happen. That you *can* optimize for.

Before I go into two practices to optimize for these moments of discovery, I want to talk more generally about moving the moment of discovery, either earlier or later, for both requirements and test cases, i.e. for design and test. Because the two practices will do exactly that: moving the moment of discovery.

<!-- TEASER_END -->

# Moving the moment of discovery

There is no escaping the order of the activities of design - build - test. You think of how to do something, you do the something, you evaluate the something.

That means that the questions *"Can we design earlier?"* and *"Can we test later?"* are very different questions from *"Can we design later?"* and *"Can we test earlier?"* Designing earlier and testing later just pushes the first thing earlier and the last thing later. That's not very interesting.[^1] What's more interesting is keeping options open longer by doing design later and getting sooner and richer feedback by doing testing earlier.

[^1]: There is value in deciding early what you can decide early and in testing late what you can test late. But that's more about optimizing design and test on their own than it is about optimizing when they happen in the overall process.

## Designing later

Designing later means making decisions later. How late depends on how large the decision is. The smaller the decision, the closer you want to make it to when the actual code is written. Basically you don't want to decide things and thus reduce your options, earlier than you really have to. That does require trust. Trust that you're heading in the right direction. That you're doing good work, even though a lot has not been decided yet. That you'll correctly spot the last responsible moment to make those decisions. Because doing it later than that will not be pleasant.


## Testing earlier

Testing earlier is not the same thing as getting testers involved earlier, as in getting testers involved in writing acceptance criteria. While that is a great idea, that's not testers testing earlier. It's getting testers involved in design. Testing earlier means that you interact with and evaluate what's built, earlier. Instead of waiting until a change gets deployed to the test environment, you check out the code and play around with the unit tests. Or you make the change smaller, so it can be tested earlier.


# Two practices for designing later and testing earlier

Two of my favorite practices that allow you to design later and test earlier are working in thin vertical slices and practicing just-in-time refinement.


## Thin vertical slices

Working in thin vertical slices means [your default](link://slug/your-default-response-should-be-a-safe-one) is to build things across the whole stack you own. So adding a table to a database, or expanding an API, or building a new UI element, are not a single thing you do. They're part of a slice of work that goes across the whole stack. Put simply: a vertical slice is something that provides value to whoever your users are. What such a slice will be exactly, depends on your context. Or to be more specific, on your organization and on your architecture. (Not that those are [completely separate things](https://thinkinglabs.io/talks/2022/08/26/shades-of-conways-law.html).)

Next to making your slices of work vertical, you want to make them as thin (small) as possible. You're going to deliver something of value, and the sooner the better. And the only sustainable way to do that, is not to cut corners, or to do overtime, but to reduce scope. Build the smallest thing possible that delivers some value. And if you want an example of how far you can take that, see the ["Elephant Carpaccio"-exercise](link://slug/how-to-run-a-remote-elephant-carpaccio).

Thin vertical slices let you design later. You do want a high-level design, have a direction you're moving in. But the lower-level design, you only need that for the next vertical slice. Or as Dan North puts it: you want the ["Best Simple System for Now"](https://dannorth.net/best-simple-system-for-now/).

Thin vertical slices let you test earlier in two ways. The first way, the more obvious one, is in the "thin". If what you build is smaller, you get to test it earlier. The second way, is in the "vertical". If you build something across your whole stack, something that's supposed to deliver value to your users, you get to evaluate it in a richer context. *"Did I add the right table to the database?"* is a much narrower question than *"Do my users now have this extra capability?"* Instead of only testing part of a solution, you get to test the solution as a whole.


## Just-in-time refinement

Just-in-time refinement means that you specify work at the last responsible moment. The specificity and the moment go hand-in-hand here. High-level specification might happen months in advance. It's just a list of high-level work, often called "epics". Since you're describing them so far in advance, things might change. You might want to do them differently or not at all. So it doesn't make sense to specify them in any further detail or break them up in smaller work items. As you get closer to doing the work, you fill in more and more of the details.

Just-in-time refinement lets you design later, because that's exactly what you do. Postpone design to the latest moment where it doesn't hurt your ability to deliver. What that last responsible moment is, depends on your context, but I suspect in most cases it's later than you think.

Just-in-time refinement lets you test earlier. It makes design into an incremental process that almost unnoticeable morphs into building. (As in: the only sufficiently detailed specification of software is code.) So instead of writing some code according to some spec defined weeks ago, you're encouraged to remain mentally engaged with what you're building and how it should be designed. And with design and test being two sides of the same coin - only [distinguished by the moment of discovery](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery) - building morphs into testing as designing morphs into building. You're testing earlier, because design - build - test are no longer three separate sequential steps of delivering software.

---

What do you do to optimize for moments of discovery? What risks and challenges do you see with these two practices? Are there contexts where you would not want to optimize for moments of discovery?
