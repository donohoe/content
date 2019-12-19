# Web Performance: Year in Review for Media & Journalism
#### December 19th 2019

The realm of web performance goes deep into the perceived user experience of load time and the actual load time. My specific interest is in media and presenting information to readers - typically article pages. For any given news site, about 80% of their traffic will go to their articles, so that is the focus of this talk.

Measuring performance becomes harder when you layer in third-parties, internet congestion, and advertising. That said, while the daily and weekly data fluctuates, broad trends emerge.

### 2018

In December of 2018, the average news article took **24 seconds to load**, consumed **3.58MB** of your data plan, and Google scored it a [Speed Index](https://blog.catchpoint.com/2017/04/20/understanding-speed-index/) value of **11,721** (a Speed Index of 3,000 or lower is considered good).

That's very bad. 

Luckily performance is a popular subject in the [#webperf](https://twitter.com/search?q=%23webperf) community at large, engineering, and the design community. We have had another whole year to address this, so let's take a look...

### 2019 a.k.a. "The Future"

In December of 2019, the average news article took **40 seconds to load**, saved you **230K less** from your data plan, and Google scored it a slightly worse Speed Index value of **12,815**.

_WTF!?_

Let's step back a moment and review what we're dealing with and why this is just plain bad. If we had all agreed to do nothing on performance this would still have been a terrible outcome. That makes this so much worse.

The data for this comparison is here: [Performance Tracking Analysis 2018 and 2019](https://docs.google.com/spreadsheets/d/16Po_hHkaoJNJFr1oE5HJ2R1EwaX9uGLwQXrReDp04Ow/edit#gid=1178249413). It is based on the on-going daily data collection for the [Article Performance Leaderboard](https://webperf.xyz/) which is [here](https://docs.google.com/spreadsheets/d/1c1zhkdvWE0WvG84TT3Czekj0N-0sRUEBKO3c0Aeflxw/edit#gid=0).

### The Average Article

So let's take a step back for one moment. What are we talking about when we talk about "articles"? 

They are the most common page-type in news organizations. In terms of length they are often referred to in terms of "short-form" (600+ words) and long-form (1,200+) but the definition varies widely.

Most of the articles being tested are not "long-form" articles but to play devil's advocate I'm using that as an example. In this case a long-form article with 7,000 words or more (an estimated 25 minute reading time), with a leading high-res image for display on a high-resolution mobile device.

The text of that article is about 25K of data and we will assume featured image at 50K. In 2019, that constitutes 2.2% of what the browser receives when you load an average article. (The text of this post is under 6K an dthe image is 16K)

Given that we are wrapping that core content of 75K with 3,325K of secondary data, this is a horrendous state.

For that same article, lets factor in 10kb for additional HTML, 50K for CSS, 100K for fonts, and 50K for Javascript. That would bring and payload well under 300K.


![Chart of relative area based on page size](/posts/media/article-webperf-breakdown.png)

* 25K = Text
* 75K = Text with Image
* 300K = Core Text, Image, HTML, CSS, and JS
* 3,468K = All the above and Usual Suspects: Ads, frameworks, unesesary code, heavy fonts, 3rd-party trackers etc.

Only 8.9% of what the browser receives when requesting an article is actually necessary. 

You have to wonder what we are doing?

I would add that even with an ad blocker enabled I generally see articles in the 2MB range so I'm not just passively-aggressively blaming it all on ads and tracking.

This should be a wake-up call for everyone.

It is pointless to turn to band-aid solutions like [AMP](http://ampletter.org/) if our own core pages remain a dumping ground for "everything else". We know that fast media pages are possible. We know that it is possible to have article pages with ads and tracking that load faster than AMP pages.

This is not rocket science. It's not even computer science. It's just thoughtful planning.

Okay then.

In a desperate attempt to end on a lighter note, any lighter note, I'd want to acknowledge a few winners and losers in the Web Page Performance realm based on data collection for the Article Leaderboard.

There were 5 sites that had performance gains above 1000%. That's damn amazing. Not a 10% improvement, or even doubling to a 100% improvement, but more than 1000% improvement. Perhaps there is hope?

### Biggest Gains

* BBC improved 1039% and between Decembers its Load Time dropped from 44 seconds to 22 seconds
* CNN experience a 1447% improvement. It had a really high Page Size at nearly 10mb but have trimmed it back to 2.8MB. Not bad given they load video.
* Hearst Newspapers (disclaimer: former employer) was burdened by a few heavy sites (Chron.com and SeattlePI) but that has calmed down
* The LA Times had whooping 2,867% change. Both Page Load and Page Size have more than halved. The 17 second load time on Fast 3G (as an imperfect measure) isn't 'that bad'

### Largest Loses

* _The Tylt_ was really fast last year at a respectable 9s time and is now averaging 21s even though its dropped from 2MB in size to 1.5MB. Maybe it is my data; maybe it is end of year ad campiagns goign crazys?
* The New York Times, often seen as a good standard, almost doubled in load time even though Page Size decreased overall. Baffling.
* Conde Nast as a whole has been declining. 

### What can you do in 2020?

If you are one of the faster sites on the internet in media, talk more about it. The folks at Motor Trend, DotDash, and The Outline (Bustle Digital) have cracked this. [Go see for yourself](https://webperf.xyz/).

This is a solved problem.
