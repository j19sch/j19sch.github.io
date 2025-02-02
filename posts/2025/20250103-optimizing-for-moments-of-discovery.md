<!--
.. title: Optimizing for moments of discovery
.. slug: optimizing-for-moments-of-discovery
.. date: 2025-01-03
.. category: 
.. tags: 
.. type: text
.. description: 
-->

ToDo:
- add link in difference etc post to this one
- add link in being intentional etc post to this one
- separate post about "designing and building and testing are all the same thing"?
	- and lingering beliefs about waterfall
	- also links to thin vertical slices and Zuills' maxim

Last year I wrote about how [the difference between a requirement and a test case is the moment of discovery](link://slug/the-difference-between-a-test-case-and-a-requirement-is-the-moment-of-discovery). And how that means that [we should be intentational about our exploratory testing](link://slug/being-intentional-about-exploratory-testing). Exploratory testing is just one example of a bigger idea, however: optimizing for moments of discovery.

So what does that mean, optimizing for moments of discovery? Don't those moments just happen? Isn't that what serendipity is all about? I think it's fair to say that you can't make moments of disovery happen. You *can* make them more likely to happen. That you *can* optimize.


# Four things to optimize

There are four aspects to this optimization:
1. the activity - what
2. the moment - when
3. the skill - how (well)
4. the recording - ???

I'd like to illustrate these by returning to the idea that started these series of posts: the requirement and the test case.  Later in this post I'll provide some more examples of things you can do to optimize for the moment of discovery.

The questions are phrased oddly, because it's easier to discuss discoveries in hindsight, because as mentioned, you can't make discoveries happen, only make them more likely to happen.


## The activity

For optimizing the activity, we can ask the question: should this be a test case or a requirement? Is this something we should figure out during design, before we have built anything? Or should we figure this out by interacting with and exploring something we have built - even if we've only built something very small?

Because it does make sense to figure out some things in advance. And it's good to test and verify those things. But you can't start building from a completely blank slate. You'll have to make some decisions. Then there are things you can't figure out in advance.vAnd finally, there are things that maybe you can figure out in advance, but it's so much easier/cheaper/better to see what happens when you get there, then to figure them out in advance.

So basically, choose wisely what you want to figure out in design and what you want to figure out in test. When that design-build-test loop is five minutes, don't worry too much about it. When that loop is five weeks, however, or five years...


## The moment

There is no escaping the order of the activities of design - build - test. You think of doing something, you do the something, you evaluate the something.[^1] That means that the questions "can we design earlier?" en "can we test later?" are very different questions from "can we design later?" and "can we test earlier?"

[^1]: Even TDD does not escape this order. You write a test, you run the test. You run the code, you run the test. You refactor the code, you run the test. It does a great job of intermingling designing, building, and testing. But the order is still: idea - build - evaluate.

Designing earlier and testing later go together very well. It's traditional waterfall with the belief it is possible to first write down all (most) of the requirements. So at the end you just have to check of what was built, meets those requirements. It's also the pattern of getting someone else to develop some piece of software for you. Budgets need to be allocated. Contracts need to be written. Writing down what you want upfront does make that part of the process easier - even if you don't end up with the software you actually need.

There's also an interesting aspect to designing earlier and testing later, however. Why not design earlier? Especially if that means you can build and test earlier? Get that "walking skeleton" going. Get that first version out there. And why not test later? Why invest time and energy right now, if it's not something we need to know yet? The value of a test is in what happens after the test. Does it inform a decision? A new test? Or doesn't it do anything, and was it wasted effort?[^2]

[^2]: That's not always an easy distinction to make. A very small and cheap test doesn't have to do much to have value, so it might be hard to notice.

Designing later is a great approach, but it does require trust. Trust that you're heading in the right direction, doing good work, even though a lot has not been decided yet. Trust that you'll be able to spot the last responsible moment and decide no later than that moment. It is really powerful, though. Why reduce your options in the future by deciding things, fix(ating) things earlier than you need to?

Testing earlier is not the same thing as getting testers involved earlier. For example, getting testers involved in writing acceptance criteria. While that is a great idea, that's not testers testing earlier. It's getting testers involved in design. Testing earlier means that you interact with and evaluate what's built, earlier. Instead of waiting until a change gets deployed to the test environment, you check out the code and play around with the unit tests.


## The skill

Skill is crucial, which is why I wrote a post last year about [the nine skills of exploratory testing](link://slug/the-nine-skills-of-exploratory-testing).

Designing is also a skill, with some overlap with, but also plenty distinct from exploratory testing. Since design is not my area of expertise, I'l give one example. My current team is writing use cases following the methodology described by Alistair Cockburn in his excellent book "Writing Effective Use Cases" (2000). Writing good use cases definitely is a skill and that's even without considering the part where you get people to share the information that needs to go into the use cases.


## The recording / What remains / What you leave behind

Discovering something is great, but then what? What do you do with this information? How do you capture it? How do you share it? Documentation often is where information goes to die. Documentation needs to be a tool, something that's being used. Not just some files stored in a place where no one really looks anymore.

One thing that designs and tests have in common is that the best kind is the executable kind. Not that all design and all tests need to be executable. But as far as documentation goes: the less it's a document that's created and updated and maintained as something separate from the code, the better.





---


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
