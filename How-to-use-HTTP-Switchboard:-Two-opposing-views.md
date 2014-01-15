There are two main ways to use *HTTP Switchboard* ("HTTPSB"), and then there is everything in between and beyond. Basically: your choice.

One important thing to remember though, whatever the approach you use, the preset lists of blocked hosts can still be used to block the ad servers, trackers, malware, nuisance, etc. of the internet.

## The block-all/allow-exceptionally approach

![block-all/allow-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-basics-block-all-by-default.png)

This is the out-of-the-box settings:
- All is blocked by default (by means of the `all` cell being blacklisted).
- CSS and images are whitelisted.
- Frames are blacklisted.
- Preset blocked hosts are blacklisted.

Advantages:
- Security is greatly enhanced.
- Privacy is greatly enhanced.

Disadvantages:
- Web pages are less likely to render and/or behave as they were designed to.
- Sometimes it might be difficult, even a challenge, to find what needs to be whitelisted in order to make a web page render and/or behave properly. Mitigation:
    * A site-level scope can be used to restrict a allow all/block exceptionally mode to a web site.
    * Geeky users can help less geeky users through the easy exchange of recipes.
    * (Future?) An easy accessible library of common useful recipes which can be applied with one click.

## The allow-all/block-exceptionally approach

![allow-all/block-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-basics-allow-all-by-default.png)

- All is allowed by default (by means of the `all` cell being whitelisted).
- Preset blocked hosts are blacklisted.

Advantages:
- Web pages are more likely to render and/or behave as they were designed to.
- You see all the crap you are being served when not blocking (actually, it's worst because there are still the preset lists of blocked hosts which are still blocking more crap).

Disadvantages:
- Security is greatly diminished. Mitigation:
    * The preset lists of blocked hosts.
- Privacy is greatly diminished. Mitigation:
    * The preset lists of blocked hosts.
