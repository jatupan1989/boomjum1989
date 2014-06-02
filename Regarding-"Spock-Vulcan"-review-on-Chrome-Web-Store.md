Someone nicknamed "Spock Vulcan" left this review in the Chrome Web Store:

> I hate to rate this so low, but as far as I could tell it didn't do anything besides add unnecessary delay to webpages. Each page's frame incurs a 200-1500ms delay before rendering/scripting begins. This makes pages take longer to initialize which subsequently affects network timing. (later note: even with settings disabled and blacklists removed, the browser is still impeded. Back to using /etc/hosts.)

This review is (suspiciously) pure nonsense. Everybody can find out by themselves. Here is the counter proof:

- Top screenshot is for HTTPSB in block-all/allow-exceptionally mode:
    * DOMContentLoaded = 304 ms. Number of net requests = 108.
- Middle screenshot is for HTTPSB in allow-block-exceptionally mode:
    * DOMContentLoaded = 1,114 ms. Number of net requests = 170.
- Bottom screenshot is without HTTPSB
    * DOMContentLoaded = 1,570 ms. Number of requests = 291.

![Wired timings](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/spock-vulcan-counterproof.png)

Click [here](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/spock-vulcan-counterproof.png) for image in its original size.

Browser cache was cleared before each test.

One thing is for sure: HTTPSB gives full information and control to users about what web pages are allowed to do. HTTPSB is free, comes with no strings attached and no agenda. HTTPSB is significantly more efficient memory- and CPU-wise than any other comparable blockers I've measured so far.

It's bound to annoy some people who make a living (directly or indirectly) off the bloat.