The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to more 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

The values are averages of aggregated results of the 15 web page visited over 5 runs. In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

The most important figure in my opinion with regard to privacy is the 3rd-party _Domain_ count, hence the results are ordered from left-to-right according to the third-party domain count.

#### June 4, 2014

|               | HTTPSB<br>BA/AX   | HTTPSB<br>AA/BX   | Adblock           | Adguard AdBlocker | Privacy&nbsp;Badger | No&nbsp;blocker   |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -------------------:| -----------------:|
| Domains       |       **21** / 22 |       **52** / 53 |       **74** / 75 |       **93** / 94 |       **157** / 158 |     **401** / 402 |
| Hosts         |       **48** / 74 |      **97** / 143 |     **128** / 183 |     **150** / 222 |       **236** / 316 |     **596** / 683 |
| Scripts       |         **0** / 0 |     **183** / 263 |     **215** / 299 |     **235** / 321 |       **308** / 406 |     **505** / 625 |
| Cookies       |         **0** / 0 |        **2** / 34 |        **8** / 49 |       **20** / 74 |         **38** / 99 |     **231** / 317 |
| Net requests  |   **625** / 1,217 |   **879** / 1,653 | **1,025** / 1,864 | **1,044** / 1,911 |   **1,144** / 2,021 | **1,973** / 2,980 |
| Bandwidth     |        16,645,571 |                 ? |        25,884,484 |                 ? |                   ? |        29,375,024 |

