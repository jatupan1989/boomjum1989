The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to more 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

The values are averages of aggregated results of the 15 web page visited over 5 runs. In the table, a result reported as "**_x_** <sub>_n_</sub>" means "**_3rd-party count_** <sub>_total count_</sub>".

The most important figure in my opinion with regard to privacy is the 3rd-party _Domain_ count, hence the results are ordered from left-to-right according to the third-party domain count.

#### June 4, 2014

|                         | HTTPSB<br>BA/AX            | HTTPSB<br>AA/BX            | Adblock                    | Adguard                    | Privacy<br>Badger            | No blocker                 |
| ----------------------- | --------------------------:| --------------------------:| --------------------------:| --------------------------:| ----------------------------:| --------------------------:|
| <sup>Domains</sup>      |       **21** <sub>22</sub> |       **52** <sub>53</sub> |       **74** <sub>75</sub> |       **93** <sub>94</sub> |       **157** <sub>158</sub> |     **401** <sub>402</sub> |
| <sup>Hosts</sup>        |       **48** <sub>74</sub> |      **97** <sub>143</sub> |     **128** <sub>183</sub> |     **150** <sub>222</sub> |       **236** <sub>316</sub> |     **596** <sub>683</sub> |
| <sup>Scripts</sup>      |         **0** <sub>0</sub> |     **183** <sub>263</sub> |     **215** <sub>299</sub> |     **235** <sub>321</sub> |       **308** <sub>406</sub> |     **505** <sub>625</sub> |
| <sup>Cookies</sup>      |         **0** <sub>0</sub> |        **2** <sub>34</sub> |        **8** <sub>49</sub> |       **20** <sub>74</sub> |         **38** <sub>99</sub> |     **231** <sub>317</sub> |
| <sup>Net requests</sup> |   **625** <sub>1,217</sub> |   **879** <sub>1,653</sub> | **1,025** <sub>1,864</sub> | **1,044** <sub>1,911</sub> |   **1,144** <sub>2,021</sub> | **1,973** <sub>2,980</sub> |
| <sup>Bandwidth</sup>    |                 16,645,571 |                          ? |                 25,884,484 |                          ? |                            ? |                 29,375,024 |

