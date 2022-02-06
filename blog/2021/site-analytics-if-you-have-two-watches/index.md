<!--
.. title: Site analytics: if you have two watches...
.. slug: site-analytics-if-you-have-two-watches
.. date: 2021-12-28 11:08:16 UTC+01:00
.. tags: site
.. category: meta
.. link: 
.. description:
.. type: text
-->

When I moved my blog to this site, I added [Clicky](https://clicky.com/) as a privacy-friendly way to collect analytics. About a month ago I added [Plausible](https://plausible.io/) analytics, because I wanted to compare the two.

My reasons to consider an alternative to Clicky, and Plausible in particular, were varied. Plausible looks nicer. Clicky's free plan only lets you track one site, I want analytics for this site and for my [Context of Agile](https://context-of-agile.org/) site. I'd like to have more than 30 days of history for my data. Those last two wishes require a paid plan (regardless if Clicky or Plausible) and Plausible is cheaper than Clicky.

So I got a 30-day trial with Plausible, added its script to my site, while Clicky also kept collecting data. With the trial now over, it's time to take a look at the data they both collected over the period from 28 November to 27 December 2021. I've added some thoughts after each table with data and at the end of this post I've added some more general thoughts.


<!-- TEASER_END -->


## Visitor metrics

Let's start with some basic site metrics.

<table class="table table-bordered table-sm" style="max-width:500px">
  <thead class="thead-light">
    <tr>
      <th scope="col">metric</th>
      <th scope="col" class="text-right">Clicky</th>
      <th scope="col" class="text-right">Plausible</th>
    </tr>
  </thead>
  <tbody>
    <tr>
  		<td>unique visitors</td>
  		<td class="text-right">273</td>
  		<td class="text-right">296</td>
    </tr>
    <tr>
  		<td>visit duration</td>
  		<td class="text-right">51s</td>
  		<td class="text-right">81s</td>
    </tr>
    <tr>
  		<td>bounce rate</td>
  		<td class="text-right">79%</td>
  		<td class="text-right">75%</td>
    </tr>
  </tbody>
</table>

Starting with the first metric, unique visitors, there's already a significant difference between Clicky and Plausible. The average visit duration is also sobering: few if any of my blog posts can be read in 51 or 81 seconds. My first reaction to the bounce rate was that it was rather high, but then I realized that for a site that's mostly a blog, it makes sense. Most visitors follow a link to a specific blog post, read it (or skim it, based on the visit duration), and move on.

There's one stat I didn't include in the table, because Clicky and Plausible don't measure it in the same way. Clicky measured 434 actions, of which 90+% should be page views. Plausible counted 525 page views. So also quite a gap there even if we consider all Clicky actions as page views.


## Sources and search

Next set of data: where do visitors come from? Are they referred via another site? Or did they find the site via a search engine?

<table class="table table-bordered table-sm" style="max-width:500px">
  <thead class="thead-light">
    <tr>
      <th scope="col">sources</th>
      <th scope="col" class="text-right">Clicky</th>
      <th scope="col" class="text-right">Plausible</th>
    </tr>
  </thead>
  <tbody>
    <tr>
  		<td>direct</td>
  		<td class="text-right">154</td>
  		<td class="text-right">175</td>
    </tr>
    <tr>
  		<td>Twitter</td>
  		<td class="text-right">45</td>
  		<td class="text-right">40</td>
    </tr>
    <tr>
  		<td>LinkedIn</td>
  		<td class="text-right">25</td>
  		<td class="text-right">23</td>
    </tr>
    <tr>
  		<td>Ministry of Testing</td>
  		<td class="text-right">5</td>
  		<td class="text-right">6</td>
    </tr>
    <tr>
  		<td>testingcurve.wordpress.com</td>
  		<td class="text-right">3</td>
  		<td class="text-right">3</td>
    </tr>
  </tbody>
</table>

*Note: there were some more small sources. I left those out, because I don't think they add to this analysis.*

The first thing that strikes me is the large number of direct visits. Since most of my page views are for specific blog posts, that either means people are typing or copy-pasting the full url to a blog post into their browser, or that people are coming from a source that can't be tracked. My bet is on the latter.

The other thing that's interesting about the data is the difference between Clicky and Plausible. Plausible has more direct visitors; Clicky has more referrals. They don't cancel each other out, however. Both Clicky and Plausible reported 84 referred visitors in total, so the difference is in the counts for the individual source sites.

Finally, testingcurve.wordpress.com is my old Wordpress blog. Apparently some people still find that site first, so perhaps I should do some search engine optimization for this site.

On to search engines:

<table class="table table-bordered table-sm" style="max-width:500px">
  <thead class="thead-light">
    <tr>
      <th scope="col">search</th>
      <th scope="col" class="text-right">Clicky</th>
      <th scope="col" class="text-right">Plausible</th>
    </tr>
  </thead>
  <tbody>
    <tr>
  		<td>google</td>
  		<td class="text-right">28</td>
  		<td class="text-right">24</td>
    </tr>
    <tr>
  		<td>bing</td>
  		<td class="text-right">8</td>
  		<td class="text-right">7</td>
    </tr>
    <tr>
  		<td>duckduckgo</td>
  		<td class="text-right">2</td>
  		<td class="text-right">9</td>
    </tr>
    <tr>
  		<td>yahoo</td>
  		<td class="text-right">1</td>
  		<td class="text-right">1</td>
    </tr>
    <tr>
  		<td>ecosia</td>
  		<td class="text-right">6</td>
  		<td class="text-right">1</td>
    </tr>
  </tbody>
</table>

The theme is probably becoming clear by now: the numbers are different, but there is no clear pattern to the differences.


## Countries

This theme continues with the countries visitors are from. Plausible has significantly more visitors from the Unites States and the Netherlands, but significantly fewer from China and Canada than Clicky.

<table class="table table-bordered table-sm" style="max-width:500px">
  <thead class="thead-light">
    <tr>
      <th scope="col">country</th>
      <th scope="col" class="text-right">Clicky</th>
      <th scope="col" class="text-right">Plausible</th>
    </tr>
  </thead>
  <tbody>
    <tr>
  		<td>United States</td>
  		<td class="text-right">59</td>
  		<td class="text-right">89</td>
    </tr>
    <tr>
  		<td>Netherlands</td>
  		<td class="text-right">41</td>
  		<td class="text-right">52</td>
    </tr>
    <tr>
  		<td>China</td>
  		<td class="text-right">35</td>
  		<td class="text-right">3</td>
    </tr>
    <tr>
  		<td>Canada</td>
  		<td class="text-right">11</td>
  		<td class="text-right">4</td>
    </tr>
    <tr>
  		<td>Switzerland</td>
  		<td class="text-right">11</td>
  		<td class="text-right">11</td>
    </tr>
    <tr>
  		<td>United Kingdom</td>
  		<td class="text-right">11</td>
  		<td class="text-right">13</td>
    </tr>
    <tr>
  		<td>Germany</td>
  		<td class="text-right">8</td>
  		<td class="text-right">11</td>
    </tr>
  </tbody>
</table>

*Note: I only included countries for which either Clicky or Plausible counted 10 or more visitors.*

At this point I started to wonder if the total number of countries matches the total number of visitors. Plausible counted 296 country entries, which matches the number of unique visitors it reports. Clicky counted 293 country entries, which matches the number of visitors it counted, but not the number of unique visitors (273). So it looks like I should not be comparing the numbers the way I am in the table above: Plausible records the country for each unique visitor; Clicky for each visitor.


## Pages

The data on which pages were visited, is no different from the previous tables. Plausible and Clicky never seem to agree.

<table class="table table-bordered table-sm" style="max-width:720px">
  <thead class="thead-light">
    <tr>
      <th scope="col">page</th>
      <th scope="col" class="text-right">Clicky</th>
      <th scope="col" class="text-right">Plausible</th>
    </tr>
  </thead>
  <tbody>
    <tr>
  		<td><a href="/blog/clojure/2021/clj7-programming-to-abstractions-with-sequence-functions/">(clj 7) Programming to abstractions with sequence functions</a></td>
  		<td class="text-right">92</td>
  		<td class="text-right">111</td>
    </tr>
    <tr>
  		<td><a href="/blog/2021/how-to-run-a-remote-elephant-carpaccio/">How to run a remote Elephant Carpaccio<a></td>
  		<td class="text-right">53</td>
  		<td class="text-right">56</td>
    </tr>
    <tr>
  		<td><a href="/">/</a></td>
  		<td class="text-right">48</td>
  		<td class="text-right">43</td>
    </tr>
    <tr>
  		<td><a href="/blog/">/blog</a></td>
  		<td class="text-right">37</td>
  		<td class="text-right">32</td>
    </tr>
    <tr>
  		<td><a href="/blog/2019/test-strategy-primer/">Test strategy primer</a></td>
  		<td class="text-right">24</td>
  		<td class="text-right">22</td>
    </tr>
    <tr>
  		<td><a href="/blog/2021/two-times-remote-elephant-carpaccio/">Two times remote Elephant Carpaccio</a></td>
  		<td class="text-right">20</td>
  		<td class="text-right">21</td>
    </tr>
    <tr>
  		<td><a href="/blog/2021/lessons-learned-after-facilitating-elephant-carpaccio/">Lessons learned after facilitating remote Elephant Carpaccio</a></td>
  		<td class="text-right">14</td>
  		<td class="text-right">12</td>
    </tr>
    <tr>
  		<td><a href="/my-projects/learning-clojure/">Learning Clojure</a></td>
  		<td class="text-right">9</td>
  		<td class="text-right">10</td>
    </tr>
    <tr>
  		<td><a href="/blog/clojure/2020/clj5-loop-and-recur-into-and-conj/">(clj 5) Loop and recur, into and conj</a></td>
  		<td class="text-right">7</td>
  		<td class="text-right">10</td>
    </tr>
  </tbody>
</table>

*Note: I only included pages for which either Clicky or Plausible counted 10 or more visitors.*

These numbers mostly makes sense to me. The first two are posts I published in the reporting period. The one about remote Elephant Carpaccio links to two post from October about the same topic, so they also show up in the data. My home page and blog page are in 3rd and 4th place. The "Test strategy primer" is from 2019, but I shared it in at least one Slack workspace. Which leaves the bottom two entries, both related to Clojure. I'm not sure why they got those views. I did publish a Clojure blog post in the reporting period, but it links to neither of those two pages.



## My thoughts

After all of this I feel like I have more questions than before I started looking into this.

Are Clicky and Plausible reporting the same things? I know they're not when Clicky labels something as "actions" and Plausible as "page views", but when they are labeled the same? For countries, one counted unique visitors, while the other counted visitors. Perhaps something similar is going on with other numbers that are labeled the same?

One step deeper is the question: are they measuring the same things? Probably not, considering the differences in their numbers. And there have to be differences in implementation between Clicky and Plausible, since they were built by different people. Thirdly, both Clicky and Plausible depend on visitors allowing their script to be executed. Since that is some JavaScript served from Clicky's or Plausible's domain[^1] instead of the visited site, some browsers and plugins will block it, depending on their settings. So some visitors will have both Clicky and Plausible blocked, some just one of them, some neither.

Which brings us to the law[^2] I referred to in the title:

> "A man with a watch knows what time it is. A man with two watches is never sure."

Someone with two watches can't escape the question: is one of my watches correct, or if not, at least more correct than the other one? And without a third watch that's known to be correct, there's no way to tell. Of course, someone with a single watch has no guarantee that their watch tells time correctly either, but at least they don't have a second watch constantly reminding them of that fact. The same with site analytics.

I still had to make a decision, though, and decide whether to keep either Clicky or Plausible. I went with Plausible for the reasons I stated at the start of this post. With the next bill date in 12 months, that gives me ample time to reflect on some other questions. How important are site analytics to me? How useful? Is it worth the money I'm paying? And the biggest question: could it be that I sometimes care a bit too much about my site's numbers?



[^1]: There are ways around this. One is to proxy the script so it seems to originate from the same domain. Another one is to track analytics server-side, which has other challenges, e.g. excluding crawlers and bots. (They tend to not execute any JavaScript, so won't be counted via a client-side analytics script.)

[^2]: This law is known as [Segal's law](https://en.wikipedia.org/wiki/Segal%27s_law). That's a misattribution, though. Apparently it was coined by the San Diego Union.
