More details regarding the benchmarks found at [Methodology and notes](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Methodology-and-notes).

The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

#### January 24, 2014

|               | HTTPSB<sup>OOB</sup> | Ghostery          | Adblock+          | HTTPSB<sup>AA/BX</sup> | Disconnect        | No blocker        |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| -----------------:|
| URLs visited  |                15 |                15 |                15 |                15 |                15 |                15 |
| Domains       |       **18** / 19 |       **52** / 53 |       **60** / 61 |       **82** / 83 |     **105** / 106 |     **430** / 431 |
| Hosts         |       **51** / 87 |      **98** / 172 |     **106** / 177 |     **137** / 215 |     **171** / 260 |     **643** / 743 |
| Scripts       |         **0** / 0 |     **159** / 201 |     **163** / 208 |     **196** / 259 |     **226** / 296 |     **495** / 575 |
| Cookies       |         **0** / 0 |        **9** / 50 |        **7** / 48 |       **18** / 78 |       **17** / 87 |     **224** / 313 |
| Net requests  |     **418** / 750 |    **663** /1,287 |   **615** / 1,224 |   **740** / 1,390 |   **804** / 1,510 | **1,757** / 2,505 |
| Bandwidth     |         9,846,856 |        18,016,101 |        17,645,598 |        19,989,297 |        18,944,959 |        23,437,021 |

### Notes
- _HTTPSB<sup>OOB</sup>_ means *HTTP Switchboard* with [out-of-the-box settings](https://github.com/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-block-allallow-exceptionally-approach).
- _HTTPSB<sup>AA/BX</sup>_ means *HTTP Switchboard* in [allow-all/block-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-allow-allblock-exceptionally-approach), with out-of-the-box preset blacklists.

### Methodology
Benchmarks were done using [*Browser session benchmark*](https://github.com/gorhill/sessbench). The script used is:
```
wait 3
repeat 5
clear cache
clear cookies
http://www.finance.yahoo.com/
http://www.money.msn.com/
http://www.money.cnn.com/
http://www.forbes.com/
http://www.wsj.com/
http://www.google.com/finance
http://www.bloomberg.com/
http://www.cnbc.com/
http://www.businessinsider.com/
http://www.fool.com/
http://www.marketwatch.com/
http://www.businessweek.com/
http://www.ibtimes.com/
http://www.ft.com/
http://www.seekingalpha.com/
```

List taken from [Top 15 Most Popular Business Websites | January 2014](http://www.ebizmba.com/articles/business-websites).