<sup>From now on I'm going to benchmark other blockers too. I will keep providing benchmarks for HTTPSB in _BA/AX_ and _AA/BX_ mode,
and _No blocker_ stats, so the results from these can be used as "anchors" to compare blockers across benchmarks. For example, with
the above results, I can say that using HTTPSB's results as anchors, [Ghostery](https://chrome.google.com/webstore/detail/ghostery/mlomiejdfkolichcflejclcbmpeaniij) and [Adblock Plus](https://chrome.google.com/webstore/detail/adblock-plus/cfhdojbkjhnklbpkdaibdccddilifddb) perform better privacy-wise than [Adblock](https://chrome.google.com/webstore/detail/adblock/gighmmpiobklfepjocnamgkkbiglidom),
[Adguard AdBlocker](https://chrome.google.com/webstore/detail/adguard-adblocker/bgnkhhnnamicmpeenaelnjfhikgbkllg) and
[Privacy Badger](https://chrome.google.com/webstore/detail/privacy-badger/pkehgijcmpdhfbdbbnkijodmdjhbjlgp).
**Note:** This time I primed Privacy Badger before the benchmark.</sup>

#### May 2, 2014

|                         | HTTPSB<br>BA/AX            | Ghostery                   | Adblock+                   | HTTPSB<br>AA/BX            | Disconnect                 | Privacy<br>Badger                 | No blocker                 |
| ----------------------- | --------------------------:| --------------------------:| --------------------------:| --------------------------:| --------------------------:| ---------------------------------:| --------------------------:|
| <sup>Domains</sup>      |       **21** <sub>22</sub> |       **52** <sub>53</sub> |       **54** <sub>55</sub> |       **54** <sub>55</sub> |       **93** <sub>94</sub> |            **192** <sub>193</sub> |     **420** <sub>421</sub> |
| <sup>Hosts</sup>        |       **49** <sub>75</sub> |      **99** <sub>160</sub> |      **97** <sub>149</sub> |     **101** <sub>153</sub> |     **171** <sub>248</sub> |            **299** <sub>381</sub> |     **641** <sub>720</sub> |
| <sup>Scripts</sup>      |         **0** <sub>0</sub> |     **173** <sub>286</sub> |     **177** <sub>272</sub> |     **169** <sub>265</sub> |     **262** <sub>385</sub> |            **334** <sub>455</sub> |     **518** <sub>641</sub> |
| <sup>Cookies</sup>      |         **0** <sub>0</sub> |        **8** <sub>47</sub> |        **1** <sub>33</sub> |        **2** <sub>43</sub> |       **19** <sub>83</sub> |             **52** <sub>115</sub> |     **263** <sub>341</sub> |
| <sup>Net requests</sup> |   **680** <sub>1,199</sub> |   **966** <sub>1,722</sub> |   **913** <sub>1,612</sub> |   **930** <sub>1,648</sub> | **1,124** <sub>1,936</sub> |        **1,340** <sub>2,176</sub> | **2,079** <sub>2,849</sub> |
| <sup>Bandwidth</sup>    |                 15,147,576 |                 27,406,535 |                 26,489,990 |                 27,040,340 |                 28,758,904 |                                 ? |                          ? |

<sup>Changes from previous benchmark: EFF-backed Privacy Badger (beta) added, see [these important notes](https://github.com/EFForg/privacybadgerfirefox/blob/master/README.md#how-heuristic-blocking-works), mostly, the results for Privacy Badger represent a worst-case scenario as the extension improves with usage (next benchmark I will prime it beforehand). Starting with [HTTP Switchboard version 0.8.6.4](/gorhill/httpswitchboard/wiki/Change-log#0864), Fanboy's specialized lists are not longer enabled by default.</sup>

#### February 26, 2014

|                         | HTTPSB<br>BA/AX            | HTTPSB<br>AA/BX            | Ghostery                   | Adblock+                   | Disconnect                 | No blocker                 |
| ----------------------- | --------------------------:| --------------------------:| --------------------------:| --------------------------:| --------------------------:| --------------------------:|
| <sup>Domains</sup>      |       **21** <sub>22</sub> |       **45** <sub>46</sub> |       **48** <sub>49</sub> |       **53** <sub>54</sub> |       **87** <sub>88</sub> |     **412** <sub>413</sub> |
| <sup>Hosts</sup>        |       **49** <sub>78</sub> |      **89** <sub>142</sub> |      **98** <sub>165</sub> |      **96** <sub>152</sub> |     **153** <sub>232</sub> |     **609** <sub>697</sub> |
| <sup>Scripts</sup>      |         **0** <sub>0</sub> |     **171** <sub>282</sub> |     **176** <sub>291</sub> |     **175** <sub>280</sub> |     **252** <sub>392</sub> |     **525** <sub>677</sub> |
| <sup>Cookies</sup>      |         **0** <sub>0</sub> |        **3** <sub>43</sub> |        **5** <sub>48</sub> |        **2** <sub>35</sub> |       **16** <sub>85</sub> |     **231** <sub>316</sub> |
| <sup>Net requests</sup> |   **630** <sub>1,229</sub> |   **941** <sub>1,710</sub> |   **965** <sub>1,794</sub> |   **920** <sub>1,698</sub> | **1,063** <sub>2,018</sub> | **2,120** <sub>3,048</sub> |
| <sup>Bandwidth</sup>    |                 16,342,053 |                 26,603,582 |                 26,502,113 |                 26,714,512 |                 27,950,492 |                 31,282,722 |

<sup>Change from previous benchmark: Starting with HTTP Switchboard version 0.8.3.0, all preset lists of blocked hosts are enabled by default, except of for the huge "assets/thirdparties/hosts-file.net/hosts.txt". This allows HTTPSB in allow-all/block-exceptionally mode to perform well when compared to other blockers.</sup>

#### January 24, 2014

|                         | HTTPSB<br>BA/AX            | Ghostery                   | Adblock+                   | HTTPSB<br>AA/BX            | Disconnect                 | No blocker                 |
| ----------------------- | --------------------------:| --------------------------:| --------------------------:| --------------------------:| --------------------------:| --------------------------:|
| <sup>Domains</sup>      |       **24** <sub>25</sub> |       **54** <sub>55</sub> |       **59** <sub>60</sub> |       **69** <sub>70</sub> |       **91** <sub>92</sub> |     **476** <sub>477</sub> |
| <sup>Hosts</sup>        |       **55** <sub>82</sub> |     **109** <sub>183</sub> |     **107** <sub>169</sub> |     **126** <sub>200</sub> |     **157** <sub>240</sub> |     **693** <sub>785</sub> |
| <sup>Scripts</sup>      |         **0** <sub>0</sub> |     **176** <sub>307</sub> |     **173** <sub>293</sub> |     **187** <sub>327</sub> |     **235** <sub>391</sub> |     **534** <sub>698</sub> |
| <sup>Cookies</sup>      |         **0** <sub>0</sub> |        **4** <sub>54</sub> |        **1** <sub>44</sub> |       **10** <sub>73</sub> |       **12** <sub>86</sub> |     **299** <sub>389</sub> |
| <sup>Net requests</sup> |   **651** <sub>1,232</sub> | **1,064** <sub>1,921</sub> | **1,019** <sub>1,815</sub> | **1,087** <sub>1,934</sub> | **1,103** <sub>2,091</sub> | **2,300** <sub>3,236</sub> |
| <sup>Bandwidth</sup>    |                 14,935,325 |                 25,128,116 |                 25,150,853 |                 25,785,433 |                 26,007,184 |                 28,855,067 |

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
