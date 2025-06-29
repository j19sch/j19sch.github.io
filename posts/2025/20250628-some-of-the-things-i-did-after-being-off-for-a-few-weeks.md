<!--
.. title: Some of the things I did after being off for a few weeks
.. slug: some-of-the-things-i-did-after-being-off-for-a-few-weeks
.. date: 2025-06-28
.. category: 
.. tags: 
.. type: text
.. description: Show what you do day-to-day!
-->

I wish people would share more of what they do day-to-day. Especially testers and quality engineers. Show the work you do. On the other hand, I do realize that that's hard. You don't want to share sensitive information. You want to respect the privacy of your team. And then there's the whole practical side. How much of the context do you need to share to have an intelligible story?

Since my current project is open source and my team works in public, I have more options than most. So let's see if this kind of post works out.

---

Last week was my first week back at work after a few weeks of vacation. So an important part of my week was catching up. Going through emails and chat messages. Talk with my fellow team members. Participate in the usual meetings. Some stuff that didn't make it into this post. More importantly, there are three things I did, that give a good idea of what a significant part of my job looks like.


# Refactoring some test automation code {.small}

While going through my emails, I noticed a notification mail about a pull request (PR) that fixed a flaky end-to-end test. That piqued my curiosity, so I took a look at the change. While the change was fine, I noticed some things about the test code that should be improved.

So I made those improvements and submitted a [pull request](https://github.com/kiesraad/abacus/pull/1671). The changes I made came down to:

- move hard-coded strings related to some test data files to a single location
- improve a locator so that it no longer is tightly coupled with the test data
- replace instances of `page.getByText()` in the test with a locator in a page object
- remove some unused or unneeded code

So nothing major - except for the locator improvement, I did bring that one up during standup -, but some small improvements to the readability and maintainability of our Playwright tests.


# Looking into a ~~edge~~ less common case {.small}

Another team was having a discussion about unnamed lists ("blanco lijst" in Dutch). In the Netherlands a political party can register their name and then the name will be printed on the ballot. If they don't, they can still participate in the elections, but the place on the ballot where their name would be, is left empty.

Since we hadn't really considered this less-common case yet for our application, I tried it out. As expected, the results were fairly boring. The application worked fine. Just the places where it displayed the party name, looked a little awkward, since the party name was now an empty string.

So after discussing with the team, I created an [issue to fix the UI](https://github.com/kiesraad/abacus/issues/1685). While doing so, I realized that we hadn't agreed on a translation of "blanco lijst" to English yet. (We've chosen to have our code base in English.) That became a [PR suggesting first the translation "blank list"](https://github.com/kiesraad/abacus/pull/1682) and then we changed it to "unnamed list". Finally, I submitted a [PR to extend the test data of our end-to-end tests](https://github.com/kiesraad/abacus/pull/1686). I had realized a while ago that the test data should be made a bit more representative of reality, so it was good to come across a concrete reason for such an improvement. There are more improvements to make, also to the data that's loaded into the application by default[^1], but we're going to wait with that until after some upcoming functional changes.

[^1]: It's behind a feature flag. Really cool how easy that is in Rust.


# Do exploratory testing on a new feature {.small}

While going through the titles of all the PRs that were merged during my vacation, I noticed the team had worked on the airgap detection feature[^2]. So I spent some time doing exploratory testing on this feature.

[^2]: For the record, this feature is intended more to help the admins to run the application airgapped, than to fully enforce that the application will run airgapped.

I did not find any major issues, but I did find some smaller things I'll discuss with the team.

1) If the airgap detection discovers an internet connection, it locks the application and shows a screen about how to resolve the lock. If you disable the internet connection again, however, you have to wait until the airgap detection runs again, which is every minute. When it runs again and detects no internet connection, it does not emit a log line or notify the user in any way. So what an admin would end up doing, is disable the internet connection again and then refresh the page until the application unlocks itself again.

2) The copy of the page that is shown when the application is locked, can be improved. It contains a reference to a stage in the process, while the application is also used in other stages. The page is also the same for different user roles, while it would be nicer to have role-specific copy on the page. Some of these users can disable the internet connection again, while others can't.

3) The air gap detection feature interferes with the auto-signout feature. If a user is inactive for too long, they are automatically signed out. When that happens, they are redirected to the login page, which shows a message explaining what happened. However, if that auto-signout happens while the application is locked, once the lock is removed again and the user tries to continue where they were, the user is correctly redirected to the login page, but the message shown is differnt. It says they don't have access to that page and should log in with a user that does.

What it's interesting about these three findings is that they are all examples of where the airgap detection feature interacts with another system. For the first two that system are the users of the application. For the third one it's another feature, the auto-signout. They show the importance of having a rich evaluation context[^3] when testing software.

[^3]: This really needs to be its own blog post one day.

I also noticed two things unrelated to the airgap feature.

4) Our `index.html` contains a favicon link, but in the browser no favicon is displayed. It looks like the link points to a non-existing location. I honestly don't remember if this was working fine before my vacation or not.

5) At one point the application makes two duplicate POST calls. Luckily the call is idempotent. I suspect this was caused by a recent refactor in this area.

These two findings show the importance of the [skill of noticing](link://slug/the-nine-skills-of-exploratory-testing#noticing). It's not because your focus is on a specific feature, you need to be blind to everything else. While it's hard to claim serendipity is a skill, I do feel you can increase the chances of moments of serendipity happening.

---

# (extra) Reviewing the job description for an agile test engineer {.small}

Later this year a new team will start at my organisation, building a new appplication for the nomination-part of the elections ("kandidaatstelling" in Dutch). We will be hiring a test engineer for that team and my manager asked my to review the job description. So if you're interested in becoming that test engineer, doing work similar to what I've described here, and your Dutch is at least at B2-level, drop me line!
