Under construction.

* [Can I whitelist Facebook (or whatever) only when visiting Facebook (or whatever)?](FAQ#can-i-whitelist-facebook-or-whatever-only-when-visiting-facebook-or-whatever)
* [Why my browser-based popup player doesn't play even after whitelisting all?](FAQ#why-my-browser-based-player-doesnt-play-even-after-whitelisting-all)
* [What is "strict blocking"?](FAQ#what-is-strict-blocking)
* [In the top left of the matrix, what is "other"?](FAQ#in-the-top-left-of-the-matrix-what-is-other)
* [How can I see the full URL of requests made on a page?](FAQ#how-can-i-see-the-full-url-of-requests-made-on-a-page)
* [What does HTTP Switchboard does more than, say, AdBlock+ or AdBlock?](FAQ#what-does-http-switchboard-does-more-than-say-adblock-or-adblock)
* [What do you gain out of this?](FAQ#what-do-you-gain-out-of-this)

#### Can I whitelist Facebook (or whatever) only when visiting Facebook (or whatever)?

Yes, using [per-page permissions](https://github.com/gorhill/httpswitchboard/wiki/Per-page-permissions:-an-example).

#### Why my browser-based player doesn't play even after whitelisting all?

Typical scenario as an example (inspired from [issue #40](/gorhill/httpswitchboard/issues/40)):

- Goto <http://www.teamradio.ca>.
- Click "LISTEN LIVE 1040" on the right.
- A browser popup window opens (that would be the browser-based player).

The popup menu for HTTPSB is unreachable in the browser-based player window. This means there is no way to whitelist just what is needed to make the browser-based player work. The problem is not specific to HTTPSB, any extension you have might be crippled by having its popup menu unreachable.

This is why popup browser windows suck. They are rude, they interfere with *your* choices.

Until I find a handsome solution (if any), here is the workaround:

- Copy the URL address in the browser-based player.
- Open a new tab in the main browser window (the one in which the extension button is not occulted).
- Paste the URL address in the address bar.
- The browser-based player will now open in the full window, you can now whitelist appropriately.
- Once you are satisfied with your careful whitelisting, make sure to persist them using the padlock.
- Close this tab.

From then on, the browser-based popup-up player will be able to play correctly the content.

Just for information purpose, for the above example specifically, just whitelisting:

- `teamradio.ca`
- `streamtheworld.com`
- `plugin` @ `streamtheworld.com`

Solved the problem.

#### What is "strict blocking"?

Here are [snapshots](/gorhill/httpswitchboard/wiki/%22Strict-blocking%22-illustrated) of the difference between using **strict blocking** or not.

#### In the top left of the matrix, what is "other"?

See this [wiki page](/gorhill/httpswitchboard/wiki/In-the-top-left-of-the-matrix,-what-is-%22other%22%3F).

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