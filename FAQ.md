Under construction.

* [What is "strict blocking"?](FAQ#what-is-strict-blocking)
* [In the top left of the matrix, what is "other"?](FAQ#in-the-top-left-of-the-matrix-what-is-other)
* [How can I see the full URL of requests made on a page?](FAQ#how-can-i-see-the-full-url-of-requests-made-on-a-page)
* [What does HTTP Switchboard does more than, say, AdBlock+ or AdBlock?](FAQ#what-does-http-switchboard-does-more-than-say-adblock-or-adblock)
* [What do you gain out of this?](FAQ#what-do-you-gain-out-of-this)

#### What is "strict blocking"?

Here are [snapshots](/gorhill/httpswitchboard/wiki/%22Strict-blocking%22-illustrated) of the difference between using **strict blocking** or not.

#### In the top left of the matrix, what is "other"?

So far, here is what I found:
- [favicon.ico](http://en.wikipedia.org/wiki/Favicon)
- [web fonts](http://en.wikipedia.org/wiki/Web_fonts)
- HTML5 [&lt;audio&gt;](http://en.wikipedia.org/wiki/HTML5_Audio) tag
- HTML5 [&lt;video&gt;](http://en.wikipedia.org/wiki/HTML5_video) tag
- [SVG](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics) files
- I found a behind-the-scene request occurrence by chromium: <https://www.google.com/searchdomaincheck?format=url&type=chrome>

#### How can I see the full URL of requests made on a page?

- Open the popup menu of *HTTP Switchboard*
- Click on the *Stats* icon in the top-right corner
- *HTTP Switchboard* info page opens
- Scroll down to the *Geeky stats* section
- There you can see the full URL of all requests, blocked or allowed, made by your browser
- Use the drop-down list to select the stats for a specific page
- Use the checkbox filters to narrow to specific types of request

#### What does HTTP Switchboard does more than, say, AdBlock+ or AdBlock?

There is [AdBlock](https://chrome.google.com/webstore/detail/adblock/gighmmpiobklfepjocnamgkkbiglidom), and there is [AdBlock Plus](https://chrome.google.com/webstore/detail/adblock-plus/cfhdojbkjhnklbpkdaibdccddilifddb) (which the [EFF advise to install](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online)).

If you really care about your privacy, it is good to know what is happening behind a web page, so
I did some tests to compare AdBlock and AdBlock Plus vs HTTP Switchboard. See the differences for yourself when using real web pages, and make an informed choice:

- AdBlock vs HTTP Switchboard:
    * [edition.cnn.com](http://www.diffchecker.com/flic8v70) (Edit: it appears the diffs are not permanent after all, my original one has been replaced with something else...)
    * [nbcpolitics.nbcnews.com](http://www.diffchecker.com/z9byyjng).
- AdBlock Plus (using EFF installation instructions) vs HTTP Switchboard:
    * [edition.cnn.com](http://www.diffchecker.com/jxpdhmit)
    * [nbcpolitics.nbcnews.com](http://www.diffchecker.com/wep03p6r).

Using out of the box settings for *AdBlock* and *HTTP Switchboard*. Using settings suggested by EFF for
*AdBlock Plus*. Note that with *HTTP Switchboard*, the user does not need to explicitly change the cookie settings in chromium/chrome (as required with AdBlock Plus). If cookies are blacklisted for a domain, any outbound cookie will be removed, regardless of chromium/chrome owns settings. 

#### What do you gain out of this?

Nothing, the project is [GPLv3](http://www.gnu.org/licenses/quick-guide-gplv3.html). I am having fun doing this though. Oh, and [this](https://www.gnu.org/philosophy/surveillance-vs-democracy.html)