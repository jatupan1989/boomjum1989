The results emphasize 3rd-party requests, as these are, I believe, a key statistics when it comes to gauge privacy matters. The rationale being that the more a user push data to more 3rd parties (a mere net request _is_ pushing data) -- typically without the user being aware -- the larger the footprint of leaked metadata. It is difficult for a user to appreciate how much metadata is leaked to 3rd parties when visiting a web page, as requests to 3rd-party agents are not easy to see, let alone easy to act upon. This is where _HTTP Switchboard_ will help you the most.

The values are averages of aggregated results of the 15 web page visited over 5 runs. In the table, a result reported as "**_x_** <sub>_n_</sub>" means "**_3rd-party count_** <sub>_total count_</sub>".

The most important figure in my opinion with regard to privacy is the 3rd-party _Domain_ count, hence the results are ordered from left-to-right according to the third-party domain count.

#### June 4, 2014

|              | HTTPSB<br>BA/AX               | HTTPSB<br>AA/BX               | Adblock                       | Adguard                       | Privacy<br>Badger               | No blocker                    |
| ------------ | -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:| -------------------------------:| -----------------------------:|
| Domains      |       **21**<br><sup>22</sup> |       **52**<br><sup>53</sup> |       **74**<br><sup>75</sup> |       **93**<br><sup>94</sup> |       **157**<br><sup>158</sup> |     **401**<br><sup>402</sup> |
| Hosts        |       **48**<br><sup>74</sup> |      **97**<br><sup>143</sup> |     **128**<br><sup>183</sup> |     **150**<br><sup>222</sup> |       **236**<br><sup>316</sup> |     **596**<br><sup>683</sup> |
| Scripts      |         **0**<br><sup>0</sup> |     **183**<br><sup>263</sup> |     **215**<br><sup>299</sup> |     **235**<br><sup>321</sup> |       **308**<br><sup>406</sup> |     **505**<br><sup>625</sup> |
| Cookies      |         **0**<br><sup>0</sup> |        **2**<br><sup>34</sup> |        **8**<br><sup>49</sup> |       **20**<br><sup>74</sup> |         **38**<br><sup>99</sup> |     **231**<br><sup>317</sup> |
| Net requests |   **625**<br><sup>1,217</sup> |   **879**<br><sup>1,653</sup> | **1,025**<br><sup>1,864</sup> | **1,044**<br><sup>1,911</sup> |   **1,144**<br><sup>2,021</sup> | **1,973**<br><sup>2,980</sup> |
| Bandwidth    |                    16,645,571 |                             ? |                    25,884,484 |                             ? |                               ? |                    29,375,024 |

<sup>**Note:** This time I primed Privacy Badger before the benchmark.</sup>

#### May 2, 2014

|              | HTTPSB<br>BA/AX               | Ghostery                      | Adblock+                      | HTTPSB<br>AA/BX               | Disconnect                    | Privacy<br>Badger              | No blocker                    |
| ------------ | -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:| ------------------------------:| -----------------------------:|
| Domains      |       **21**<br><sup>22</sup> |       **52**<br><sup>53</sup> |       **54**<br><sup>55</sup> |       **54**<br><sup>55</sup> |       **93**<br><sup>94</sup> |      **192**<br><sup>193</sup> |     **420**<br><sup>421</sup> |
| Hosts        |       **49**<br><sup>75</sup> |      **99**<br><sup>160</sup> |      **97**<br><sup>149</sup> |     **101**<br><sup>153</sup> |     **171**<br><sup>248</sup> |      **299**<br><sup>381</sup> |     **641**<br><sup>720</sup> |
| Scripts      |         **0**<br><sup>0</sup> |     **173**<br><sup>286</sup> |     **177**<br><sup>272</sup> |     **169**<br><sup>265</sup> |     **262**<br><sup>385</sup> |      **334**<br><sup>455</sup> |     **518**<br><sup>641</sup> |
| Cookies      |         **0**<br><sup>0</sup> |        **8**<br><sup>47</sup> |        **1**<br><sup>33</sup> |        **2**<br><sup>43</sup> |       **19**<br><sup>83</sup> |       **52**<br><sup>115</sup> |     **263**<br><sup>341</sup> |
| Net requests |   **680**<br><sup>1,199</sup> |   **966**<br><sup>1,722</sup> |   **913**<br><sup>1,612</sup> |   **930**<br><sup>1,648</sup> | **1,124**<br><sup>1,936</sup> |  **1,340**<br><sup>2,176</sup> | **2,079**<br><sup>2,849</sup> |
| Bandwidth    |                    15,147,576 |                    27,406,535 |                    26,489,990 |                    27,040,340 |                    28,758,904 |                              ? |                             ? |

