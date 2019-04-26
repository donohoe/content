# Mining The New Yorker for Haikus
#### 2016-04-16

To be fair, these are not properly formatted Haikus but they are fun to extract and search for.

This demo focuses on a current article from *The New Yorker* by pulling one from a JSON feed. However you can easily adapt this to any piece of text.

The main PHP file, `haiku.php`, can be viewed here:

https://github.com/donohoe/code-examples/blob/master/haiku-finder/haiku.php

There are a couple of additional functions in there that I use for *Slack/HipChat* integration and are unused right now.

If you follow the instructions in the [README.md](https://github.com/donohoe/code-examples/blob/master/README.md) at the top of the repo you can get this up and running quickly using the PHP debug server.

(image: terminal-php-debug-server.png)

Visit: http://localhost:7020/haiku-finder/haiku.php (assuming you're running a local instance)

And revel in the amazingness (or not).

`"Hargrove intends to \\ find them with his code which \\ he sometimes calls"`

I should clean-up the response a bit better, perhaps as *JSONP* but I'm sure you'll figure it out.

Pull Requests welcome.

(Coverimage: haiku-new-york-aimee-estrada.png)
