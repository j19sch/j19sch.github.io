<!--
.. title: Site analytics: if you have two clocks...
.. slug: site-analytics-if-you-have-two-clocks
.. date: 2021-12-28 11:08:16 UTC+01:00
.. tags: blogging, site
.. category: meta
.. link: 
.. description:
.. type: text
-->

## Why

wordpress - clicky - plausible
let's compare clicky and plausible after one month
data is from 28Nov - 27Dec 2021


<!-- TEASER_END -->

## The data



### Basic page metrics

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



clicky actions 434 -> For most sites, 90+% of actions will be page views. (page views, downloads, and outbound links)
plausible pageviews 525

bounce: single page visit, makes sense for blog



### Sources

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
  		<td>t.co / twitter</td>
  		<td class="text-right">45</td>
  		<td class="text-right">40</td>
    </tr>
    <tr>
  		<td>linkedin.com</td>
  		<td class="text-right">25</td>
  		<td class="text-right">23</td>
    </tr>
    <tr>
  		<td>ministryoftesting.com</td>
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


links Clicky 84
sources Plausible 126 (84 non-search, 42 search)



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
    <tr>
  		<td>total</td>
  		<td class="text-right">45</td>
  		<td class="text-right">42</td>
    </tr>
  </tbody>
</table>


so totals
Clicky: 154 + 84 + 45 -> 283
Plausible: 175 + 84 + 42 -> 301

which is close to but not equal to visitor numbers


### Countries

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


more than 10


Some big differences. More US and NL in Plausible. A lot more China and Canada in Clicky.

Plausible: 296 country entries, matches unique visitors
Clicky: 293 country entries -> visitors (293), not unique ones (273)


### Pages


<table class="table table-bordered table-sm" style="max-width:500px">
  <thead class="thead-light">
    <tr>
      <th scope="col">pages</th>
      <th scope="col" class="text-right">Clicky</th>
      <th scope="col" class="text-right">Plausible</th>
    </tr>
  </thead>
  <tbody>
    <tr>
  		<td>clj 7</td>
  		<td class="text-right">92</td>
  		<td class="text-right">111</td>
    </tr>
    <tr>
  		<td>how remote elephant carpaccio</td>
  		<td class="text-right">53</td>
  		<td class="text-right">56</td>
    </tr>
    <tr>
  		<td>/</td>
  		<td class="text-right">48</td>
  		<td class="text-right">43</td>
    </tr>
    <tr>
  		<td>/blog</td>
  		<td class="text-right">37</td>
  		<td class="text-right">32</td>
    </tr>
    <tr>
  		<td>test strategy primer</td>
  		<td class="text-right">24</td>
  		<td class="text-right">22</td>
    </tr>
    <tr>
  		<td>two times rem el carp</td>
  		<td class="text-right">20</td>
  		<td class="text-right">21</td>
    </tr>
    <tr>
  		<td>lessons after rem el carp</td>
  		<td class="text-right">14</td>
  		<td class="text-right">12</td>
    </tr>
    <tr>
  		<td>learning clj</td>
  		<td class="text-right">9</td>
  		<td class="text-right">10</td>
    </tr>
    <tr>
  		<td>clj 5</td>
  		<td class="text-right">7</td>
  		<td class="text-right">10</td>
    </tr>
  </tbody>
</table>

more than 10



Plausible total visitors on pages 461
Clicky total views per page 434


## So what?
backend vs JavaScript analytics -> https://plausible.io/blog/server-log-analysis by Marko Saric
	bots don't run JS; some users block JS esp. external -> Ad/Script-Blockers
	https://plausible.io/blog/google-analytics-adblockers-missing-data
	https://plausible.io/docs/proxy/introduction


Segal's law is an adage that states:
A man with a watch knows what time it is. A man with two watches is never sure.
https://en.wikipedia.org/wiki/Segal%27s_law
known as his law, not really his


no consistent advantage to either, as in clicky numbers always higher or other way around
perhaps more to be said after more extensive analysis than I'm willing to do
not clear if stats are related, e.g. count the page view, but not know country -> see there

Plausible, remove clicky
pay for historical data
look of the site is better
no. of page views, so also context-of-agile analytics

more questions than before I started comparing: what's being measured and tracked how?

should I care as much as I do? something to think about the coming year
