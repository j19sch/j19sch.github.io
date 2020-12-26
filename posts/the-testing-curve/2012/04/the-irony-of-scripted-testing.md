<html><body><p>A bit over a week ago, James Bach posted on twitter:
"<em>This video shows a nice simple contrast between heavy scripted testing and exploratory testing <a href="http://www.youtube.com/watch?v=PxTqjAwM2Pw">youtu.be/PxTqjAwM2Pw</a> </em>" [<a href="http://twitter.com/jamesmarcusbach/status/185816224075227137">http://twitter.com/jamesmarcusbach/status/185816224075227137</a>]

So I watched the video, hoping to see something that would make me go 'Cool!', but instead I went 'Hmmm.'

First let me say that this video does get a few things right:
- Exploratory testing can be structured by using charters.
- Exploratory testing allows you to easily change your test approach based on your test results.
- Exploratory testing is very adaptable when confronted with inaccurate or changing requirements.
Yet notice how the above only talks about exploratory testing, because for every thing the video gets right about exploratory testing, it gets something wrong about scripted testing - or rather about how scripted testing works in practice.

<strong>1. The exploratory test team starts testing earlier than the scripted test team.</strong>
At the start, the exploratory team makes a high-level plan and then starts testing. The scripted team takes more time to create a detailed plan, so starts testing later.
Of course, that's only what happens if the software is deliverd on the first day the test team goes to work. I know this still does happen, but in my experience that's now how it usually goes. Most of the time, project managers realize that the test team needs time to prepare the tests and that the best time to do this is before the software is delivered. So in that respect this video is not an honest comparison between the two approaches.
What if I turn the dishonest comparison around and add some time to prepare testing? You would see the scripted test team preparing their test cases. And you would see the exploratory test team sitting idle, because there is no software to explore. (In a less dishonest comparison, I'm sure the exploratory team would find something useful to do, though.) Finally when the software is delivered, both test teams would start at the same time with the actual testing.

<strong>2. When the requirements turn out to be incorrect, the scripted team needs to stop and update the plan.</strong>
In the video the incorrect requirement is the bridge that's not on the left side, but on the right side. Unfortunately, before the red team can do anything, they all have to gather at the place the bridge was supposed to be.
First of all, if you are going to use a scripted approach, you're not supposed to start with the script that does detailed testing of the first screen. You're supposed to start with an intake test. The reason is simple: if there are any big problems, like a bridge that's not where you expected, you want to find out as early as possible.
Now let's ignore that. Let's assume one of the testers figures out the bridge is not where he expected to be. He'll tell the other testers and the captain. They discuss how to solve it and at the same time the captain is updating the plan, the testers update the test scripts. (If you have good testers, they will have scripts that are easily updateable.) There really is no need to do it like in the video, i.e. first all gather at the wrong place and only then change the plan.

<strong>3. A bug is missed, because it was not in the plan.</strong>
Near the end there's the following dialogue in the scripted team. Captain: "Number two, look to your right! There's a huge bug right there." Number two: "No can do, Captain. That's not in the plan. We must stay on the path."
With that kind of attitude, I'm amazed Number two got far enough in his career to actually become Number two. I cannot think of any 'Captain' that would tolerate this response.
It doesn't matter if your approach is scripted or exploratory - for all I care you don't even have anything that is worthy of the term 'approach'. If someone points out a bug, you do something with it. Log it, fix it, whatever. But don't ignore it. If it does get ignored, fire the guy who hired your testers in the first place.

So there you go, three big misrepresentations of how to do scripted testing. Now I realize I'm being a bit harsh on this video, as it is intended to sell exploratory testing. And one of the tricks it uses to do this, is make the competitor, scripted testing, look bad. On the other hand, what if the potential customer looking at this video has the same reaction as I did: "That's not how you do scripted testing!" He probably won't be a potential customer for exploratory testing much longer.

To close off, let me present a different way to look at it, because there's something funny going on with scripted testing. I have never seen a scripted testing approach that does not have some exploratory elements in it. To give one example: with a scripted approach a fair amount of my best testing ideas come to me during the actual testing. When that happens, I act on those ideas and afterwards add the relevant test cases to the scripts ('reverse scripting'?). So basically I deviate from the script to do exploratory testing.
And that exactly is the irony of scripted testing: the way to make a difference as a scripted tester is by doing stuff beyond the scripted testing ... stuff like exploratory testing.</p></body></html>