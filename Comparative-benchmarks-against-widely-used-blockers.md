See Notes and Methodology appear after benchmark results.

The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data from 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

#### January 22, 2014
Note: the "Requests" row will be revised to show only network requests, but split in "3rd-party / all" figures.

 | HTTPSB OOB | Adblock+ | Ghostery | HTTPSB AA/BX | Disconnect | No blocker
--- | ---:| ---:| ---:| ---:| ---:| ---:
Bandwidth | 16,018,841 | 12,049,602 | 21,609,353 | 21,858,245 | 22,756,202 | 26,020,235
Requests allowed<br>(network + cache) | 1,293<br>(1,290 + 3) | 993<br>(983 + 10) | 1,781<br>(1,771 + 10) | 1,831<br>(1,798 + 33) | 1,972<br>(1,949 + 24) | 2,925<br>(2,788 + 137)
Hosts: **3rd-party**/all | **53** / 80 | **76** / 118 | **97** / 158 | **110** / 167 | **174** / 282 | **198** / 324 | **525** / 597
Scripts: **3rd party**/all | **0** / 0 | **121** / 204 | **150** / 256 | **174** / 282 | **198** / 324 | **524** / 670
Cookies: **3rd party**/all | **0** / 0 | **3** / 26 | **9** / 46 | **16** / 62 | **15** / 75 | **212** / 277

### Notes
- This benchmark runs on Chromium Linux Mint 64-bit. Any Chromium-based browser should be able to run it though.
- "HTTPSB OOB" means *HTTP Switchboard* with [out-of-the-box settings](https://github.com/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-block-allallow-exceptionally-approach).
- "HTTPSB AA/BX" means *HTTP Switchboard* in [allow-all/block-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-allow-allblock-exceptionally-approach), with out-of-the-box preset blacklists.
- "Adblock+" means [*Adblock Plus*](https://adblockplus.org/).
- Both HTTPSB and Adblock+ were set to use [*Fanboy Ultimate List*](http://www.fanboy.co.nz/filters.html).
    * **Important note**: HTTPSB extract _only_ the blacklisted domain filters from that list, the rest is entirely ignored.
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
- I will repeat the benchmark once in a while and add results here in order to show consistentcy of results over time (keeping in mind contents of benchmarked web pages will obviously change).
- See methodology at the bottom of the page.

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