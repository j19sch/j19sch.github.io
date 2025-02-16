<!--
.. title: Optimizing for moments of discovery
.. slug: optimizing-for-moments-of-discovery
.. date: 2025-02-16
.. category: quality engineering
.. tags: quality engineering, software development, software testing, agile, elephant carpaccio
.. type: text
.. description: Design later and test earlier for better software.
-->

ToDo:
- add link in difference etc post to this one
- add link in being intentional etc post to this one
- separate post about "designing and building and testing are all the same thing"?
	- and lingering beliefs about waterfall
	- also links to thin vertical slices and Zuills' maxim
	- and all the other notes


Last year I wrote about how [the difference between a requirement and a test case is the moment of discovery](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery). And how that means that we should [be intentional about our exploratory testing](link://slug/being-intentional-about-exploratory-testing). Exploratory testing is just one example of a bigger idea, though: optimizing for moments of discovery.

So what does that mean, optimizing for moments of discovery? Don't those moments just happen? Isn't that what serendipity is all about? I think it's fair to say that you can't make moments of discovery happen. You *can* make them more likely to happen. That you *can* optimize for.

Before I go into two practices to optimize for these moments of discovery, I want to talk more generally about moving the moment of discovery, either earlier or later, for both requirements and test cases, i.e. for design and test. Because the two practices will do exactly that: moving the moment of discovery.

<!-- TEASER_END -->

# Moving the moment of discovery

There is no escaping the order of the activities of design - build - test. You think of how to do something, you do the something, you evaluate the something.[^2]

[^2]: Even TDD does not escape this order. First, you write a test and you run the test. Then you write the code and you run the test. Finally, you refactor the code and you run the test. It does a great job of intermingling designing, building, and testing at each step. But overall you still move from design to build to test.

That means that the questions *"Can we design earlier?"* and *"Can we test later?"* are very different questions from *"Can we design later?"* and *"Can we test earlier?"* Designing earlier and testing later just pushes the first thing earlier and the last thing later. That's not very interesting.[^1] What's more interesting is keeping options open longer by designing later and getting sooner and richer feedback by testing earlier.

[^1]: There is value in deciding early what you can decide early and in testing late what you can test late. But that's more about optimizing design and test on their own than it is about optimizing when they happen in the overall process.

## Designing later

Designing later means making decisions later. How late depends on how large the decision is. The smaller the decision, the closer you want to make it to when the actual code is written. Basically you don't want to decide things and thus reduce your options earlier than you really have to. That does require trust. Trust that you're heading in the right direction. That you're doing good work, even though a lot has not been decided yet. That you'll correctly spot the last responsible moment to make those decisions. Because designing too late tends to lead to some unpleasant surprises.


## Testing earlier

Testing earlier is not the same thing as getting testers involved earlier, like getting testers involved in writing acceptance criteria. While that is a great idea, that's not testers testing earlier. It's getting testers involved in design. Testing earlier means that you interact with and evaluate what's built, earlier. Instead of waiting until a change gets deployed to the test environment, you check out the code and play around with the unit tests. Or you make the change smaller, so you can test it earlier.


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

Just-in-time refinement lets you test earlier. It makes design into an incremental process that almost unnoticeable morphs into building. (As in: the only sufficiently detailed specification of software is code.) So instead of writing some code according to some spec defined weeks ago, you're encouraged to remain mentally engaged with what you're building and how it should be designed. And with design and test being two sides of the same coin - only [distinguished by the moment of discovery](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery) - build morphs as easily into test as design morphed into build. You're testing earlier, because design - build - test are no longer three sequential phases of delivering software.

---

What do you do to optimize for moments of discovery? What risks and challenges do you see with these two practices? Are there contexts where you would not want to optimize for moments of discovery?


---



## Early feedback and end-to-end feedback (Abacus)

- Vroege feedback:
    - Feedback op waar je op dat moment mee bezig bent is beter dan feedback op wat je vorige week aan het doen was
    - Dus ontwikkelen in dunne "slices" (zo klein mogelijke scope)
- End-to-end feedback:
    - Feedback op een feature is rijker dan feedback op een component
    - Dus ontwikkelen in verticale "slices" (feature over componenten heen), niet in horizontale "slices" (feature component per component bouwen)
- Gefaciliteerd door:
    - Iteratief en incrementeel ontwikkelen
    - CI/CD (zie "Kwaliteits- en testprogramma")


## Refinement (Abacus)

We doen "Just-In-Time Refinement", dus refinement op het "last responsible moment". Dit doen we om te voorkomen dat we tijd en energie steken in refinement, maar dat het resultaat ervan later herzien moet worden, of zelfs helemaal niet nodig blijkt te zijn.

epics en issues, soms spikes (spike solutions)



# A good habit: inviting serendipity in



mix things up for serendipity
refer back to intro: can you make more moments of discovery happen?




Optimize as in:
- right activity of discovery
- right moment of discovery
- right discovery / right contents of discovery
	- is that how discovery works?
	- skillful discovery? -> ET skills
- right documentation of discovery
	- Maaret: your input should be output eg issues
	- recording of discovery, often: code
	- use cases -> Alistair Cockburn's book
	- making it concrete
	- solidifying?
	- capturing, but not the moment, the discovery


Three ways of doing this (in addition to exploratory testing):
- thin vertical slices
	- elephant carpaccio
	- requires understanding of what's built so far
	- richness of evaluation context
	- > "It is in the doing of the work that we discover the work that we must do. Doing exposes reality." Woody Zuill, https://agilemaxims.com/
	- doing: design - build - test (feedback!) TDD mixes then so well
- just in time refinement
	- instead of deciding/fixating early
	- instead of front-loading all the thinking
	- documentation as output
- do things a little differently / small variations in how you do things
	- add a little chaos, serendipity, confusion (cynefin)


# toot Maaret
https://mas.to/@maaretp/113882037108302547

People have ideas about what agile is. When we worked with 'agile', we made notes of ideas that were essentially different to what others were expecting agile to mean as *process*.

- No product owner - product owned by team, with shared ownership
- Nothing changes if we change nothing - bias to moving forward to better over extensive planning
- On-time planning - plan details just before plan is executed, but plan for themes continuously
- Collaborating with others over individual productivity
- Documentation as output - writing documentation at time we know the most, as things we leave behind for our future selves
- Socialize over documenting for process - share way of working by working this way together, including all team members; follow behaviors expected over following rules.
- Value over compliance. There is always reasons on why we have compliance rules in place. Go back to discussing the value we seek a compliance activity to create.
- Proposed requirements become requirements at time of 1st release of them. They are a result of negotiation under constraints of design.

# quote Nate
"Which is while we like to imagine processes as linear and flowing from one point to another, our experience as testers is often more fractal and recursive - where one thing causes us to go back and refine something done before etc." - Nate Custer, https://www.linkedin.com/feed/update/urn:li:activity:7165642850334945281?commentUrn=urn%3Ali%3Acomment%3A%28activity%3A7165642850334945281%2C7165654356732723201%29&replyUrn=urn%3Ali%3Acomment%3A%28activity%3A7165642850334945281%2C7165706317192515584%29&dashCommentUrn=urn%3Ali%3Afsd_comment%3A%287165654356732723201%2Curn%3Ali%3Aactivity%3A7165642850334945281%29&dashReplyUrn=urn%3Ali%3Afsd_comment%3A%287165706317192515584%2Curn%3Ali%3Aactivity%3A7165642850334945281%29

# from previous posts

TODO: read first post in series

> A requirement is an answer, a “should”. It serves the purpose of design. A test case is a question, a “what if?”. It serves the purpose of evaluation.

> The value of distinguishing test cases from requirements by their moment of discovery, lies in making us aware of that moment - and where that moment fits in our processes. It lets us notice, when we discover something we expect of our software, if we discover it either as a requirement or as a test case, as part of design or as part of testing.

> And once we notice this moment, this distinction, we can reflect on it. We have a new angle to explore how we might get better at either type of discovery. We can decide if we want to move that moment of discovery, either earlier or later. And it lets us ask the question: should some discoveries be moved to other side of that moment?


# workflowy

difference is moment of discovery so optimize for them
thin vertical slices
just in time refinement
seek feedback
do things differently
add a little chaos, serendipity, confusion (cynefin)
exploratory testing
use cases?


"Which is while we like to imagine processes as linear and flowing from one point to another, our experience as testers is often more fractal and recursive - where one thing causes us to go back and refine something done before etc." - Nate Custer, https://www.linkedin.com/posts/joepschuurkes_the-difference-between-a-test-case-and-a-activity-7165642850334945281-r5Di?utm_source=share&utm_medium=member_android




# key thoughts

The dividing line between what's a test case and a requirement is the question: is this input for creation or for evaluation? If it's for creation, it's a requirement; if it's for evaluation, it's a test case.

Now you could argue, that it's possible to use test cases as input for creation. Of course, you can, but then they are requirements. The difference is not in how you title them, what template you use, the format you write them in. That's incidental, not the essense, superficial. The difference is what you do with them. -> answers and questions

## thin vertical slices
- constant revisiting of what's been done
	- challenging!
	- thin vertical slices, JIT design and test
	- thin vertical slices FTW -> serves both, JIT design and test
	- elephant carpaccio
	- thin vertical slices for richer exploration, for JIT design and test

> "It is in the doing of the work that we discover the work that we must do. Doing exposes reality."
Woody Zuill, https://agilemaxims.com/

As we do and think, we learn things. And ideally, we capture what we learn in the most approriate way.



## continuous exploratory testing and requirement engineering, both serve their purpose
- If I could tell you in detail what and how I would test upfront, I'd add those as requirements / acceptance criteria from the start. Then you could build it right/correct from the start, instead of having me test it afterwards. // if I can tell you what to test without exploring, it could have been a requirement
- can we ET sooner? not just shifting left
	- Now you could argue, that requirements need validation too. You might think your requirement is a good one, but that doesn't mean it actually is. While that's true, and important and needed, in the end it's working software, something interactive, in its real-life context, that needs to be evaluated if it's good enough. Imagination can take you far, mock ups further, but in the end we need the software.
- feedback loop between require-ing and testing -> prototypes and stuff
- The distinction between the moment of discovery, is: did we discover this requirement through testing or through design?
Where we don't want to discover the requirements through testing, that we could have discovered through design. That's something for the next part.
- there is more value in discovering test cases that are not requirements yet as early as possible
=> hence ET, product as external imagination, hence thin vertical slices for richer exploration
law of diminishing returns

just enough design, just enough testing
good enough for now, safe enough to try
architecture is decisions that are hard to change

testing as feedback on requirements and double-loop learning

both are about learning

sometimes you want to do almost only testing (quick mvp), sometimes almost only requirements (safety critical)

there is no single dividing line, it's a spectrum

## moving the moment of discovery
- obvious: earlier
- interesting: later


## designing and building and testing are all the same thing
In a sense, requirements are dead. Requirements are answers (even if tenuous). Test cases are questions. The trick is to limit test cases to only those questions that can be answered by exploring / interacting with the code / the application. The rest can be a requirement.

If you can come up with a test case for something before it's been built, then why are not involved in defining the requirements? Why are we separating design from test?[^2] Why are they done by separate people, in separate "phases", in different formats? Using different skills and techniques, or at least with differently named skills and techniques?

[^2]: And from build? See the closing thought of this post.

Requirements part of the design. Because I love the same word meaning different things in different contexts: "If it's your decision to make, it's design. If it's not, it's a requirement." - Alistair Cockburn.

where does design end and build start? cargo build?

Arguably, exploratory testing is not only about discovering additional requirements. It's also about discovering in which way(s) the application inadvertently does not meet some explicit or implicit (because 'obvious') requirement. That leads to some interesting questions about where "design" ends and "build" starts. Is writing code the part where we build the software? Or is it creating the final and most-detailed design? It also leads to interesting quetsions about the relation between "design" and "build" on the one hand, and "test" on the other. Do we first design and build, and then test? Or are they interrelated and intertwined?


## residual beliefs in waterfall

To me this shows the problematic position of requirements. In many small ways we still seem to think it's possible that if you just write down what you want the software to do, it can be built, and then tested to see if it meets the requirements. That in essence, it's a mechanical, linear, algorithmical process. And sure we agree requirements can never be complete and unambiguous and ... but that's nuance to this belief at the core of it all: it is possible to sufficiently define a piece of software through requirements.
! lingering old beliefs!



is it about power? who gets to decide what to build? -> https://chaos.social/@joeposaurus/113763875272265624
see lightning talk by Elizabeth as well, and facilitating architecture

---

# Notes from earlier

### (old) optimizing the moment

- thin vertical slices FTW -> serves both, JIT design and test
- what about req eng later?
- should have been requirement or test
- should have been sooner or later
- ET early because for some stuff it's more effective than req eng
- continuous ET and req eng, instead of all design upfront, ET at the end



---

# Four things to optimize

There are four aspects to this optimization:
1. the activity - what
2. the moment - when
3. the skill - how (well)
4. the recording - ???

I'd like to illustrate these by returning to the idea that started these series of posts: the requirement and the test case.  Later in this post I'll provide some more examples of things you can do to optimize for the moment of discovery.

The questions are phrased oddly, because it's easier to discuss discoveries in hindsight, because as mentioned, you can't make discoveries happen, only make them more likely to happen.


## The activity -> not super interesting

For optimizing the activity, we can ask the question: should this be a test case or a requirement? Is this something we should figure out during design, before we have built anything? (Or rather: before we perform a building activity. Design is fractal.) Or should we figure this out by interacting with and exploring something we have built - even if we've only built something very small?

Because it does make sense to figure out some things in advance. And it's good to test and verify those things. But you can't start building from a completely blank slate. You'll have to make some decisions. Then there are things you can't figure out in advance. And finally, there are things that maybe you can figure out in advance, but it's so much easier/cheaper/better to see what happens when you get there, then to figure them out in advance.

So basically, choose wisely what you want to figure out in design and what you want to figure out in test. When that design-build-test loop is five minutes, don't worry too much about it. When that loop is five weeks, however, or five years...


## The moment

see above

## The skill -> not super interesting

Skill is crucial, which is why I wrote a post last year about [the nine skills of exploratory testing](link://slug/the-nine-skills-of-exploratory-testing).

Designing is also a skill, with some overlap with, but also plenty distinct from exploratory testing. Since design is not my area of expertise, I'l give one example. My current team is writing use cases following the methodology described by Alistair Cockburn in his excellent book "Writing Effective Use Cases" (2000). Writing good use cases definitely is a skill and that's even without considering the part where you get people to share the information that needs to go into the use cases.


## The recording / What remains / What you leave behind -> not super interesting

Discovering something is great, but then what? What do you do with this information? How do you capture it? How do you share it? Documentation often is where information goes to die. Documentation needs to be a tool, something that's being used. Not just some files stored in a place where no one really looks anymore.

One thing that designs and tests have in common is that the best kind is the executable kind. Not that all design and all tests need to be executable. But as far as documentation goes: the less it's a document that's created and updated and maintained as something separate from the code, the better.
