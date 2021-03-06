# Web Page Performance: SF Chronicle
#### 2018-06-11

![Featured:Screenshot of SF Chronicle](/posts/media/sfchronicle-screenshot.png)

As the new template for [The San Francisco Chronicle](https://www.sfchronicle.com) rolls out to a wider audience, I want to take a step back and talk a little on web page performance.

We've asked a lot of our web pages over the years, slowing them significantly, and this project was an opportunity to hit the reset button.

**Why should I care?**

*TLDR; *Slow pages can lead to higher bounce rates, and visitors giving up before the page can load - and that's an immediate problem with turning visitors into subscribers. Slow pages mean ads go unseen, viewability suffers, or in soem cases ad impressions don't get a chance to fire at all. For those that do make it, we lose them at a higher rate as they click through articles and grow impatient. That's just desktop, imagine that for our growing mobile audience who are often on slower connection speeds. 

**Where are we at?**

The main metrics I care about and will focus on here are:

1. **Load Time**:  The time taken for the web page to be considered fully loaded (lower is better).
2. **Speed Index**:  Google's own measure of performance which is used as a SEO signal (lower is better).
3. **Page Size**:  The amount of bandwidth needed to load all the elements of a page (lower is better).

As we A/B test we have seen a significant improvement.

The **page load-time has dropped by 41%** from 28 seconds to 16 seconds. **Speed Index has dropped almost 30%** from 18,000 to 12,700. The **page-size has been reduced by a third** from an average of 3MB down to 2MB (which matters if you have a data plan) .

As we move forward we hope to squeeze further gains and we are factoring in web page performance in terms of how we plan future development work. Once we switch from A/B test to the default template I would speculate that this will help in SEO and other metrics too.

This chart shows ongoing test results from March and you can see how progress has been made in a few dramatic steps.

![WebPage Speed for SF Chronicle](/posts/media/sf-chronicle-pagespeed.png)

I test using a independent service ([webpagetest.org](https://www.webpagetest.org)) running a mobile device on a 3G connection and take the running average of the last 4 days. Detailed data and results are here (updated daily), including links to the actual test reports:

https://docs.google.com/spreadsheets/d/1Q0xZbojA4KqemLQgOyCT0pYXlt4Ec1pUOi-ARHEol5c/edit

The current snapshot as of writing (June 11th) is:

![WPP](/posts/media/wpp-stats.png)

This places it 32nd on the [Article Performance Leaderboard](https://webperf.xyz/), down from 45th place, and the goal is to get this into the top 10.

As this is rolled out to other sites (like the Houston Chronicle, San Antonio Express News) we expect similar results. Improvements on this one template will benefit all and we know we're not as performant as we can.

As we handle request for new additions or features on our pages we have started looking at the web page performance impact. We need to put the days of vendor promises that new features are "*just one line of javascript*" (lies!) behind us as we see the real and measurable benefits of faster web pages.
