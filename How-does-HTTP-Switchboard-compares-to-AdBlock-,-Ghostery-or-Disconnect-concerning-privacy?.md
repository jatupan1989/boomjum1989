<sup>[Edit: added results for AdBlock+ on December 14th, 2013]</sup>

A whole lot of web sites pull resources from 3rd parties (examples: `themes.googleusercontent.com`, `cloudfront.net`) thus giving these 3rd parties log data telling them that one specific IP address has been visiting one specific website. If you are really concerned with privacy, you might not want that.

The results below are my findings, and they are published in the spirit of informed consent.

### Notes

A disctinct feature of *HTTP Switchboard* is that it is **also** a script blocker, like *NoScript* on *Firefox*. Other blockers listed here do not prevent the execution of inline javascript.

Now regarding privacy.

Blocking everything is not necessarily a good thing to everybody, as this might break web sites. Some users, less concerned with privacy, prefer to block minimally, others will prefer to pick themselves only what is necessary for a web page to just display properly. *HTTP Switchboard* allows both approach: although it comes out of the box with blocking by default and allowing exceptionally, you can with a single click allow everything by default and block exceptionally.

Keep in mind that *HTTP Switchboard*  is somewhat different than the two other extensions, which ones are based on a blacklist which is curated by their respective author. *HTTP Switchboard* blacklists come from [various selfless third-parties](/gorhill/httpswitchboard/wiki/Credits), are extensive, and aside that, you can still block whatever you want ultimately. Also, *HTTP Switchboard* is a javascript blocker (like [NoScript](http://noscript.net/)), a feature not found in the three other extensions.

### Methodology

- [AdBlock Plus](https://chrome.google.com/webstore/detail/adblock-plus-beta/cfhdojbkjhnklbpkdaibdccddilifddb)
    * version 1.6.1
    * Installed as per [EFF's advices to improve privacy](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online), including "EasyPrivacy" list (questionable advice given the results here).
- [Ghostery](https://chrome.google.com/webstore/detail/ghostery/mlomiejdfkolichcflejclcbmpeaniij) ("increasing the transparency of your browsing experience and giving you tools to control your privacy online")
    * version 5.0.0
    * "Block all", and nothing whitelisted.
- [Disconnect](https://chrome.google.com/webstore/detail/disconnect/jeoacafpbcihiomhlakheieifhpjdfeo) ("Disconnect lets you visualize & block the invisible websites that track you")
    * version 5.10.2
    * Everything is green (["Green = blocked. Grey = not blocked"](https://disconnect.me/disconnect/faq#why-are-some-icons-green-and-some-icons-grey)), and nothing whitelisted.
- [HTTP Switchboard](https://chrome.google.com/webstore/detail/http-switchboard/mghdpehejfekicfjcdbfofhcmnjhgaag)
    * version 0.6.6
    * Out of the box settings: images from everywhere except blacklisted hostnames allowed, all else blocked.
    * Domain of URL of web page whitelisted in the matrix.

Any of the above extension was the only one running at the time of the test, no conflict with another extension can be blamed for the results.

- Steps:
    * Browser cache was cleared.
    * Target web page was force-refreshed.
    * Data was pulled from the developer console, ignoring domain and subdomains matching URL of web page. (Since then I wrote [this tool](http://www.raymondhill.net/httpsb/har-parser.html) to quickly parse the results from the console.)
    * Only hostname is listed below, often many requests to same hostname, for various type of data (javascript, font, css, etc.)

### Reponses

I will insert here the responses of the owner/developer/etc. of Ghostery/Disconnect to the results below.

- Disconnect: [Response I got in a Hacker News discussion](https://news.ycombinator.com/item?id=6886072).

### Results

***

### A page on http://www.theguardian.com

Note: `*.guim.co.uk` not reported as a 3rd-party below, as key resources are pulled from this domain (stylesheets, etc.), which domain/subdomains required whitelisting in HTTPSB for the page to display properly (to meaningfully compare to Ghostery/Disconnect).

| Hostname                                | AdBlock+       | Ghostery       | Disconnect | HTTPSB |
| --------------------------------------- |:--------------:|:--------------:|:----------:|:------:|
| What is said to be blocked:             |                | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-2-ghostery.png) | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-2-disconnect.png) | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-2-httpsb.png) |
| 3rd parties which were **not** blocked: |                |                |            |        |
| `s.ophan.co.uk`                         | ✔              | ✔              | ✔          |        |
| `facebook-web-clients.appspot.com`      | ✔              | ✔              | ✔          |        |
| `guardian-notifications.appspot.com`    | ✔              | ✔              | ✔          |        |
| `related-info-hrd.appspot.com`          | ✔              | ✔              | ✔          |        |
| `static-serve.appspot.com`              | ✔              | ✔              | ✔          | ✔      |
| `cdnjs.cloudflare.com`                  | ✔              | ✔              | ✔          |        |
| `graph.facebook.com`                    | ✔              |                |            |        |
| `clients1.google.com`                   | ✔              |                |            |        |
| `www.google.com`                        | ✔              | ✔              |            |        |
| `ajax.googleapis.com`                   | ✔              | ✔              | ✔          |        |
| `discussion.guardianapis.com`           | ✔              | ✔              | ✔          |        |
| `p.jwpcdn.com`                          | ✔              |                |            |        |
| `platform.linkedin.com`                 | ✔              |                |            |        |
| `www.linkedin.com`                      | ✔              |                |            |        |
| `images.outbrain.com`                   | ✔              |                |            |        |
| `odb.outbrain.com`                      | ✔              |                |            |        |
| `widgets.outbrain.com`                  | ✔              |                |            |        |
| `platform.twitter.com`                  | ✔              | ✔              |            |        |
| `s-static.ak.facebook.com`              | ✔              |                |            |        |
| `static.ak.facebook.com`                | ✔              |                |            |        |
| `connect.facebook.net`                  | ✔              |                |            |        |
| `cdn.api.twitter.com`                   | ✔              |                |            |        |
| `s.c.lnkd.licdn.com`                    | ✔              |                |            |        |

<sub>Note: In the case of HTTPSB, there was a hit on `static-serve.appspot.com` because images are whitelisted by default when using out-of-the-box settings. But users can, if they choose so, block specifically `static-serve.appspot.com` with a single click in the matrix. This is not possible with Disconnect and Ghostery. It is possible with AdBlock+ if you don't mind [geeky stuff](https://adblockplus.org/en/filters).</sub>

***

### A page on http://www.wired.com/

| Hostname                                | AdBlock+       | Ghostery       | Disconnect | HTTPSB |
| --------------------------------------- |:--------------:|:--------------:|:----------:|:------:|
| What is said to be blocked:             |                | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-3-ghostery.png) | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-3-disconnect.png) | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-3-httpsb.png) |
| 3rd parties which were **not** blocked: |                |                |            |        |
| `www.adobetag.com`                      |                |                | ✔          |        |
| `admin.brightcove.com`                  | ✔              |                | ✔          |        |
| `dwgyu36up6iuz.cloudfront.net`          | ✔              | ✔              | ✔          |        |
| `dnkzzz1hlto79.cloudfront.net`          | ✔              | ✔              | ✔          |        |
| `condenastl3cdn.cust.footprint.net`     |                | ✔              | ✔          |        |
| `api.cnevids.com`                       |                | ✔              | ✔          |        |
| `player.cnevids.com`                    | ✔              | ✔              | ✔          |        |
| `fonts.condenast.com`                   | ✔              | ✔              | ✔          |        |
| `contextlysiteimages.contextly.com`     |                | ✔              | ✔          |        |
| `contextlysitescripts.contextly.com`    |                | ✔              | ✔          |        |
| `rest.contextly.com`                    |                | ✔              | ✔          |        |
| `disqus.com`                            | ✔              |                |            |        |
| `go.disqus.com`                         | ✔              |                |            |        |
| `juggler.services.disqus.com`           | ✔              |                |            |        |
| `realtime.services.disqus.com`          | ✔              |                |            |        |
| `wiredthreatlevel.disqus.com`           | ✔              |                |            |        |
| `a.disquscdn.com`                       | ✔              |                |            |        |
| `connect.facebook.net`                  | ✔              |                |            |        |
| `s-static.ak.facebook.com`              | ✔              |                |            |        |
| `static.ak.facebook.com`                | ✔              |                |            |        |
| `condenastl3cdn.cust.footprint.net`     | ✔              |                |            |        |
| `s.c.lnkd.licdn.com`                    | ✔              |                |            |        |
| `www.google-analytics.com`              | ✔              |                |            |        |
| `fonts.googleapis.com`                  |                |                | ✔          |        |
| `themes.googleusercontent.com`          |                | ✔              |            |        |
| `platform.linkedin.com`                 | ✔              |                |            |        |
| `www.linkedin.com`                      | ✔              |                |            |        |
| `a.mobify.com`                          |                |                | ✔          |        |
| `cdn.mxpnl.com`                         |                |                | ✔          |        |
| `images.outbrain.com`                   | ✔              |                |            |        |
| `odb.outbrain.com`                      | ✔              |                |            |        |
| `widgets.outbrain.com`                  | ✔              |                |            |        |
| `assets.pinterest.com`                  | ✔              |                |            |        |
| `passets.pinterest.com`                 | ✔              |                |            |        |
| `widgets.pinterest.com`                 | ✔              |                |            |        |
| `714015.ssl.cf2.rackcdn.com`            |                | ✔              |            |        |
| `widgets.twimg.com`                     | ✔              |                |            |        |
| `cdn.api.twitter.com`                   | ✔              |                |            |        |
| `platform.twitter.com`                  | ✔              | ✔              |            |        |
| `p.typekit.net`                         |                |                | ✔          |        |
| `www.webmonkey.com`                     | ✔              | ✔              | ✔          | ✔      |

<sub>Note: In the case of HTTPSB, there was a hit on `www.webmonkey.com` because images are whitelisted by default when using out-of-the-box settings. But users can, if they choose so, block specifically `www.webmonkey.com` with a single click in the matrix. This is not possible with Disconnect and Ghostery. It is possible with AdBlock+ if you don't mind [geeky stuff](https://adblockplus.org/en/filters).</sub>

***

### A page on http://www.businessinsider.com

| Hostname                                | AdBlock+       | Ghostery       | Disconnect | HTTPSB |
| --------------------------------------- |:--------------:|:--------------:|:----------:|:------:|
| 3rd parties which were **not** blocked: |                |                |            |        |
| `s-static.ak.facebook.com`              | ✔              |                |            |        |
| `static.ak.facebook.com`                | ✔              |                |            |        |
| `www.facebook.com`                      | ✔              |                |            |        |
| `connect.facebook.net`                  | ✔              |                |            |        |
| `static.ak.fbcdn.net`                   | ✔              |                |            |        |
| `ajax.googleapis.com`                   | ✔              |                |            |        |
| `code.jquery.com`                       | ✔              | ✔              | ✔          |        |
| `s.c.lnkd.licdn.com`                    | ✔              |                |            |        |
| `platform.linkedin.com`                 | ✔              |                |            |        |
| `www.linkedin.com`                      | ✔              |                |            |        |
| `player.ooyala.com`                     | ✔              | ✔              |            |        |
| `assets.pinterest.com`                  | ✔              |                |            |        |
| `widgets.pinterest.com`                 | ✔              |                |            |        |
| `buttons.reddit.com`                    | ✔              |                |            |        |
| `www.reddit.com`                        | ✔              |                |            |        |
| `ak.sail-horizon.com`                   | ✔              |                | ✔          |        |
| `cdn.sailthru.com`                      |                |                | ✔          |        |
| `cdn.stumble-upon.com`                  | ✔              |                |            |        |
| `badge.stumbleupon.com`                 | ✔              |                |            |        |
| `platform.stumbleupon.com`              | ✔              |                |            |        |
| `cdn.taboola.com`                       | ✔              | ✔              |            |        |
| `netstorage.taboola.com`                | ✔              | ✔              |            |        |
| `trc.taboola.com`                       | ✔              |                |            |        |
| `cdn.api.twitter.com`                   | ✔              |                |            |        |
| `platform.twitter.com`                  | ✔              |                |            |        |

***

### A page on http://www.nationaljournal.com/

| Hostname                                | AdBlock+       | Ghostery       | Disconnect | HTTPSB |
| --------------------------------------- |:--------------:|:--------------:|:----------:|:------:|
| 3rd parties which were **not** blocked: |                |                |            |        |
| `admin.brightcove.com`                  | ✔              |                |            |        |
| `www.facebook.com`                      | ✔              |                |            |        |
| `static.ak.fbcdn.net`                   | ✔              |                |            |        |
| `cdn.api.twitter.com`                   | ✔              |                |            |        |
| `platform.twitter.com`                  | ✔              |                |            |        |

***

### A page on http://www.upworthy.com

| Hostname                                | AdBlock+       | Ghostery       | Disconnect | HTTPSB |
| --------------------------------------- |:--------------:|:--------------:|:----------:|:------:|
| What is said to be blocked:             |                | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-1-ghostery.png) | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-1-disconnect.png) | [snapshot](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-1-httpsb.png) |
| 3rd parties which were **not** blocked: |                |                |            |        |
| `d8rk54i4mohrb.cloudfront.net`          |                | ✔              | ✔          |        |
| `www.facebook.com`                      | ✔              |                |            |        |
| `s-static.ak.facebook.com`              | ✔              |                |            |        |
| `static.ak.facebook.com`                | ✔              |                |            |        |
| `connect.facebook.net`                  | ✔              |                |            |        |
| `upw-prod-images.global.ssl.fastly.net` | ✔              | ✔              | ✔          | ✔      |
| `static.ak.fbcdn.net`                   | ✔              |                |            |        |
| `www.google.com`                        | ✔              | ✔              |            |        |
| `fonts.googleapis.com`                  | ✔              | ✔              | ✔          |        |
| `www.google-analytics.com`              | ✔              |                |            |        |
| `themes.googleusercontent.com`          | ✔              | ✔              |            |        |
| `cc.simplereach.com`                    |                |                | ✔          |        |
| `platform.twitter.com`                  | ✔              | ✔              |            |        |
| `www.youtube.com`                       | ✔              |                |            |        |
| `s.ytimg.com`                           | ✔              |                |            |        |

<sub>Note: In the case of HTTPSB, there was a hit on `upw-prod-images.global.ssl.fastly.net` because images are whitelisted by default when using out-of-the-box settings. But users can, if they choose so, block specifically `upw-prod-images.global.ssl.fastly.net` with a single click in the matrix. This is not possible with Disconnect and Ghostery. It is possible with AdBlock+ if you don't mind [geeky stuff](https://adblockplus.org/en/filters).</sub>