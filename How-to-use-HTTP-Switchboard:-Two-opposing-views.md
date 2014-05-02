There are two main ways to use *HTTP Switchboard* ("HTTPSB"), and then there is everything in between and [beyond](http://www.wilderssecurity.com/threads/http-switchboard-for-chrome-chromium.356427/page-25#post-2357557). Basically: your choice.

- [Block All / Allow Exceptionally](#the-block-allallow-exceptionally-approach)
- [Allow All / Block Exceptionally](#the-allow-allblock-exceptionally-approach)
- [Allow All / Disclose All](#the-allow-alldisclose-all-approach)

One important thing to remember though, regardless of the approach you choose, the preset lists of blocked hosts is useful to block the ad servers, trackers, malware, nuisance, etc. of the internet.

#### Quick notes for novice users

Novice users shouldn't bother trying to figure which cells in the middle of the matrix need to be whitelisted or blacklisted. These cells are really more suited to advanced users and even then, exceptionally: their original purpose was to be mostly informative ("how many requests for a given type of data from a given hostname?")

I advise new users to stick to whitelist/blacklist domain cells (the left-most column) to allow or block everything from a particular domain, or type of data cells (the top-most row).

## The block-all/allow-exceptionally approach

![block-all/allow-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-basics-block-all-by-default.gif)

How to enable (this is the out-of-the-box settings):
- Blacklist the `all` and `frame` cells.
- Whitelist the `css` and `img` cells.
- Save by clicking on the padlock.

Behaviors:
- All is blocked by default (through the blacklisting of the `all` cell).
- CSS and images are whitelisted.
- Frames are blacklisted.
- Preset blocked hosts are blacklisted.

Advantages:
- Security is greatly enhanced.
    * External and inline scripts won't execute (contrary to a commonly held belief, inline scripting can be disabled in Chromium).
- Privacy is greatly enhanced.
- Use less network bandwidth ([web pages download faster](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites))

Disadvantages:
- Web pages are less likely to render and/or behave as they were designed to.
- Sometimes it might be difficult, even a challenge, to find what needs to be whitelisted in order to make a web page render and/or behave properly.

Mitigation to disadvantages:
- Quite commonly, the content of the page can still be read properly.
- A site-level scope can be used to restrict an allow all/block exceptionally mode to a web site.
- Advanced users can help novice users through the easy exchange of recipes (see *Rule manager*).
- (~~Future?~~ Present) An easy accessible library of common useful recipes which can be applied with one click.
- The preset recipe feature introduced in [0.7.8.0](https://github.com/gorhill/httpswitchboard/wiki/Change-log#wiki-0780).

Useful Chromium settings with block-all/allow-exceptionally philosophy:

- Cookies set to "Keep local data only until I quit my browser"
- Plugins set to "Click to play"
- See further privacy enhancing settings in the *Settings* page.

## The allow-all/block-exceptionally approach

![allow-all/block-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-basics-allow-all-by-default.gif)

How to enable:
- Whitelist the `all` cell.
- Un-blacklist the `frame` cell.
- Save by clicking on the padlock.

Behaviors:
- All is allowed by default.
- Preset blocked hosts are still blacklisted (because their own blacklist rule has precedence over the whitelist rule of the `all` cell).

Advantages:
- Web pages are more likely to render and/or behave as they were designed to.
- An informed and more aware user:
    * You see all the crap you are being served when not blocking (actually, it would be worst if it wasn't of the preset lists of blocked hosts which are preventing more bloat and nuisance from coming to life).

Disadvantages:
- Security is greatly diminished.
- Privacy is greatly diminished.
- Use more network bandwidth (web pages download slower)

Mitigation to disadvantages:
- The preset lists of blocked hosts, i.e. it could be worst (notice the 22 blocked scripts above).
- The support of _Adblock Plus_ complex filters introduced in 0.8.4.0.

## The allow-all/block-nothing/disclose-everything approach

This is the "extreme" approach of allowing everything, blocking nothing, but then the user keep the ability to see **all** the connections a web pages does.

![allow-all/block-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-allow-all-disclose-all.png)

How to enable:
- Whitelist the `all` cell.
- Un-blacklist the `frame` cell.
- Un-whitelist the `css` and `img` cells (just to keep things tidy).
- Save by clicking on the padlock.
- Go to the _Ubiquitous rules_ tab in the dashboard and unselect **all** lists of preset blocked hosts. Click _Apply changes_.

In this mode, absolutely nothing will be blocked by HTTPSB. A bit useless, but then, this allows a user to see completely what a web page does when no blockers are used, or if you have another blocker extension  installed, to see what is not blocked by the other extension.

It also allows a user to see the behind-the-scene connections made by the browser or other installed extensions.
