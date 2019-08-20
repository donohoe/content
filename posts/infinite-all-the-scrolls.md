# Infinite ALL the Scrolls
#### March 11th 2014

With the relaunch of Time.com I’ve had a number of people comparing it to Quartz. This happened a too when Daily Beast made updates last year, but its been more pronounced this time.

Either way, its something I feel that is still mis-categorized - especially when people bemoan the “infinite scroll”.

Well, call it “infinite scroll” if you like but to me its the furthest thing from that. I fully admit the difference may be in my mind alone. Let me explain a little bit of history and something I learned many years ago a The New York Times.

When a reader makes it to the bottom of an article there is a high tendency to lose them. Thats a general observation and not just specific to the Times. The common way people have found to deal with this was to add more links. Between the obligatory ads (seriously, why!), and recommended articles, callouts to compelling content, most popular, 3rd-party modules, and impassioned pleading to sign-up for a newsletter, you eventually end up alienating the reader and they bounce.

_Gone_. Disappeared. No conversion. No new tasty ad impression to help keep the lights on.

So it was at the Times. We’d see a high number of people bounce and wouldn’t it be great of we could entice them to stay a little bit longer.

In 2011 that gave rise to the oft copied “Coming up next” module. It flew out from the bottom-right corner of the page as you approach the end of the article. It was conceived and built by Tahir Khan and it was very very effective. The Bounce Rate dropped a very significant percentage.

![Partial screenshot of Coming Up Next](/posts/media/nytimes-next-article.png)

To me the main conclusion was; readers are being paralyzed by choice. They’re overwhelmed with options. This module was clear and different from everything else and it solved one big problem - **Do not make the reader think**.

It didn’t try and guess from a list of curated items, or present a recommendation based on browsing history, it just said “go here” (arbitrarily the next article in a section) and a significant number of people did with one click.

It was genius.

![Download ALL the Articles](/posts/media/meme-download-all.png)

In building Quartz this was one lesson I took with me. In our execution the idea wasn’t to implement “infinite scroll”. It was about taking the ”Coming up next” module to its logical conclusion - remove the need to click.

What most people do not know, is that when you load a page on Quartz - be it the main page or an article, you load ALL the pages.

That side-bar on the left side (we call it the “Queue”) - it typically has 18 to 26 articles present. When you open the page we load a big string of JSON and save it all locally. Its actually quite inexpensive and it means when you click on any Article its there immediately. Only images, if not already cached are left to load.

So as you approach the end of an Article there is no cost to “preload” that next Article. Its there. You don’t have to read it. It will never be counted as a Page View unless you scroll beyond a generous threshold (we were never ever sneaky about trying to abuse PVs - PVs are evil anyway but thats a different story…).

So, in the end:

_Simple Reader Choice (effectively none) + Preloaded Data = Amazing Page Depth_

This is the part where I disappoint people and provide absolutely no numbers to back all this up. Sorry! Its a combination of memory and also keeping promises.

However I’ve seen the Page Depth metric of a number of different web sites. Ours was several times higher - typically to a ballpark of 3 to 5 times.

This isn’t going to be a magic bullet. Even at Quartz there are things we didn’t plan for (a large ‘Engage" ad at the end of every article instead of every 2 or 3). Also consider that if a reader is skipping through thats a lot of content to push into DOM - see Mediums approach that avoids this).

So yeah, forgive me if I winch at the term Infinite Scroll. Its not quite that simple.
