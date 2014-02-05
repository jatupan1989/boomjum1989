_HTTP Switchboard_ uses the [chrome.webRequest API](http://developer.chrome.com/extensions/webRequest.html) to filter/report net requests. However, anything which is not passed to the above API by your Chromium-based browser can not be filtered/reported by HTTPSB.

These requests are not merely behind-the-scene (which are reported by HTTPSB), they are also unavailable to extensions, which means it is even more difficult for a user to be aware of these. So here are lists of all the connections which have been found to be hidden from user view, i.e. which can't even be reported as behind-the-scene requests by HTTPSB.

The remote connections were collated after having disabled **everything** which can be reasonably disabled by a user in order to prevent as much those hidden remote connections. Only the `about:blank` page was opened after browser was launched, and only HTTPSB extension installed locally was present.

### Chromium 31 / Linux

[list of remote servers]

### Chrome 32 / Windows

At start, and then regularly:

```
[gibberish].1e100.net         # seems to correspond to "clients[?].google.com"
```

Apparently, the above `clients[?].google.com` hostname translates into `[gibberish].1e100.net` utlimately. `1e100.net` is Google.

### Opera 19 / Windows

#### "Preload Discover contents" enabled

At start:
```
[gibberish].1e100.net
origin.any.bing.com
205.251.242.54                # amazon.com
[gibberish].yahoo.com
[gibberish].cloudfront.net
```

#### "Preload Discover contents" disabled

At start:
```
updates.opera.com
```
