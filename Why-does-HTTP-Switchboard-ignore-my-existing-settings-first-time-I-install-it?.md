HTTP Switchboard will ignore all pre-existing javascript, plug-in and cookie exceptions you might have at the time you install the extension. Why?!

The javascript rules (aka "exceptions") built into Chromium/Chrome are very broad, and there is no way to make these broad built-in rules match HTTP Switchboard's more fine-grain approach. Here is an example:

Say you have javascript from `www.youtube.com` set to `allow` using Chromium/Chrome built-in javascript blocker. In reality, the built-in blocker will allow javascript from `www.youtube.com` (expected), but also javascript from all other origins which pulled scripts onto the page:

```
www.youtube.com/*
s.ytimg.com/*
apis.google.com/*
s0.doubleclick.net/*
s0.2mdn.net/*
ssl.google-analytics.com/*
```

Not all of these are really needed for the page to display and behave properly: some are required, some others are not. If HTTP Switchboard was to naively try to blindly copy your pre-existing rule to allow `www.youtube.com`, this would be the result:

```
www.youtube.com/*
```

And the page would **still** not work despite having transcribed your pre-existing rule into HTTP Switchboard, because for the page to properly display and behave, it also needs these two other rules:

```
google.com
ytimg.com
```

And there is no way for HTTP Switchboard to know this. So rather than pretend to do a good job at importing your pre-existing settings, HTTP Switchboard prefers to be honest: it can't import properly broad existing rules.

And this is why HTTP Switchboard encourages users to help each other through the *recipes* which can be easily imported/exported from the *Rule manager*.