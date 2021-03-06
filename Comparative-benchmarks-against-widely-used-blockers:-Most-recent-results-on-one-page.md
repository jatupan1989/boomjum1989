The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user pushes data to more 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

The values are averages of aggregated results of the 15 web page visited over 5 runs. In the table, a result reported as "**_x_** / _n_" means "**_3rd-party count_** / _total count_".

The most important figure in my opinion with regard to privacy is the 3rd-party _Domain_ count, hence the ordering from left-to-right using the 3rd-party domain count figures.

Click on the links in the table for more details about a specific benchmark.

| &nbsp; | | | | | | |
| ------------- | -----------------:| -----------------:| -----------------:| -----------------:| -----------------:| -----------------:|
| [**Top 15 Most Popular<br> News Websites**](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites) |
|               | HTTPSB<sup>OOB</sup> | Ghostery          | Adblock+          | HTTPSB<sup>AA/BX</sup> | Disconnect        | No blocker        |
| Domains       |       **24** / 25 |       **54** / 55 |       **59** / 60 |       **69** / 70 |       **91** / 92 |     **476** / 477 |
| Hosts         |       **55** / 82 |     **109** / 183 |     **107** / 169 |     **126** / 200 |     **157** / 240 |     **693** / 785 |
| Scripts       |         **0** / 0 |     **176** / 307 |     **173** / 293 |     **187** / 327 |     **235** / 391 |     **534** / 698 |
| Cookies       |         **0** / 0 |        **4** / 54 |        **1** / 44 |       **10** / 73 |       **12** / 86 |     **299** / 389 |
| Net requests  |   **651** / 1,232 | **1,064** / 1,921 | **1,019** / 1,815 | **1,087** / 1,934 | **1,103** / 2,091 | **2,300** / 3,236 |
| Bandwidth     |        14,935,325 |        25,128,116 |        25,150,853 |        25,785,433 |        26,007,184 |        28,855,067 |
| &nbsp; |
| [**Top 15 Most Popular<br>Business Websites**](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Business-Websites) |||||||
|               | HTTPSB<sup>OOB</sup> | Ghostery          | Adblock+          | HTTPSB<sup>AA/BX</sup> | Disconnect        | No blocker        |
| Domains       |       **18** / 19 |       **52** / 53 |       **60** / 61 |       **82** / 83 |     **105** / 106 |     **430** / 431 |
| Hosts         |       **51** / 87 |      **98** / 172 |     **106** / 177 |     **137** / 215 |     **171** / 260 |     **643** / 743 |
| Scripts       |         **0** / 0 |     **159** / 201 |     **163** / 208 |     **196** / 259 |     **226** / 296 |     **495** / 575 |
| Cookies       |         **0** / 0 |        **9** / 50 |        **7** / 48 |       **18** / 78 |       **17** / 87 |     **224** / 313 |
| Net requests  |     **418** / 750 |    **663** /1,287 |   **615** / 1,224 |   **740** / 1,390 |   **804** / 1,510 | **1,757** / 2,505 |
| Bandwidth     |         9,846,856 |        18,016,101 |        17,645,598 |        19,989,297 |        18,944,959 |        23,437,021 |
| &nbsp; |
| [**Top 15 Most Popular<br>Tech & Gadget Websites**](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Tech-&-Gadget-Websites) |||||||
|               | HTTPSB<sup>OOB</sup> | Ghostery          | Adblock+          | HTTPSB<sup>AA/BX</sup> | Disconnect        | No blocker        |
| Domains       |       **26** / 27 |       **59** / 60 |       **66** / 67 |       **76** / 77 |       **85** / 86 |     **398** / 399 |
| Hosts         |       **37** / 69 |      **91** / 140 |      **97** / 146 |     **115** / 173 |     **145** / 203 |     **580** / 646 |
| Scripts       |         **0** / 0 |     **146** / 204 |     **151** / 208 |     **155** / 240 |     **194** / 262 |     **489** / 578 |
| Cookies       |         **0** / 0 |        **9** / 38 |        **6** / 25 |       **16** / 60 |       **17** / 58 |     **233** / 304 |
| Net requests  |     **309** / 710 |   **583** / 1,252 |   **583** / 1,233 |   **655** / 1,390 |   **671** / 1,370 | **1,737** / 2,494 |
| Bandwidth     |        19,801,676 |        30,769,246 |        30,340,281 |        31,174,355 |        30,895,419 |        33,826,528 |
| &nbsp; |
| [**Top 15 Most Popular<br>Blogs**](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-Blogs) |||||||
|               | HTTPSB<sup>OOB</sup> | Ghostery          | Adblock+          | HTTPSB<sup>AA/BX</sup> | Disconnect        | No blocker        |
| Domains       |       **32** / 33 |       **56** / 57 |       **72** / 73 |       **89** / 90 |       **89** / 90 |     **381** / 382 |
| Hosts         |       **36** / 71 |      **74** / 116 |      **91** / 142 |     **122** / 177 |     **144** / 188 |     **578** / 635 |
| Scripts       |         **0** / 0 |     **101** / 180 |     **129** / 200 |     **149** / 240 |     **163** / 231 |     **476** / 572 |
| Cookies       |         **0** / 0 |       **20** / 47 |       **17** / 41 |       **37** / 74 |       **32** / 58 |     **224** / 275 |
| Net requests  |     **369** / 711 |   **540** / 1,138 |   **588** / 1,168 |   **639** / 1,282 |   **647** / 1,234 | **1,573** / 2,236 |
| Bandwidth     |        30,365,916 |        37,611,873 |        38,043,172 |        38,366,098 |        37,856,378 |        42,021,162 |