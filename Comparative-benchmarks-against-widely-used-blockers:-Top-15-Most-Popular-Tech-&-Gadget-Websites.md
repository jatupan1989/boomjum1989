The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to more 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

The values are averages of aggregated results of the 15 web page visited over 5 runs. In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

The most important figure in my opinion with regard to privacy is the 3rd-party _Domain_ count.

#### January 24, 2014

|               | HTTPSB<sup>OOB</sup> | Ghostery          | Adblock+          | HTTPSB<sup>AA/BX</sup> | Disconnect        | No blocker        |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| -----------------:|
| Domains       |       **26** / 27 |       **59** / 60 |       **66** / 67 |       **76** / 77 |       **85** / 86 |     **398** / 399 |
| Hosts         |       **37** / 69 |      **91** / 140 |      **97** / 146 |     **115** / 173 |     **145** / 203 |     **580** / 646 |
| Scripts       |         **0** / 0 |     **146** / 204 |     **151** / 208 |     **155** / 240 |     **194** / 262 |     **489** / 578 |
| Cookies       |         **0** / 0 |        **9** / 38 |        **6** / 25 |       **16** / 60 |       **17** / 58 |     **233** / 304 |
| Net requests  |     **309** / 710 |   **583** / 1,252 |   **583** / 1,233 |   **655** / 1,390 |   **671** / 1,370 | **1,737** / 2,494 |
| Bandwidth     |        19,801,676 |        30,769,246 |        30,340,281 |        31,174,355 |        30,895,419 |        33,826,528 |

### See also
- [Top 15 Most Popular News Websites](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites)
- [Top 15 Most Popular Business Websites](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Business-Websites)
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
http://www.cnet.com/
http://www.yahoo.com/tech
http://www.theverge.com/
http://www.tomshardware.com/
http://www.gizmodo.com/
http://www.wired.com/
http://www.zdnet.com/
http://www.engadget.com/
http://www.digitaltrends.com/
http://www.techrepublic.com/
http://www.gizmag.com/
http://www.imore.com/
http://www.gsmarena.com/
http://www.geek.com/
http://www.anandtech.com/
```

List taken from [Top 15 Most Popular Tech & Gadget Websites | January 2014](http://www.ebizmba.com/articles/gadget-websites).