<sup>Changes from previous benchmark: EFF-backed Privacy Badger (beta) added, see [these important notes](https://github.com/EFForg/privacybadgerfirefox/blob/master/README.md#how-heuristic-blocking-works), mostly, the results for Privacy Badger represent a worst-case scenario as the extension improves with usage (next benchmark I will prime it beforehand). Starting with [HTTP Switchboard version 0.8.6.4](/gorhill/httpswitchboard/wiki/Change-log#0864), Fanboy's specialized lists are not longer enabled by default.</sup>

#### February 26, 2014

|              | HTTPSB<br>BA/AX               | HTTPSB<br>AA/BX               | Ghostery                      | Adblock+                      | Disconnect                    | No blocker                    |
| ------------ | -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:|
| Domains      |       **21**<br><sup>22</sup> |       **45**<br><sup>46</sup> |       **48**<br><sup>49</sup> |       **53**<br><sup>54</sup> |       **87**<br><sup>88</sup> |     **412**<br><sup>413</sup> |
| Hosts        |       **49**<br><sup>78</sup> |      **89**<br><sup>142</sup> |      **98**<br><sup>165</sup> |      **96**<br><sup>152</sup> |     **153**<br><sup>232</sup> |     **609**<br><sup>697</sup> |
| Scripts      |         **0**<br><sup>0</sup> |     **171**<br><sup>282</sup> |     **176**<br><sup>291</sup> |     **175**<br><sup>280</sup> |     **252**<br><sup>392</sup> |     **525**<br><sup>677</sup> |
| Cookies      |         **0**<br><sup>0</sup> |        **3**<br><sup>43</sup> |        **5**<br><sup>48</sup> |        **2**<br><sup>35</sup> |       **16**<br><sup>85</sup> |     **231**<br><sup>316</sup> |
| Net requests |   **630**<br><sup>1,229</sup> |   **941**<br><sup>1,710</sup> |   **965**<br><sup>1,794</sup> |   **920**<br><sup>1,698</sup> | **1,063**<br><sup>2,018</sup> | **2,120**<br><sup>3,048</sup> |
| Bandwidth    |                    16,342,053 |                    26,603,582 |                    26,502,113 |                    26,714,512 |                    27,950,492 |                    31,282,722 |

<sup>Change from previous benchmark: Starting with HTTP Switchboard version 0.8.3.0, all preset lists of blocked hosts are enabled by default, except of for the huge "assets/thirdparties/hosts-file.net/hosts.txt". This allows HTTPSB in allow-all/block-exceptionally mode to perform well when compared to other blockers.</sup>

#### January 24, 2014

|              | HTTPSB<br>BA/AX               | Ghostery                      | Adblock+                      | HTTPSB<br>AA/BX               | Disconnect                    | No blocker                    |
| ------------ | -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:| -----------------------------:|
| Domains      |       **24**<br><sup>25</sup> |       **54**<br><sup>55</sup> |       **59**<br><sup>60</sup> |       **69**<br><sup>70</sup> |       **91**<br><sup>92</sup> |     **476**<br><sup>477</sup> |
| Hosts        |       **55**<br><sup>82</sup> |     **109**<br><sup>183</sup> |     **107**<br><sup>169</sup> |     **126**<br><sup>200</sup> |     **157**<br><sup>240</sup> |     **693**<br><sup>785</sup> |
| Scripts      |         **0**<br><sup>0</sup> |     **176**<br><sup>307</sup> |     **173**<br><sup>293</sup> |     **187**<br><sup>327</sup> |     **235**<br><sup>391</sup> |     **534**<br><sup>698</sup> |
| Cookies      |         **0**<br><sup>0</sup> |        **4**<br><sup>54</sup> |        **1**<br><sup>44</sup> |       **10**<br><sup>73</sup> |       **12**<br><sup>86</sup> |     **299**<br><sup>389</sup> |
| Net requests |   **651**<br><sup>1,232</sup> | **1,064**<br><sup>1,921</sup> | **1,019**<br><sup>1,815</sup> | **1,087**<br><sup>1,934</sup> | **1,103**<br><sup>2,091</sup> | **2,300**<br><sup>3,236</sup> |
| Bandwidth    |                    14,935,325 |                    25,128,116 |                    25,150,853 |                    25,785,433 |                    26,007,184 |                    28,855,067 |

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
