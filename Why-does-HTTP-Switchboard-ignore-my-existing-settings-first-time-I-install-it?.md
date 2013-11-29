*HTTP Switchboard* ("HTTPSB") will ignore all pre-existing javascript, plug-in and cookie exceptions you might have at the time you install the extension. Why?!

The javascript rules (aka "exceptions") built into Chromium/Chrome are very broad, and there is no way to make these broad built-in rules match HTTPSB's more fine-grain approach. Here is an example:

Say you have javascript from `www.youtube.com` set to `allow` using Chromium/Chrome built-in javascript blocker. In reality, the built-in blocker will allow javascript from `www.youtube.com` (expected), but also javascript from all other origins which pulled scripts onto the page:

```
www.youtube.com/*
s.ytimg.com/*
apis.google.com/*
s0.doubleclick.net/*
s0.2mdn.net/*
ssl.google-analytics.com/*
```

Not all of these are really needed for the page to display and behave properly: some are required, some others are not. If HTTPSB was to naively try to blindly copy your pre-existing rules to allow `www.youtube.com`, this would be the result:

```
www.youtube.com/*
```

And the page would **still** not work despite having transcribed your pre-existing rule into HTTPSB, because for the page to properly display and behave, it also needs these two other rules:

```
google.com/*
ytimg.com/*
```

And there is no way for HTTPSB to know this. So rather than pretend to do a good job at importing your pre-existing settings, HTTPSB prefers to be straightforward: it can't import properly Chromium/Chrome's overly broad rules.

And this is why HTTPSB encourages users to help each other through the *recipes* which can be easily imported/exported from the *Rule manager*. I've posted a couple of these recipes in the [Google group](https://groups.google.com/forum/?hl=en#!forum/httpsb), and I will try to assist as much as I can if you need help into identifying the minimal set of rules necessary to make a web page works properly.

**Edit:** I gave more thought on this, and there is a way I could make Chromium/Chrome broad rules fit fine-grained HTTPSB: by using per-page permissions. Example: User has existing Chromium/Chrome rule to allow `www.youtube.com`, thus HTTPSB would create the following page-scoped rule:

```
https://www,youtube.com
    * *
```