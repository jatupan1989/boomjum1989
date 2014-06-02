Someone nicknamed "Spock Vulcan" left this review in the Chrome Web Store:

> I hate to rate this so low, but as far as I could tell it didn't do anything besides add unnecessary delay to webpages. Each page's frame incurs a 200-1500ms delay before rendering/scripting begins. This makes pages take longer to initialize which subsequently affects network timing. (later note: even with settings disabled and blacklists removed, the browser is still impeded. Back to using /etc/hosts.)

I don't hate rating this review as (suspiciously) pure nonsense. Everybody can find out by themselves. Here is the counter proof:

- Top screenshot is for HTTPSB in block-all/allow-exceptionally mode: DOMContentLoaded = 304 ms
- Middle screenshot is for HTTPSB in allow-block-exceptionally mode: DOMContentLoaded = 1,114 ms
- Bottom screenshot is without HTTPSB: DOMContentLoaded = 1,570 ms

![Wired timings](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/spock-vulcan-counterproof.png)

Click [here](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/spock-vulcan-counterproof.png) for image in its original size.