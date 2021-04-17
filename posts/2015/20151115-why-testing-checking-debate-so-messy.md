<!--
.. title: Why the testing/checking debate is so messy - a fruit salad analogy
.. slug: why-the-testingchecking-debate-is-so-messy-a-fruit-salad-analogy
.. date: 2015-11-15 12:17:12 UTC+01:00
.. tags: semantics, context-driven testing, testing and checking
.. category: philosophy of testing
.. link: 
.. description:
.. type: text
-->

Five days ago James Thomas posted [the following](https://www.linkedin.com/grp/post/55636-6069749695687770112?trk=groups-post-b-title) in the Software Testing & Quality Assurance group on LinkedIn:

> **Are Testing and Checking different or not?**  
> This [article by Paul Gerrard](http://gerrardconsulting.com/?q=node/659) explains why we shouldn't be trying to draw a distinction between checking and testing, but should be paying more attention to the skills of the testers we employ to do the job.

I posted a reply there, but I think I can do better than those initial thoughts, so here we go.

Let's imagine the following scene: Alice and Bob are preparing a fruit salad together.  
*Alice*: "Ok, let's make a nice fruit salad. We need some apples and some fruit."  
*Bob*: "Euh, aren't apples fruit?"  
*Alice*: "Yes. Of course. But when I say 'fruit', I mean 'non-apple fruit'."<!-- TEASER_END -->  
*Bob*: "So you don't think that an apple is fruit?"  
*Alice*: "No, I do. It's just when I say 'fruit', I want to focus on the non-apple fruit."  
*Bob*: "Uhuh. So fruit is stuff like bananas, pears and pomegranate?"  
*Alice*: "Exactly. And that would actually make a great fruit salad: apple and those three fruits."  
*Bob*: "Ok, but what if I feel like having a fruit salad. And it turns out that I only have apples and bananas at home and I don't have time to go to the store. And, importantly, I really really don't like bananas. So I decide to only use apple. That's still a fruit salad, right?"  
*Alice*: "I suppose so, technically, but still... a fruit salad without any non-apple fruit... I mean, everyone puts apples in their fruit salad and there's so much more fruit than just apples! So when I say 'fruit', I just really want to focus on the non-apple fruit, ok?"  
*Bob*: "Ok, fine. Glad we cleared that up. One more question though: what about tomatoes?"  
*Alice*: "Don't. Just don't."

Now read this piece of dialogue again and replace 'apple' with 'checking' and 'fruit' with 'testing'. Bob's confusion is exactly the reason why the whole testing/checking debate is messy: most of the time it's about testing **versus** checking. You can see it in the title of the [LinkedIn post](https://www.linkedin.com/grp/post/55636-6069749695687770112?trk=groups-post-b-title): "Are testing and checking different or not?" You can see it in [Paul Gerrard's article](http://gerrardconsulting.com/?q=node/659): "[...] the James Bach & Michael Bolton demarcation of or distinction between 'testing versus checking'." You can see it in [Cem Kaner's article](http://context-driven-testing.com/?p=69): "According to the new doctrine, "checking" is the opposite of "testing" and therefore, automated tests that check against expectations are not only not sapient, they are not tests." You can also see it in the original "[Testing vs. Checking](http://www.developsense.com/blog/2009/08/testing-vs-checking/)" blog post by Michael Bolton dated August 2009. It's right there in the title. Do take note however, that this post has been retired and we are directed to the new version "[Testing and Checking Refined](http://www.satisfice.com/blog/archives/856)". However, the new version still contains a sub-title "Checking vs. Testing".

"Testing and Checking Refined" also contains a helpful diagram, that's key to the point I want to make in this post. The diagram shows us that there's one overarching category 'testing' (fruit), which contains two things: 'checking' (apples) and all other testing activities (non-apple fruit). This helps us to understand two things.

First of all, it shows that any discussion about testing **versus** checking is bullshit. They are on a different conceptual level, just like fruit and apples, so any direct comparison is meaningless. To throw in one more analogy, what would you answer when you were asked while visiting a friend at his home: "Would you like coffee, or something to drink?"

Secondly, it explains why my previous point is difficult to get[^1]. The diagram presents people with two concepts: 'testing' and 'checking'. Of course there's also "learning by experimenting, including study, questioning, modeling, observation, inference, etc.", but that's just too vague to register mentally as an entity. It does not coalesce into a concept. What we're left with are only two concepts, 'testing' and 'checking', and the non-checking part of testing is gone. This is actually illustrated by the title of James Bach's and Michael Bolton's blog post: "Testing and Checking Refined".

So when you present two concepts in this way, is it really that surprising that people talk about them likes apples and oranges, instead of like apples and fruit? I think not.

---

*This post was originally published [here](https://testingcurve.wordpress.com/2015/11/15/why-the-testingchecking-debate-is-so-messy-a-fruit-salad-analogy/).*

[^1]: Including for myself. See for instance how I'm struggling with this very problem in my blog post from August: "[What's the word for the part of testing that's not checking?](https://testingcurve.wordpress.com/2015/08/17/whats-the-word-for-the-part-of-testing-thats-not-checking/)"