<sup>From now on I'm going to benchmark other blockers too. I will keep providing benchmarks for HTTPSB in _BA/AX_ and _AA/BX_ mode,
and _No blocker_ stats, so the results from these can be used as "anchors" to compare blockers across benchmarks. For example, with
the above results, I can say that using HTTPSB's results as anchors, [Ghostery](https://chrome.google.com/webstore/detail/ghostery/mlomiejdfkolichcflejclcbmpeaniij) and [Adblock Plus](https://chrome.google.com/webstore/detail/adblock-plus/cfhdojbkjhnklbpkdaibdccddilifddb) perform better privacy-wise than [Adblock](https://chrome.google.com/webstore/detail/adblock/gighmmpiobklfepjocnamgkkbiglidom),
[Adguard AdBlocker](https://chrome.google.com/webstore/detail/adguard-adblocker/bgnkhhnnamicmpeenaelnjfhikgbkllg) and
[Privacy Badger](https://chrome.google.com/webstore/detail/privacy-badger/pkehgijcmpdhfbdbbnkijodmdjhbjlgp).
**Note:** This time I primed Privacy Badger before the benchmark.</sup>

#### May 2, 2014

|               | HTTPSB<br>BA/AX   | Ghostery          | Adblock+          | HTTPSB<br>AA/BX   | Disconnect        | Privacy&nbsp;Badger<br>[beta](https://github.com/EFForg/privacybadgerfirefox/blob/master/README.md#how-heuristic-blocking-works) | No&nbsp;blocker        |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| ------------------------:| -----------------:|
| Domains       |       **21** / 22 |       **52** / 53 |       **54** / 55 |       **54** / 55 |       **93** / 94 |            **192** / 193 |     **420** / 421 |
| Hosts         |       **49** / 75 |      **99** / 160 |      **97** / 149 |     **101** / 153 |     **171** / 248 |            **299** / 381 |     **641** / 720 |
| Scripts       |         **0** / 0 |     **173** / 286 |     **177** / 272 |     **169** / 265 |     **262** / 385 |            **334** / 455 |     **518** / 641 |
| Cookies       |         **0** / 0 |        **8** / 47 |        **1** / 33 |        **2** / 43 |       **19** / 83 |             **52** / 115 |     **263** / 341 |
| Net requests  |   **680** / 1,199 |   **966** / 1,722 |   **913** / 1,612 |   **930** / 1,648 | **1,124** / 1,936 |        **1,340** / 2,176 | **2,079** / 2,849 |
| Bandwidth     |        15,147,576 |        27,406,535 |        26,489,990 |        27,040,340 |        28,758,904 |                        ? |                 ? |

<sup>Changes from previous benchmark: EFF-backed Privacy Badger (beta) added, see [these important notes](https://github.com/EFForg/privacybadgerfirefox/blob/master/README.md#how-heuristic-blocking-works), mostly, the results for Privacy Badger represent a worst-case scenario as the extension improves with usage (next benchmark I will prime it beforehand). Starting with [HTTP Switchboard version 0.8.6.4](/gorhill/httpswitchboard/wiki/Change-log#0864), Fanboy's specialized lists are not longer enabled by default.</sup>

#### February 26, 2014

|               | HTTPSB<br>BA/AX | HTTPSB<br>AA/BX | Ghostery  | Adblock+          | Disconnect   | No blocker        |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| -----------------:|
| Domains       |       **21** / 22 |       **45** / 46 |       **48** / 49 |       **53** / 54 |       **87** / 88 |     **412** / 413 |
| Hosts         |       **49** / 78 |      **89** / 142 |      **98** / 165 |      **96** / 152 |     **153** / 232 |     **609** / 697 |
| Scripts       |         **0** / 0 |     **171** / 282 |     **176** / 291 |     **175** / 280 |     **252** / 392 |     **525** / 677 |
| Cookies       |         **0** / 0 |        **3** / 43 |        **5** / 48 |        **2** / 35 |       **16** / 85 |     **231** / 316 |
| Net requests  |   **630** / 1,229 |   **941** / 1,710 |   **965** / 1,794 |   **920** / 1,698 | **1,063** / 2,018 | **2,120** / 3,048 |
| Bandwidth     |        16,342,053 |        26,603,582 |        26,502,113 |        26,714,512 |        27,950,492 |        31,282,722 |

<sup>Change from previous benchmark: Starting with HTTP Switchboard version 0.8.3.0, all preset lists of blocked hosts are enabled by default, except of for the huge "assets/thirdparties/hosts-file.net/hosts.txt". This allows HTTPSB in allow-all/block-exceptionally mode to perform well when compared to other blockers.</sup>

#### January 24, 2014

|               | HTTPSB<br>BA/AX | Ghostery          | Adblock+          | HTTPSB<br>AA/BX | Disconnect        | No blocker        |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| -----------------:|
| Domains       |       **24** / 25 |       **54** / 55 |       **59** / 60 |       **69** / 70 |       **91** / 92 |     **476** / 477 |
| Hosts         |       **55** / 82 |     **109** / 183 |     **107** / 169 |     **126** / 200 |     **157** / 240 |     **693** / 785 |
| Scripts       |         **0** / 0 |     **176** / 307 |     **173** / 293 |     **187** / 327 |     **235** / 391 |     **534** / 698 |
| Cookies       |         **0** / 0 |        **4** / 54 |        **1** / 44 |       **10** / 73 |       **12** / 86 |     **299** / 389 |
| Net requests  |   **651** / 1,232 | **1,064** / 1,921 | **1,019** / 1,815 | **1,087** / 1,934 | **1,103** / 2,091 | **2,300** / 3,236 |
| Bandwidth     |        14,935,325 |        25,128,116 |        25,150,853 |        25,785,433 |        26,007,184 |        28,855,067 |

### See also
- [Top 15 Most Popular Business Websites](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Business-Websites)
- [Top 15 Most Popular Tech & Gadget Websites](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Tech-&-Gadget-Websites)
- [Top 15 Most Popular Blogs](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Blogs)
- [Methodology and notes](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Methodology-and-notes)

### Notes
- _HTTPSB<sup>BA/AX</sup>_ means *HTTP Switchboard* with [block-all/allow-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-block-allallow-exceptionally-approach) (out-of-the-box settings).
- _HTTPSB<sup>AA/BX</sup>_ means *HTTP Switchboard* in [allow-all/block-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-allow-allblock-exceptionally-approach), with out-of-the-box preset blacklists.

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