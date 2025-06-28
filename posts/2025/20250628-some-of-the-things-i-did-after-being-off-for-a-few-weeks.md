<!--
.. title: Some of the things I did after being off for a few weeks
.. slug: some-of-the-things-i-did-after-being-off-for-a-few-weeks
.. date: 2025-06-28
.. category: 
.. tags: 
.. type: text
.. description: 
-->

Last week was my first week back at work after a few weeks of vacations. And since I'd love to see more blog posts (and conference talks) about the work it is people actually do, I figured I could write about what I did in that first week back.

Of course, I did the obvious things. Catch up on email and chat. Have chats with some of my team mates. Participate in the usual meetings. And I kept track of everything through [my notes](link://slug/my-note-taking-system-for-work) (tl;dr bullet journal). And I did some other things I'm not going to talk about, because not everything should be public. But there are three things I can and want to talk about, as they give a good idea of what a significant part of my job entails.


# Refactoring some test automation code {.small}

While going through my emails, I noticed a notification mail about a pull request (PR) that fixed a flaky end-to-end test. That piqued my curiosity, so I took a look at the change. While the change was fine, I noticed some things about the test code that should be improved.

So I made those improvements and submitted a pull request. Luckily my current project is open source, so I can show you [the actual PR](https://github.com/kiesraad/abacus/pull/1671). The changes I made came down to:

- move hard-coded strings related to some test files to a single location
- improve a locator so it no longer is tightly coupled with the test data
- replace instances of `page.getByText()` in the test with a locator in a page object
- remove some unused or unneeded code

So nothing major - except for the locator improvement, I did bring that one up during standup -, but some nice improvements to the readability and maintainability of our Playwright tests.


# Looking into a ~~edge~~ less common case {.small}

Another team was having a discussion about unnamed lists ("blanco lijst" in Dutch). In the Netherlands a political party can register their name and then it will be printed on the ballot. If they don't, they can still participate in the elections, but the place on the ballot where their name would be, is left empty.

Since we hadn't really considered this less-common case yet for our application, I tried it out. As expected, the results were fairly boring. The application worked fine. Just the places where it displayed the party name, looked a little awkward, since the party name was now an empty string.

So after discussing with the team, I created an [issue to fix the UI](https://github.com/kiesraad/abacus/issues/1685). While doing so, I realized that we hadn't agreed on a translation of "blanco lijst" yet. That became a [PR suggesting first the translation "blank list"](https://github.com/kiesraad/abacus/pull/1682) and then we changed it to "unnamed list". Finally, I submitted a [PR to extend the test data of end-to-end tests](https://github.com/kiesraad/abacus/pull/1686). I had realized a while ago that the test data should be made a bit more representative of reality, so it was good to come across a concrete reason for such an improvement. There are more improvements to make, also to the data that's loaded into the application by default[^1], but we're going to wait with that until after some upcoming functional changes.

[^1]: It's behind a feature flag. Really cool how easy that is in Rust.


# Do exploratory testing on a new feature {.small}

While going through the titles of all the PRs that were merged during my vacation, I noticed they had worked on the airgap detection feature[^2]. So I spent some time doing exploratory testing on this feature.

[^2]: For the record, this feature is intended more to help the admins to run the application airgapped, then to fully enforce that the application will run airgapped.

I did not find any major issues, but I did find some smaller things I'll discuss with the team.

1) If the airgap detection discovers an internet connection, it locks the application and shows a screen about how to resolve the lock. If you disable the internet connection again, however, you have to wait until the airgap detection runs again, which is every minute. When it runs again and detects no internet connection, it does not emit a log line. So what an admin would end up doing, is to disable the internet connection again and then refresh the page until the application unlocks itself again.

2) The copy of the page that is shown when the application is locked, can be improved. It contains a reference to a stage in the process, while the application is also used in other stages. The page is also the same for different user roles, while it would be nicer to have role-specific copy on the page.

3) The air gap detection feature interferes with the auto-signout feature. If a user is inactive for too long, they are automatically signed out. When that happens, they are redirected to the login page, which then shows a message explaining what happened. However, if that auto-signout happens while the application is locked, when the internet connection is disabled again and the user tries to continue where they were, they are redirected correctly to the login page, but the message says something different. It says they don't have access to that page and should log in with a user that does.

I also noticed two things unrelated to the airgap feature.

4) Our `index.html` contains a favicon link, but in the browser no favicon is displayed. It looks like the link points to a non-existing location. I honestly don't remember if this working fine before my vacation or not.

5) At one point the application makes two duplicate POST calls. Luckily the call is idempotent. I suspect this was caused by a recent refactor in this area.

There are two things I think are interesting about the things I found.

The first three are all examples of where the airgap detection feature interact with another system. For the first two that system are the users of the application. For the third one it's another feature, the auto-signuit. They show the importance of having a rich evaluation context[^3].

[^3]: This really needs to be its own blog post one day.

The last two are things unrelated to the feature, but that I discovered while exploring the feature. They show the importance of the [skill of noticing](link://slug/the-nine-skills-of-exploratory-testing#noticing).

---

# (bonus) Reviewing the job description for an agile test engineer {.small}

Later this year a new team will start at my organisation, building a new appplication for the nomination-part of the elections ("kandidaatstelling" in Dutch). We will be hiring a test engineer for that team and my manager asked my to review the job description. So if you're interested in being that test engineer, doing work similar to what I've described here, and your Dutch is at least at B2-level, drop me line!
