# Twenty Five Years of The New York Times Crossword Data
#### Date: 2017-11-22

Coverimage: crossword.jpg

I first started reverse-engineering the *[.puz](http://www.muppetlabs.com/~breadbox/txt/acre.html)* file format about 6 years ago. Its a very efficient crossword format that goes to great lengths to compact the data into a small payload.

With that done, the *The New York Times* crossword archive had interesting information.

This is a [CSV](https://github.com/donohoe/nyt-crossword) of collected data representing clues and answers from *The New York Times* [crossword archive](https://www.nytimes.com/crosswords/archive) over almost 25 years.

It spans December 1993 through to July 2017 and contains about 432,205 clues and answers.

One thing I really love about this data is how it captures moments in time. For example, take *Facebook*. One of the Clues to which this is the answer goes "*Alternative to Friendster or MySpace*". Who remembers either of those services? Who ever thought of Facebook as a competitor to those now?

Or even better, there is "*AOL*". It went from "*Big letters in cyberspace*" and "*Yahoo! competitor*" in 2000, to "*Earthlink competitor*" in 2002 and then didn't feature much after 2011.

Example:
<pre><code>
"id","thekey","key","source","file","date","day","difficulty","direction","number","instruction","flag","groupid","question","answer"
"1048337","Jul2814A24","nytimes","Jul2814.puz","2014-07-28 00:00:00","Monday","6","A","24",,"0","nytimes","Cutters that cut with the grain","RIPSAWS"
"1048338","Jul3015A48","nytimes","Jul3015.puz","2015-07-30 00:00:00","Thursday","3","A","48",,"0","nytimes","Ill-looking","PALE"
"1048336","Jul3015D47","nytimes","Jul3015.puz","2015-07-30 00:00:00","Thursday","3","D","47",,"0","nytimes","Like some tea","HERBAL"
"1048335","Jul2814D23","nytimes","Jul2814.puz","2014-07-28 00:00:00","Monday","6","D","23",,"0","nytimes","With great attention to detail","MINUTELY"
"1048333","Jul2814A22","nytimes","Jul2814.puz","2014-07-28 00:00:00","Monday","6","A","22",,"0","nytimes","Portent","OMEN"
"1048329","Jul2814A20","nytimes","Jul2814.puz","2014-07-28 00:00:00","Monday","6","A","20",,"0","nytimes","In the manner of","ALA"
"1048330","Jul3015D44","nytimes","Jul3015.puz","2015-07-30 00:00:00","Thursday","3","D","44",,"0","nytimes","Long vowel indicator","MACRON"
"1048331","Jul2814A21","nytimes","Jul2814.puz","2014-07-28 00:00:00","Monday","6","A","21",,"0","nytimes","Fraidy-cat","WUSS"
"1048332","Jul3015D45","nytimes","Jul3015.puz","2015-07-30 00:00:00","Thursday","3","D","45",,"1","nytimes","Creator of the characters added in 17-, 28-, 44- and 57-Across","ALCOTT"
"1048334","Jul3015D46","nytimes","Jul3015.puz","2015-07-30 00:00:00","Thursday","3","D","46",,"0","nytimes","University that was originally the Medical College of Louisiana","TULANE"
"1048325","Jul2814D18","nytimes","Jul2814.puz","2014-07-28 00:00:00","Monday","6","D","18",,"0","nytimes","""Gross!""","EWW"
"</code></pre>

The [CSV is available in full on Github](https://github.com/donohoe/nyt-crossword). Please let me know if you spot gaps or errors.

**Further reading**

* [puz - FileFormat.wiki](https://code.google.com/archive/p/puz/wikis/FileFormat.wiki)
* [PUZ format](https://fileinfo.com/extension/puz)
