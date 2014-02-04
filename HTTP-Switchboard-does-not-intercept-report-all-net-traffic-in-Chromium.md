_HTTP Switchboard_ uses the [chrome.webRequest](http://developer.chrome.com/extensions/webRequest.html) to filter/report net requests. However, anything which is not passed to the above API by your Chromium-based browser can not be filtered/reported by HTTPSB.

So what are requests which are not passed to HTTPSB?

So far this is what has been found on Chromium Version 31.0.1650.63 Built on Ubuntu 13.04, running on LinuxMint 15:

- At launch:
    translate.googleapis.com
    googleapis.l.google.com
    qe-in-f95.1e100.net