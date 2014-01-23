Notes and Methodology appear after benchmark results.

The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data from 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

#### January 22, 2014

**IMPORTANT**: I just found out that the number of 3rd-party hosts is over-reported from what really happens, I will redo the benchmark and post correct results ASAP. Turns out the code which was counting 1st/3rd party requests was being executed even for blocked requests.

|               | HTTPSB OOB      | Adblock+        | Ghostery        | HTTPSB AA/BX    | Disconnect      | No blocker        |
| ------------- | -------------- :| -------------- :| -------------- :| -------------- :| -------------- :| ---------------- :|
| URLs visited  |              15 |              15 |              15 |              15 |              15 |                15 |
| Bandwidth     |      17,955,495 |      12,762,008 |      24,289,750 |      23,701,438 |      24,032,170 |        27,133,906 |
| Net requests  | **680** / 1,321 |   **581** / 872 | **928** / 1,817 | **943** / 1,826 |   1,014 / 1,954 | **1,848** / 2,790 |
| Domains       |     **21** / 22 |     **38** / 39 |     **49** / 50 |     **65** / 66 |         81 / 82 |     **358** / 359 |
| Hosts         |     **47** / 76 |    **65** / 110 |    **94** / 161 |   **113** / 179 |       144 / 219 |     **527** / 604 |
| Scripts       |       **0** / 0 |   **106** / 180 |   **133** / 257 |   **154** / 286 |       188 / 326 |     **419** / 560 |
| Cookies       |       **0** / 0 |      **0** / 22 |      **2** / 46 |      **8** / 60 |        ?        |     **205** / 279 |

### Notes
- This benchmark runs on Chromium Linux Mint 64-bit. Any Chromium-based browser should be able to run it though.
- "HTTPSB OOB" means *HTTP Switchboard* with [out-of-the-box settings](https://github.com/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-block-allallow-exceptionally-approach).
- "HTTPSB AA/BX" means *HTTP Switchboard* in [allow-all/block-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-allow-allblock-exceptionally-approach), with out-of-the-box preset blacklists.
- "Adblock+" means [*Adblock Plus*](https://adblockplus.org/).
- Both HTTPSB and Adblock+ were set to use [*Fanboy Ultimate List*](http://www.fanboy.co.nz/filters.html).
    * **Important note**: HTTPSB uses _only_ the blacklisted domain filters from that list, the rest is entirely ignored.
- [Ghostery](http://www.ghostery.com/) and [Disconnect](https://disconnect.me/) were set in their respective equivalent of "Block all trackers" mode.
- The latest version of all blockers was used on the day of the benchmark.
- "3rd-party" in the strictest sense, meanings if the domain name of a request differs from the domain of a page URL address, the request is deemed 3rd-party.
- "Cookies" means outbound cookies, i.e. cookies reaching a remote host. These are the cookies which really matter with regard to privacy.
- Keep in mind:
    * A user can not add/remove filters from Ghostery and Disconnect.
        - Correct me if I am wrong.
    * A user can add/remove filters from HTTPSB and Adblock+. Where these two differ:
        - How easy it is to add/remove filters: Adblock+ = [geeky](https://adblockplus.org/en/filters), HTTPSB = easy.
        - The granularity of their filters: Adblock+ = coarse- to fine-grained, HTTPSB = hostname/type of request (firewall-like).
- HTTPSB, Adblock+ and Disconnect are all [GPL](http://en.wikipedia.org/wiki/GNU_General_Public_License).
- I will repeat the benchmark once in a while and add results here in order to show consistentcy of results over time.
    * Keep in mind contents of benchmarked web pages will obviously change, so results are meaningful when compared to each other within the same benchmark.

### Methodology

Benchmarks were done using [*Browser session benchmark*](https://github.com/gorhill/sessbench). The script used is:
```
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