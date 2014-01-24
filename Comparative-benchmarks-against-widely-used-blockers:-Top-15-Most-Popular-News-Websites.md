More details regarding the benchmarks found at [Methodology and notes](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Methodology-and-notes).

The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

#### January 24, 2014

<sup>Note: Benchmarks were done again as Adblock+ results were found to be erroneous due to unexpected side-effects showing up when ADB+ is active (the pages were deemed fully loaded way too soon by the Chrome API for unknown reasons). I did not investigate in depth why this happens, I just made sure the benchmarker was hardened against these unexpected conditions. I may investigate further and report if time permits. In any case, results now make more sense.</sup>

|               | HTTPSB<sup>OOB</sup>        | Ghostery          | Adblock+          | HTTPSB<sup>AA/BX</sup>      | Disconnect        | No blocker        |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| -----------------:|
| URLs visited  |                15 |                15 |                15 |                15 |                15 |                15 |
| Domains       |       **24** / 25 |       **54** / 55 |       **58** / 59 |       **68** / 69 |       **92** / 93 |     **423** / 424 |
| Hosts         |       **55** / 82 |     **109** / 182 |     **106** / 168 |     **124** / 198 |     **160** / 242 |     **638** / 730 |
| Scripts       |         **0** / 0 |     **170** / 298 |     **170** / 286 |     **185** / 324 |     **237** / 391 |     **516** / 676 |
| Cookies       |         **0** / 0 |        **4** / 53 |        **1** / 43 |       **10** / 71 |       **13** / 77 |     **251** / 340 |
| Net requests  |   **650** / 1,304 | **1,053** / 1,966 | **1,015** / 1,869 | **1,082** / 1,985 | **1,110** / 2,143 | **2,171** / 3,172 |
| Bandwidth     |        16,114,826 |        26,095,444 |        26,406,718 |        26,594,165 |       27,388,244  |        30,381,427 |

### Notes
- "HTTPSB OOB" means *HTTP Switchboard* with [out-of-the-box settings](https://github.com/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-block-allallow-exceptionally-approach).
- "HTTPSB AA/BX" means *HTTP Switchboard* in [allow-all/block-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-allow-allblock-exceptionally-approach), with out-of-the-box preset blacklists.

### Methodology
Benchmarks were done using [*Browser session benchmark*](https://github.com/gorhill/sessbench). The script used is:
```
wait 3
repeat 5
clear cache
clear cookies
http://news.yahoo.com/
http://www.huffingtonpost.com/
http://www.cnn.com/
http://news.google.com/
http://www.nytimes.com/
http://www.foxnews.com/
http://www.theguardian.com/
http://www.nbcnews.com/
http://www.dailymail.co.uk/
http://www.usatoday.com/
http://www.washingtonpost.com/
http://www.wsj.com/
http://www.abcnews.go.com/
http://news.bbc.co.uk/
http://www.latimes.com/
```

List taken from [Top 15 Most Popular News Websites | January 2014](http://www.ebizmba.com/articles/news-websites).