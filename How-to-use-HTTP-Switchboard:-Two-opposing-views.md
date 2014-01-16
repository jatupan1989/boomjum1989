There are two main ways to use *HTTP Switchboard* ("HTTPSB"), and then there is everything in between and beyond. Basically: your choice.

One important thing to remember though, whatever the approach you use, the preset lists of blocked hosts can still be used to block the ad servers, trackers, malware, nuisance, etc. of the internet.

## The block-all/allow-exceptionally approach

![block-all/allow-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-basics-block-all-by-default.gif)

This is the out-of-the-box settings:
- All is blocked by default (through the blacklisting of the `all` cell).
- CSS and images are whitelisted.
- Frames are blacklisted.
- Preset blocked hosts are blacklisted.

Advantages:
- Security is greatly enhanced.
- Privacy is greatly enhanced.
- Use less network bandwidth (web pages download faster)

Disadvantages:
- Web pages are less likely to render and/or behave as they were designed to.
- Sometimes it might be difficult, even a challenge, to find what needs to be whitelisted in order to make a web page render and/or behave properly.

Mitigation to disadvantages:
- Quite commonly, the content of the page can still be read properly.
- A site-level scope can be used to restrict an allow all/block exceptionally mode to a web site.
- Geeky users can help less geeky users through the easy exchange of recipes (see *Rule manager*).
- (Future?) An easy accessible library of common useful recipes which can be applied with one click.

Useful Chromium settings with block-all/allow-exceptionally philosophy:

- Cookies set to "Keep local data only until I quit my browser"
- Plugins set to "Click to play"
- See further privacy enhancing settings in the *Settings* page.

## The allow-all/block-exceptionally approach

![allow-all/block-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-basics-allow-all-by-default.gif)

- All is allowed by default (through the whitelisting of the `all` cell).
- Preset blocked hosts are blacklisted.

Advantages:
- Web pages are more likely to render and/or behave as they were designed to.
- An informed and more aware user:
    * You see all the crap you are being served when not blocking (actually, it's worst because there are still the preset lists of blocked hosts which are still blocking more crap).

Disadvantages:
- Security is greatly diminished.
- Privacy is greatly diminished.
- Use more network bandwidth (web pages download slower)

Mitigation to disadvantages:
- The preset lists of blocked hosts, i.e. the disadvantages could be worst...
