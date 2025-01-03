.. title: Your default response should be a safe one
.. slug: your-default-response-should-be-a-safe-one
.. date: 2024-12-29
.. category: misc
.. tags: programming, note-taking, communication
.. type: text
.. description: Your default response should be a safe one. Because it's what you default to when there's not time to think.
-->

In his training DVD *"[Ukemi from the Ground Up](https://edgeworkbooks.com/dvd-ukemi-from-the-ground-up/)"*, [Ellis Amdur](https://edgeworkbooks.com/about-ellis-amdur/) explains how your default response should be a safe one. In the context of the video it's about what your action should be in response to an Aikido technique like *kote gaeshi*: Do you jump and do a breakfall? Or do you roll? The breakfall is the safe option. The roll is the comfortable one, except for the times you should have done the breakfall. Then you break your wrist...

Unfortunately, the choice between breakfall and roll is not up to you. *Kote gaeshi* is a throw executed through a wrist lock[^1] and it's up to the person applying the technique what kind of throw it will be. Either they gently apply the wrist lock, guide you to the ground, and you can roll. Or they apply the technique more dynamically and there's no time to roll. In that case you have to jump and turn over your arm to fall safely on your side/back. That's what's called a breakfall.

[^1]: To be clear: it's not just a matter of grabbing someone's hand and yanking it in the right direction. You also need proper positioning, compromising your opponent's balance first, using the wrist lock to control the opponent's center, etc.

As you can imagine, there's not always a lot of time to think and decide between roll and breakfall. And if there's no time to think, whatever your default response is, that's what your body will do. That's why your default response to *kote gaeshi* should be the breakfall, the response that's safe in both circumstances. The worst case scenario is that you take a breakfall you didn't need to. While the alternative, defaulting to the role even when you should have done the breakfall, comes with significantly worse consequences.


<!-- TEASER_END -->

<div style="margin-top: 1.7rem;" />


In software development we luckily don't have to make many decisions that might result in harm to our own bodies. (There's plenty of other harm done in and through software development, though.) So arguably there's always time to think. The problem, however, is that there's rather too many things to think about. You want to be thinking about the important parts of the problem and do the rest on auto-pilot, i.e. have your default responses deal with them. And if we're going to rely on our defaults, we better make sure that they are safe ones. So below I'll share three of my defaults.


# Git status all the things {.small}
One of my defaults is to do `git status` as basically every other *git* command. Even though I have my command-line set up so that it tells me what branch I'm on and what state that branch is in. I just like to check what exactly *git* thinks the status of my changes is.

So a normal set of *git* actions for me is:

- `git status`
- `git add .`
- `git status`
- `git commit`
- `git status`
- `git push`

And when I see something that surprises me, I will `git diff` or `git log` to dig one level deeper.

I do know that until I push, I can easily correct what I'm doing. And even after pushing, if it's just my branch, no one is going to mind a quick force push to fix some small thing.

And yet, I `git status` all the time, because I want to get it right the first time. And because if my habit is to `git status`, I'm not going to make any mistakes. And the one time I'm in a rush or under pressure, and I'm more likely to mess something up, I will have my default of `git status`-ing all the time, making it more likely that I catch my mistake before it ends up in a commit.


# Always take notes {.small}
I always take notes. In meetings. In 1-to-1s. About what I do every day. And I take notes when I'm trying to figure something out. Such as, how to get a certain piece of software to work on my machine. Or when I'm doing some exploratory testing.

Most of the time, I don't return to those notes after I'm done with whatever I wanted to do. Sometimes I do, however. Sometimes I even edit them and clean them up and share them in the team wiki. Most of the time, though, the value of my notes is during the thing I'm doing. When I'm not sure anymore what exactly it is that I did, or in what order. Then it's great to have notes from your past self to tell you.

And what's very much not great, is being in the middle of figuring something out, having a question about what you did five minutes ago, not being able to answer that question from the top of your head, but also having no notes to fall back on.

So that's why I take notes. They help me during the thing, to look back into the past and to help me focus and structure. And that's enough value that I'd rather take notes too often, then having to retrace and redo all my steps, just because I couldn't be bothered to write things down.


# Post in the team channel {.small}

When you want to discuss something over chat with a single person, it's tempting to send them a direct message. Even when you're not discussing something private or sensitive. However, that prevents anyone else, both in the present and the future, from ever finding that conversation. Someone on the present might have been able to contribute. And both someone in the present or the future might have learned something useful from it.

So a good default is to post in the team channel. And when you are posting something sensitive or private, I'd assume you're taking enough care in how you phrase your message, that you also realize that the team channel is not the right place for it.
And if a conversation turns private or sensitive, you always have the option to suggest to continue it elsewhere. Sensitive conversations probably benefit from something more high-bandwidth than chat anyway.

To be perfectly honest, I sometimes struggle with sticking to this default. When it's not a habit of the whole team, it does feel a little weird. It makes it feel like you're calling someone out, even though that's not your intention. Because the room is quiet and then there's you speaking up. I find it helps in such cases to be explicit about what you're doing, aka "having the meta-conversation". And since the stakes are not that high, it's ok to lapse once in a while.

You could argue that the safe default is actually the opposite. Default to direct messages, so anything sensitive remains private between the two of you. I can imagine teams where that is actually the right choice. And if that is your team, I hope you find yourself in a better team soon.

---

What are some of your default responses to certain situations? How safe are they? And what are the defaults in your team?
