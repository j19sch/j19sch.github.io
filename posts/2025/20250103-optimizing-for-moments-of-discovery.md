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
- add link to difference etc post
- add link to being intentional etc post
- separate post about "designing and building and testing are all the same thing"?
	- and lingering beliefs about waterfall
	- also links to thin vertical slices and Zuills' maxim

Last year I wrote about how the difference between a requirement and a test case is the moment of discovery. And how that means that we should be intentational about our exploratory testing. In this post I want to make a similar point, but on a larger scale: you should optimize for moments of discovery.

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


Three ways of doing this (in addition to exploratory testing):
- thin vertical slices
	- elephant carpaccio
	- requires understanding of what's built so far
	- richness of evaluation context
	- > "It is in the doing of the work that we discover the work that we must do. Doing exposes reality." Woody Zuill, https://agilemaxims.com/
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
