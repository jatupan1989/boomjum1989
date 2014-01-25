### Methodology

Benchmarks were done using [*Browser session benchmark*](https://github.com/gorhill/sessbench).

- The benchmarks are run on Chromium Linux Mint 64-bit. Any Chromium-based browser should be able to run it though.
- Adblock+:
    * _Allow some non-intrusive advertising_ was disabled
    * Filter lists used:
        - [EasyList](https://easylist-downloads.adblockplus.org/easylist.txt)
        - [Fanboy+Easylist-Merged Ultimate List](http://www.fanboy.co.nz/filters.html)
- HTTPSB<sup>OOB</sup> and HTTPSB<sup>AA/BX</sup>:
    * Blacklists used:
        - Out-of-the-box blacklists
        - [Fanboy+Easylist-Merged Ultimate List](http://www.fanboy.co.nz/filters.html)
            * HTTPSB uses _only_ the blacklisted domain filters from that list, the rest is entirely ignored.
- [Ghostery](http://www.ghostery.com/) and [Disconnect](https://disconnect.me/) were set in their respective equivalent of "Block all trackers" mode.
- The latest version of all blockers was used on the day of the benchmark.
- Chrome *Settings* / *Privacy* / *Content Settings* / *Plug-ins* => "Click to play" was selected.
- Chrome *Settings* / *Privacy* / *Content Settings* / *JavaScript* => "Allow all sites to run JavaScript" was selected.

### Notes (unsorted)

"Adblock+" means [*Adblock Plus*](https://adblockplus.org/).

"3rd-party" in the strictest sense, meanings if the domain name of a request differs from the domain of a page URL address, the request is deemed 3rd-party.

"Cookies" means outbound cookies, i.e. cookies reaching a remote host. These are the cookies which really matter with regard to privacy.

Keep in mind:
- A user can not add new filters in Ghostery or Disconnect.
    * Correct me if I am wrong.
- A user can add new filters in HTTPSB and Adblock+. Where these two differ:
    * How easy it is to add/remove filters: Adblock+ = [geeky](https://adblockplus.org/en/filters), HTTPSB = easy (just click on a cell in the matrix).
    * The granularity of their filters: Adblock+ = coarse- to fine-grained, HTTPSB = hostname/type of request (firewall-like).
    * With Adblock+ it is not possible to completely block *all* requests to an entire web site (see [Why was "Site blocking" removed?](https://web.archive.org/web/20111206122411/https://adblockplus.org/en/faq_features#siteblock)), meaning that even if you create an Adblock filter to block, say, `evil.com`, there will still be a request made to `evil.com` if you try to open a web page from `evil.com`.
    * Adblock doesn't prevent the execution of inline javascript.
    * HTTPSB<sup>OOB</sup> breaks a lot of sites, because it allows only images and stylesheets, and block everything else (javascript, cookies, etc.)

I will repeat the benchmark once in a while and add results here in order to show consistentcy of results over time.
- Keep in mind contents of benchmarked web pages will obviously change, so results are meaningful when compared to each other within the same benchmark.