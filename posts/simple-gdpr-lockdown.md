# Simple GDPR Lockdown
#### 2018-05-26

![Featured:Homer Simpson seated and reading a GDPR manual](/posts/media/homer-gdpr.jpg)

There was a certain level of mis-information and mis-understanding regarding the EU privacy regulations that came into law.

I would argue that there are a lot of pundits who have no idea how difficult it is to audit your own site to find all the strange and obscure third-party vendors and scripts it pulls in and insert onto your pages. And thats a whole ton of upfront work before you've even figured how to remove, sanitize, or replace them.

Instead, how about you create something similar to an ad-blocker that only affects things you don't explicitly white-list? Its actually not that hard, and quite powerful too.

There words: **Content. Security. Policies.**

The HTTP [Content-Security-Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) response header provides control over the resources the user agent is allowed to load. It was originally envisioned to guard against cross-site scripting attacks.

It is also available as a *META* tag to all modern browsers (sorry, no Internet Explorer). I've put together a very simple implementation that ties all these things together. 

https://github.com/donohoe/simple-gdpr-lockdown/

The one critical dependency is that you are able to tell what country your visitors is from and whether that is part of the EU or not. 

In the short-term it allow you to be compliant while you dig into the codebase and obscure business rules that have accumulated over the years (or decades).

*Pull Requests* welcome.
