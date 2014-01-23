Notes:
- "HTTPSB OOB" means *HTTP Switchboard* with out-of-the-box settings.
- "HTTPSB AA/BX" means *HTTP Switchboard* in allow-all/block-exceptionally mode, with out-of-the-box preset blacklists.
- "Adblock+" means [*Adblock Plus*](https://adblockplus.org/).
- Both HTTPSB and Adblock+ were set to use *Fanboy Complete List*.
- [Ghostery](http://www.ghostery.com/) and [Disconnect](https://disconnect.me/) were set in their respective equivalent of "Block all trackers" mode.
- The latest version of all blockers was used on the day of the benchmark.
- "Cookies" means outbound cookies, i.e. cookies reaching a remote host. These are the cookies which really matter with regard to privacy.
- Keep in mind:
    * A user can not add/remove filters from Ghostery and Disconnect.
    * A user can add/remove filters from HTTPSB and Adblock+. Where these two differ:
        - How easy it is to add/remove filters: Adblock+ = geeky, HTTPSB = easy.
        - The granularity of their filters: Adblock+ = finer grained, HTTPSB = hostname/type of request.
- HTTPSB, Adblock+ and Disconnect are all [GPL](http://en.wikipedia.org/wiki/GNU_General_Public_License).

#### January 22, 2014
 | HTTPSB OOB | Adblock+ | Ghostery | HTTPSB AA/BX | Disconnect | No blocker
--- | ---:| ---:| ---:| ---:| ---:| ---:
Bandwidth | 16,018,841 | 12,049,602 | 21,609,353 | 21,858,245 | 22,756,202 | 26,020,235
Requests allowed<br>(network + cache) | 1,293<br>(1,290 + 3) | 993<br>(983 + 10) | 1,781<br>(1,771 + 10) | 1,831<br>(1,798 + 33) | 1,972<br>(1,949 + 24) | 2,925<br>(2,788 + 137)
Hosts: **3rd-party** / all | **53** / 80 | **76** / 118 | **97** / 158 | **110** / 167 | **174** / 282 | **198** / 324 | **525** / 597
Scripts: **3rd party** / all | **0** / 0 | **121** / 204 | **150** / 256 | **174** / 282 | **198** / 324 | **524** / 670
Cookies: **3rd party** / all | **0** / 0 | **3** / 26 | **9** / 46 | **16** / 62 | **15** / 75 | **212** / 277