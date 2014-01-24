Notes and Methodology appear after benchmark results.

The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

#### January 24, 2014

<sup>Note: Benchmarks were done again as Adblock+ results were found to be erroneous due to unexpected side-effects showing up when ADB+ is active (the pages were deemed fully loaded way too soon by the Chrome API for unknown reasons). I did not investigate in depth why this happens, I just made sure the benchmarker was hardened against these unexpected conditions. I may investigate further and report if time permits. In any case, results now make more sense.</sup>

|               | HTTPSB OOB        | Ghostery          | Adblock+          | HTTPSB AA/BX      | Disconnect        | No blocker        |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| -----------------:|
| URLs visited  |                15 |                15 |                15 |                15 |                15 |                15 |
| Bandwidth     |        16,114,826 |        26,095,444 |        26,406,718 |        26,594,165 |       26,406,718  |        30,381,427 |
| Net requests  |   **650** / 1,304 | **1,053** / 1,966 | **1,015** / 1,869 | **1,082** / 1,985 | **1,110** / 2,143 | **2,171** / 3,172 |
| Domains       |       **24** / 25 |       **54** / 55 |       **58** / 59 |       **68** / 69 |       **92** / 93 |     **423** / 424 |
| Hosts         |       **55** / 82 |     **109** / 182 |     **106** / 168 |     **124** / 198 |     **160** / 242 |     **638** / 730 |
| Scripts       |         **0** / 0 |     **170** / 298 |     **170** / 286 |     **185** / 324 |     **237** / 391 |     **516** / 676 |
| Cookies       |         **0** / 0 |        **4** / 53 |        **1** / 43 |       **10** / 71 |       **13** / 13 |     **251** / 340 |

### Notes
- This benchmark runs on Chromium Linux Mint 64-bit. Any Chromium-based browser should be able to run it though.
- "HTTPSB OOB" means *HTTP Switchboard* with [out-of-the-box settings](https://github.com/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-block-allallow-exceptionally-approach).
- "HTTPSB AA/BX" means *HTTP Switchboard* in [allow-all/block-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-allow-allblock-exceptionally-approach), with out-of-the-box preset blacklists.
- "Adblock+" means [*Adblock Plus*](https://adblockplus.org/).
- "3rd-party" in the strictest sense, meanings if the domain name of a request differs from the domain of a page URL address, the request is deemed 3rd-party.
- "Cookies" means outbound cookies, i.e. cookies reaching a remote host. These are the cookies which really matter with regard to privacy.
- Keep in mind:
    * A user can not add new filters in Ghostery or Disconnect.
        - Correct me if I am wrong.
    * A user can add new filters in HTTPSB and Adblock+. Where these two differ:
        - How easy it is to add/remove filters: Adblock+ = [geeky](https://adblockplus.org/en/filters), HTTPSB = easy (just click on a cell in the matrix).
        - The granularity of their filters: Adblock+ = coarse- to fine-grained, HTTPSB = hostname/type of request (firewall-like).
- HTTPSB, Adblock+ and Disconnect are all [GPL](http://en.wikipedia.org/wiki/GNU_General_Public_License).
- I will repeat the benchmark once in a while and add results here in order to show consistentcy of results over time.
    * Keep in mind contents of benchmarked web pages will obviously change, so results are meaningful when compared to each other within the same benchmark.

### Methodology

- Both HTTPSB and Adblock+ were set to use [*Fanboy Ultimate List*](http://www.fanboy.co.nz/filters.html).
    * **Important note**: HTTPSB uses _only_ the blacklisted domain filters from that list, the rest is entirely ignored.
- [Ghostery](http://www.ghostery.com/) and [Disconnect](https://disconnect.me/) were set in their respective equivalent of "Block all trackers" mode.
- The latest version of all blockers was used on the day of the benchmark.
- Chrome *Settings* / *Privacy* / *Content Settings* / *Plug-ins* => "Click to play" was selected.
- Chrome *Settings* / *Privacy* / *Content Settings* / *JavaScript* => "Allow all sites to run JavaScript" was selected.

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