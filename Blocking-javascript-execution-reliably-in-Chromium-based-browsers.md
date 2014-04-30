_[This was meant for a [post on Hacker News](https://news.ycombinator.com/item?id=7673741), but posted here because a HN post is limited to 2000 characters, and I didn't want to truncate the text]_

There is an unfortunate myth still going on out there which can be resumed as follow:

> It is not possible to reliably block javascript execution in [Chromium-based browser]

I disagree.

## The myth

Unfortunately, more often than not, my attempts at explaining that it is indeed possible to block javascript execution reliably in a Chromium-based browser are quickly dismissed with no visible attempts, from my point of view, to really understand how it works, so that there can be a genuine assessment of how reliable it is.

Months ago, I unexpectedly found myself writing an extension for Chromium to enhance security. Nothing was planned, it just happened after I started hacking with the API "just to see" how all this worked.

It's called HTTP Switchboard [1], and as I entertain the idea of slapping "v1.0" on it at this point, I am still faced with the myth "[Chromium-based browser] can't reliably block javascript".

Given the huge amount of hours I dedicated to this project, I have to admit that it does sadden me to see such a myth unfairly undermining my work.

The purpose of this post is my attempt to dispel this particular myth. Honestly, I don't think I will really dispel the myth, but I can't help but give it a try.

## The problem

Other javascript blockers on Chromium-based browsers typically rely on the `chrome.contentSettings.javascript` API to block or allow execution of javascript for a given web page. [2]

This particular API is unreliable, because as per chrome API documentation, "[unless] the doc says otherwise, methods in the chrome.* APIs are asynchronous". [3]

This means that when an extension calls, say, `chrome.contentSettings.javascript.set([rule])` to block or allow javascript execution, the rule passed to the API call will take effect *at some point in the future*, and this future could be *after* the web page has loaded, *after* the page has been parsed, and *after* inline javascript has been executed.

There is just no guarantee as to when the rule will take effect.

Early in the development of my extension, this is also how I tried to block inline javascript execution, and this was causing ugly issues. [4]

Asynchronous is a good thing, but in this particular, narrow case, it is definitely not.

## The solution

I spent long hours to try and figure what could be done. Wrote quite a lot of prototype code, which I always had to throw.

Eventually, one prototype worked.

In retrospect, this seems an obvious solution, but I guess it is not *that* obvious since so far I haven't seen the mechanism used elsewhere.

There are only three places (which I know of so far) in the chrome API where code can be (optionally) executed in a synchronous ("blocking") manner:

In the `chrome.webRequest.onBeforeRequest`, `chrome.webRequest.onBeforeSendHeaders`, and `chrome.webRequest.onHeadersReceived` event handlers. [5]

Thus the solution was to create a `chrome.webRequest.onHeadersReceived` event handler which would inject a `Content-Security-Policy` header with the directive `"script-src 'none'"`.

It just works:

![HTTPSB can block reliably](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-can-block-reliably.png)

The event handler is executed in a synchronous manner, and Chromium-based browsers have supported the `Content-Security-Policy` header since a while now. [6]

After having spent so much time to try to find a solution, it was a marvelous moment when I finally realized this solved the thorny issue of blocking javascript reliably.

It works so well, I wouldn't be surprised to see the same approach adopted by other javascript blockers written for Chromium-based browsers in the future.

## The exception: Data URI

In Chromium-based browsers, loading a data URI in the address bar doesn't result in HTTP headers being received through a `chrome.webRequest.onHeadersReceived` event handler, therefore no `Content-Security-Policy "script-src 'none'"` header can be injected, thus inline javascript cannot be disabled for data URIs. [7]

(But this is not the case brought forth by the majority of people arguing that javascript cannot be reliably blocked in a Chromium-based browser.)

Now, I just want to emphasize that data URIs for Chromium-based browsers are treated quite differently than other browsers:

In a Chromium-based browser, a data URI *is its own unique origin*, and as per Chromium developers, "they don't have access to cookies or other resources belonging to their parent".

Furthermore, if my extension is present, external resources referenced in a data URI, and which are not whitelisted won't be allowed to load.

This mitigates *significantly* the execution of javascript code in a data URI, and I do not consider this enough of an issue to for my work to deserve the "unreliable" tag.

## References

- [1] <https://github.com/gorhill/httpswitchboard#http-switchboard-for-chromium>
- [2] <https://developer.chrome.com/extensions/contentSettings>
- [3] <https://developer.chrome.com/extensions/api_index#conventions>
- [4] <https://github.com/gorhill/httpswitchboard/issues/35>
- [5] <https://developer.chrome.com/extensions/webRequest>
- [6] <http://caniuse.com/contentsecuritypolicy>
- [7] <http://forums.informaction.com/viewtopic.php?f=8&t=7020&start=30#p68784>