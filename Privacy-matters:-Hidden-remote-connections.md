_HTTP Switchboard_ uses the [chrome.webRequest API](http://developer.chrome.com/extensions/webRequest.html) to filter/report net requests. However, anything which is not passed to the above API by your Chromium-based browser can not be filtered/reported by HTTPSB.

These requests are not merely behind-the-scene (which are reported by HTTPSB), they are also unavailable to extensions, which means it is even more difficult for a user to be aware of these. So here are lists of all the connections which have been found to be hidden from user view, i.e. which can not be reported as behind-the-scene requests by HTTPSB, and therefore can not be filtered through HTTPSB.

The remote connections were collated after having disabled **everything** which can be reasonably disabled by a user in order to prevent as much those hidden remote connections. Only the `about:blank` page was opened after browser was launched, and only HTTPSB extension installed locally was present.

### Chromium 31 / Linux

At start:

```
[gibberish].1e100.net         # seems to correspond to "clients[?].google.com"
translate.googleapis.com
```
### Chrome 32 / Windows

At start, and then regularly:

```
[gibberish].1e100.net         # seems to correspond to "clients[?].google.com"
```

Apparently, the above `clients[?].google.com` hostname translates into `[gibberish].1e100.net` utlimately. `1e100.net` is Google.

### Opera 19 / Windows

Always at start:
```
autoupdate.opera.com
```

Sometimes at start (related to "_Settings_/_Start page_/_Preload Discover contents_"?):
```
[gibberish].jfk1.r.cloudfront.net:49504
```

Sometimes at start but less often, seemingly related to "_Settings_/_Search_/_Manage search engines..._":
```
[gibberish].1e100.net         # google.com
origin.any.bing.com
205.251.242.54                # amazon.com
[gibberish].yahoo.com
```
