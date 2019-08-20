# The Idea of Quartz
#### September 12th 2017
## a.k.a. “I found an old bunch of screenshots”

Quartz launched on September 24th, 2012 at 9:55am EST. As it comes up on 5 years of age, I thought it was overdue to test my l33t medium typing skillz.

Quartz started for me on February 22nd 2012 with a tweet to Zach Seward on his departure from the WSJ for an _yet unnamed venture_. I was living in Seattle at the time and coincidentally had just landed in NYC. The next morning I found myself having breakfast with Kevin Delaney and talking news product.

I find it crazy that people ask me about the early days. I tend to describe it as Kevin, Zach, and I doing “_all the things we wanted, but weren’t allowed to do at our old jobs_” (WSJ and NYT).

This is a hastily arranged snapshot of notes, ideas, and a small part of the process that went into Quartz in the very early days.

## The Big Picture
The homepage was dead in 2012. Well, not really. However we saw that the core experience of any news platform rests in the article. The Article should be the application. The homepage was secondary and could be managed in a variety of ways.

In any other organization, the things we were proposing would make the powers-that-be nervous. While certain ideas are accepted today, five years ago this was a radical departure from the playbook.

The original plan included deep-linking and annotations. We also planned to launch with HTTPS enabled. HTTPS isn’t as hard to accomplish these days in 2017 but was a larger challenge back in 2012.

That was too much to take on in the timeline we had and had to wait until later.

![Featured:Whiteboard with early Quartz wireframes](/posts/media/idea-of-quartz/1-whiteboard.jpg)

The early guiding principles included:

* Focus on tablet and mobile viewports
* The mouse is secondary — go with thumbs and scrolling
* Page Views can go to hell — its engagement and experience stupid
* Own ads. View as a first-class citizen. Don’t repeat industry mistakes.

In short; If you do right by the reader, respect the content, the revenue will follow.

So from whiteboard discussions with Zack and others, I usually then went to the iOS app Paper (by FiftyThree).

![Wireframes](/posts/media/idea-of-quartz/2-wireframe.jpg)
![Wireframe of long article](/posts/media/idea-of-quartz/3-wireframe-article-long.jpg)
![Wireframe of annotations](/posts/media/idea-of-quartz/4-wireframe-annotations-side.jpg)
![Wireframe of an annotation](/posts/media/idea-of-quartz/5-wiresframe-annotation.jpg)
![Wireframes of previewing an annotation](/posts/media/idea-of-quartz/9-wiresframe-annotation-preview.jpg)

A large part I enjoyed was thinking through wireframes and engineering constraints together. It helped to mentally silo functionality into ‘_what you know is possible_’ and ‘_what requires research_’ and understanding the knock-on relationship between the two.

## Development
In the time before browsers provided rich viewport options for development we had to hack around that.

We built the site around WordPress, but it didn’t publish pages. Instead we built a JSON representation of articles, and collections of articles that we pulled in, cached locally. The article body was one big HTML fragment.

The first prototype didn’t include “continuous scroll” but it demonstrated the speed nature of pulling in articles quickly from cache. 

![Screenshot of website in development](/posts/media/idea-of-quartz/10-screenshot-dev.jpg)

When you loaded “qz.com” you had inadvertently loaded data for 15 to 20 articles. We were well within localStorage limitations of the time. The end result was lightning fast when scrolling from one to another.

I would add that while I have no respect for Page Views as a meaningful metric, I was paranoid people would accuse us of abusing the metric. As such, when you scroll from one article to another a new PV was triggered if:

* The next article because 60–70% into the viewport
* Was in view for 2–3 (I think) number of seconds — to prevent false counts from when people scroll quickly and skip between articles

![Screenshot](/posts/media/idea-of-quartz/11-screenshort-article-partial.jpg)

The new’ish APIs offered in the HTML5 specification were one reason we were pushing big on the open-web. We felt we could provide an experience that was in keeping with the intent of the web and avoided a parallel app development.

We also used the cache manifest so that site would work offline. Sadly the API at the time was too buggy and likley not very well thought through. It made trouble-shooting a huge pain.

## Annotations
Annotations couldn’t come soon enough. The goal was deep-linking, highlighting, and annotations. Sam built a custom backend to manage the whole process. We followed a similar method to what I had done at the NYTimes and it was a joy to work on.

![Screenshot of Annotations](/posts/media/idea-of-quartz/12-annotations-1.jpg)
![Screenshot of Annotations](/posts/media/idea-of-quartz/14-annotations-3.jpg)

## 451
At one point Gawker had to remove an article from UK readers. It brought up the whole issue of:

* How to you block content by country, and
* How do you inform readers that they’re experiencing censorship.

![Screenshot of 451 Error Page](/posts/media/idea-of-quartz/16-451-error-page.jpg)

We had reporters in London and I wanted to a solution in place rather than be reactive.

The 451 error code was a draft (became an official code in December 2015) but we implemented part of it anyway just in case. Ultimately it didn’t make it to production as we still had questions on the CDN level to figure out.

## Ads, Native Content & Sponsored Content
These days I guess its “native content”. I’ve tried working on sponsored content at The New Yorker and seen how it goes across Conde Nast. In my mind, how it was built at Quartz remains the gold standard.

Internally we often said; We focus on our two customers: The reader and the advertiser. Do right by both of them.

![Screenshot of native ad](/posts/media/idea-of-quartz/17-ads-1.jpg)

From the very beginning, we intended that sponsored content had the full set of editorial tools and features that regular content had. That it was templated and differentiated from regular editorial content.

The template is the important factor. I still firmly believe that you will have a hard time scaling native content if you have to do bespoke work on a client by client basis. A flexible and rich template — with known constraints is the holy grail.

![Screenshot of native ad](/posts/media/idea-of-quartz/18-ads-2.jpg)

All thoughts on ads went though the lens of UX and feedback. Among the early principles and features ofd ads, we covered:

* Responsive ad units
* Tracking Viewability internally before we knew the name for it
* Ads could work offline
* No popups and no interstitials

On a personal note, it was amazing the support we got internally on our proposal for ads. Its a rare thing when editorial, engineering and revenue sides are in such sync. I want to write an essay on that alone but I can’t. Jay Lauf and the team were great partners and collaborates and ultimately made it all possible.

## Ad Blockers
Not many people know this but we created ads that only work with ad blockers. If you had an ad blocker you were shown simple static creative asking you to donate to a good cause.

Call it an easter-egg.

![Screenshot of easter egg](/posts/media/idea-of-quartz/19-easter-egg.jpg)

Collectively these received about 20.8 million impressions. I can only hope that translated to some minor increase in donations. Assuming an optimistic CTR of 0.05% then that would be 10K click-throughs.

Versions
We built a simple version tracker to track medium and major site updates. Powered by Google Sheets but sadly no longer working.

![Screenshot of the deployment history dashboard](/posts/media/idea-of-quartz/21-last-deploy-dashboard.jpg)


## The End
I left Quartz early in 2014 and most of my early work has been rebuilt, removed, or refactored since then (so much for the cassette player easter-egg).

I continue to be impressed with the direction and promise of Quartz — the continued focus on good people doing good things. I’m proud that the ideals that drove us all at the very beginning continue to be alive and well.

Happy Birthday Quartz!
