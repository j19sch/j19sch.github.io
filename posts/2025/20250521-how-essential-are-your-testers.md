<!--
.. title: How essential are your testers?
.. slug: how-essential-are-your-testers
.. date: 2025-05-21
.. category: quality engineering
.. tags: career, management, quality engineering, software testing, teaching, test management
.. type: text
.. description: It's probably a bit of a Schrödinger-like situation...
-->

A question I don't seem to be able to let go of is: where does a tester fit into a software development team? More specifically, how essential are testers to the team?

I think that there are basically three options:

1. Your testers do not add something essential.
2. It's not clear if your testers add something essential.
3. Your testers do add something essential.


# Your testers do not add something essential {.small}

I suspect this is becoming more and more common. Thanks to Agile, CI/CD, DevOps, improved tooling and changing expectations, you should not have testers that find the dumb bugs I was expected to find at the start of my career. If a programmer wrote a `>` where it should have been a `>=`, we should expect a unit test and not a tester to catch it.

<!-- TEASER_END -->

However, as William Gibson said: *"The future is already here - it's just not very evenly distributed."*[^1] If you do find that you need to employ testers to verify requirements, I'm sorry to say, but you have a quality problem. [You don't need more testers or better testing](https://curiousduck.io/assets/pdfs/btwq.pdf). You need your programmers to engage with what they build in more varied and rich ways.

[^1]: [https://quoteinvestigator.com/2012/01/24/future-has-arrived/](https://quoteinvestigator.com/2012/01/24/future-has-arrived/)


There's a different aspect to this, though. A lot of testers have never learned to do better than this, than what's expected of them in these kinds of environments. These testers do not do anything that a (junior) programmer, a product owner, a business analyst, or a UX designer couldn't do equally well. They are supposed to be a testing expert, but have no actual testing expertise to distinguish themselves with from those other roles.

And the sad thing - and an important point of this post - is that we can't blame these testers. Where should they have learned these testing skills? And for what reason, if there's no expectation to have them? And this sadness extends to the programmers. They too are stuck in an environment that will never expect them to develop into a well-rounded professional.


# It's not clear if your testers add something essential {.small}
I suspect that this is the most common position of good testers: *"We don't know exactly what they do, but we do know we don't want them to stop doing it."* A lot of organizations are not set up to support good testing, so good testers do their best with what they have. They shape their role. They try to [shape their organization in addition to doing their job](link://slug/a-good-tester-is-all-over-the-place#doing-your-job-vs-improving-the-system). And they shape themselves to fill whatever quality gaps they find.

Which raises the question: what is a good tester?

In short: they explore changes in the domain, in the code (production and test), and in the environment (infra, libraries, etc.). They do so in order to evaluate the software. They use a diverse set of tools. They are able to share what they find both as information and as code.

However, since the organization doesn't truly understand testing, they have trouble clearly seeing the value these testers bring. They can't tell if all of the testers bring this value, or only some of them do. So the question how essential these testers are, becomes rather moot. As does the question how the organization could get so much more value from their testers, if these testers didn't have to spend as much time shaping their role and their organization.


# Your testers do add something essential {.small}
Awesome! Take a moment to appreciate it. And please share your story. :-)

---

# Which of those three is you? {.small}
So if you're not sure which of these three situation you are in, how can you tell?

The simplest heuristic is to look at what happens when a tester goes on vacation for a few weeks.

If work starts piling up in the "to test"-column, that's not a good sign.  
If everything proceeds exactly as normal, that's not a good sign.  
If you prefer not to think too hard about it, that's not a good sign.
