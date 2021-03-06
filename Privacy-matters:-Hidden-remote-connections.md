_HTTP Switchboard_ uses the [chrome.webRequest API](http://developer.chrome.com/extensions/webRequest.html) to filter/report net requests. However, anything which is not passed to the above API by your Chromium-based browser can not be filtered/reported by HTTPSB.

These requests are not merely behind-the-scene (which are reported by HTTPSB), they are also unavailable to extensions, which means it is even more difficult for a user to be aware of these. So here are lists of all the connections which have been found to be hidden from user view, i.e. which can not be reported as behind-the-scene requests by HTTPSB, and therefore can not be filtered through HTTPSB.

The remote connections were collated after having disabled **everything** which can be reasonably disabled by a user in order to prevent as much those hidden remote connections. Only the `about:blank` page was opened after browser was launched, and only HTTPSB extension installed locally was present.

**TODO** Evaluate the use of the following [command-line switches](http://peter.sh/experiments/chromium-command-line-switches/):
- `--host-rules` [desc](http://peter.sh/experiments/chromium-command-line-switches/#host-rules)
- `--disable-background-networking` [desc](http://peter.sh/experiments/chromium-command-line-switches/#disable-background-networking)
    * "The following systems are disabled via this flag: IntranetRedirectDetector (requests randomURLs 2-5s after startup); GoogleUrlTracker (searchdomaincheck); SafeBrowsing updater; Extension updater" [(ref)](https://codereview.chromium.org/3312014) [(thanks!)](http://www.wilderssecurity.com/threads/wanted-an-assessment-of-tactics-against-privacy-invasions-by-chrome-browser.362914/page-2#post-2364193)
- `--disable-component-extensions-with-background-pages` [desc](http://peter.sh/experiments/chromium-command-line-switches/#disable-component-extensions-with-background-pages) (I still need to figure what this does _exactly_, but it _seems_ this got rid of that _Hangout Services_ thing sometimes showing up in the Task manager (need to confirm this though when time allows).

### Chromium 31 + HTTPSB / Linux

At start, and then regularly:

```
[gibberish].1e100.net         # seems to correspond to "clients[?].google.com"
```

At start, if "_Settings_/_Languages_/_Offer to translate pages that..._" is enabled:
```
translate.googleapis.com
```

When visiting the "_Settings_" page, regardless of whether "_Settings_/_Languages_/_Offer to translate pages that..._" is enabled or disabled:
```
translate.googleapis.com
```

[Chrome developer on reddit](http://www.reddit.com/r/chrome/comments/1xsxjv/best_browser_google_chrome_vs_chromium/cff4ec8): "Chromium does extension updates, yes ... I see `translate.googleapis.com` in the code too. I'm not 100% sure so I filed a bug and assigned it to the right people."

### Chrome 32 + HTTPSB / Windows

At start, and then regularly:

```
[gibberish].1e100.net         # seems to correspond to "clients[?].google.com"
```

At start, if "_Settings_/_Languages_/_Offer to translate pages that aren't in a language that I read_" is enabled:
```
translate.googleapis.com
```

When visiting the "_Settings_" page, regardless of whether "_Settings_/_Languages_/_Offer to translate pages that..._" is enabled or disabled:
```
translate.googleapis.com
```

### Opera 19 + HTTPSB / Windows

At start:
```
autoupdate.geo.opera.com
```

Sometimes at start (might be related to above `autoupdate.geo.opera.com`):
```
[gibberish].cloudfront.net
```

Sometimes at start but less often, seemingly related to "_Settings_/_Search_/_Manage search engines..._":
```
[gibberish].1e100.net         # google.com
origin.any.bing.com
205.251.242.54                # amazon.com
[gibberish].yahoo.com
```

### Firefox 26 + NoScript / Linux

For reference purpose.

At start:
```
ocsp.godaddy.com.akadns.net
secure.informaction.com
```