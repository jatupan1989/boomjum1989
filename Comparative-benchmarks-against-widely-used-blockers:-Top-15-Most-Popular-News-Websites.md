The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to more 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

The values are averages of aggregated results of the 15 web page visited over 5 runs. In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

The most important figure in my opinion with regard to privacy is the 3rd-party _Domain_ count, hence the results are ordered from left-to-right according to the third-party domain count.

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
- _HTTPSB<sup>BA/AX</sup>_ means *HTTP Switchboard* with [out-of-the-box settings](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-block-allallow-exceptionally-approach).
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