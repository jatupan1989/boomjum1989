The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to more 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

The values are averages of aggregated results of the 15 web page visited over 5 runs. In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

The most important figure in my opinion with regard to privacy is the 3rd-party _Domain_ count.

#### January 24, 2014

|               | HTTPSB<sup>OOB</sup> | Ghostery          | Adblock+          | HTTPSB<sup>AA/BX</sup> | Disconnect        | No blocker        |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| -----------------:|
| Domains       |       **32** / 33 |       **56** / 57 |       **72** / 73 |       **89** / 90 |       **89** / 90 |     **381** / 382 |
| Hosts         |       **36** / 71 |      **74** / 116 |      **91** / 142 |     **122** / 177 |     **144** / 188 |     **578** / 635 |
| Scripts       |         **0** / 0 |     **101** / 180 |     **129** / 200 |     **149** / 240 |     **163** / 231 |     **476** / 572 |
| Cookies       |         **0** / 0 |       **20** / 47 |       **17** / 41 |       **37** / 74 |       **32** / 58 |     **224** / 275 |
| Net requests  |     **369** / 711 |   **540** / 1,138 |   **588** / 1,168 |   **639** / 1,282 |   **647** / 1,234 | **1,573** / 2,236 |
| Bandwidth     |        30,365,916 |        37,611,873 |        38,043,172 |        38,366,098 |        37,856,378 |        42,021,162 |

### See also
- [Top 15 Most Popular News Websites](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites)
- [Top 15 Most Popular Business Websites](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Business-Websites)
- [Top 15 Most Popular Tech & Gadget Websites](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Tech-&-Gadget-Websites)
- [Methodology and notes](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Methodology-and-notes)

### Notes
- _HTTPSB<sup>OOB</sup>_ means *HTTP Switchboard* with [out-of-the-box settings](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-block-allallow-exceptionally-approach).
- _HTTPSB<sup>AA/BX</sup>_ means *HTTP Switchboard* in [allow-all/block-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-allow-allblock-exceptionally-approach), with out-of-the-box preset blacklists.

### Methodology
Benchmarks were done using [*Browser session benchmark*](https://github.com/gorhill/sessbench). The script used is:
```
wait 3
repeat 5
clear cache
clear cookies
http://www.huffingtonpost.com/
http://www.tmz.com/
http://www.businessinsider.com/
http://www.gawker.com/
http://www.lifehacker.com/
http://www.mashable.com/
http://www.gizmodo.com/
http://www.thedailybeast.com/
http://www.perezhilton.com/
http://www.techcrunch.com/
http://www.cheezburger.com/
http://www.jezebel.com/
http://www.deadspin.com/
http://www.engadget.com/
http://www.kotaku.com/
```

List taken from [Top 15 Most Popular Blogs | January 2014](http://www.ebizmba.com/articles/blogs).