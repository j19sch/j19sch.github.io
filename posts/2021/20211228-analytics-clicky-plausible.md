<!--
.. title: Site analytics: comparing Clicky and Plausible
.. slug: site-analytics-comparing-clicky-and-plausible
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

!! TALBES LOOK HORRIBLE WITH CURRENT STYLING !!




### Basic page metrics

| metric            | clicky | plausible |
| --- | --- | --- |
| unique visitors | 273    | 296 |
| visit duration | 51s | 81s |
| bounce rate | 79% | 75% |

clicky actions 434 -> For most sites, 90+% of actions will be page views. (page views, downloads, and outbound links)
plausible pageviews 525

bounce: single page visit, makes sense for blog



### Sources

| sources                  | clicky | plausible |
| --- | --- | --- |
| direct                       | 154 | 175 |
| t.co  / twitter                  | 45 | 40 |
| linkedin.com          | 25 | 23 |
| ministryoftesting.com | 5| 6 |
| testingcurve.wordpress.com/ | 3 | 3 |


links Clicky 84
sources Plausible 126 (84 non-search, 42 search)


| search                  | clicky | plausible |
| --- | --- | --- |
| google      | 28 | 24 |
| bing        | 8 | 7 |
| duckduckgo  | 2 | 9 |
| yahoo       | 1 | 1 |
| ecosia      | 6 | 1 |
|total        | 45 | 42 |



so totals
Clicky: 154 + 84 + 45 -> 283
Plausible: 175 + 84 + 42 -> 301

which is close to but not equal to visitor numbers


### Countries

more than 10

| locale        | clicky | plausible |
| --- | --- | --- |
| US          | 59 | 89 |
| NL          | 41 | 52 |
| China       | 35 | 3  |
| Canada      | 11 | 4  |
| Switzerland | 11 | 11 |
| UK          | 11 | 13 |
| Germany     | 8  | 11 |

Some big differences. More US and NL in Plausible. A lot more China and Canada in Clicky.

Plausible: 296 country entries, matches unique visitors
Clicky: 293 country entries -> visitors (293), not unique ones (273)


### Pages

more than 10

| pages        | clicky | plausible |
| --- | --- | --- |
| clj7                                     | 92 | 111 |
| how remote elephant carpaccio            | 53 | 56  |
| /                                        | 48 | 43  |
| /blog                                    | 37 | 32  |
| test strategy primer                     | 24 | 22  |
| two times remote elephant carpaccio      | 20 | 21  |
| lessons after rem el carp                | 14 | 12  |
| learing clojure                          |  9 | 10  |
| clj5                                     |  7 | 10  |


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
