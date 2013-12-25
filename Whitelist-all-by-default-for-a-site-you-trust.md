There is a web site you trust completely and you just want to whitelist all by default on
this web site, rather than hunting exactly for what should be whitelisted to make it work smoothly. "Whitelisting by default" means all current and future requests will be allowed (a feature many NoScript users wish they had: ["Why must I "Temporarily allow all this page" REPEATEDLY?"](http://forums.informaction.com/viewtopic.php?f=7&t=8309))

I will use an example to demonstrate how to proceed to whitelist all by default for a site you trust (like,
say, your bank).

Suppose I totally trust <https://vimeo.com/> (it's just an example...), and
I want to whitelist all by default for that site, that is, current web requests and whatever
future web requests the site might make. So here it is:

This is what you would see normally using out-of-the-box permissions (aka rules) of *HTTP Switchboard* ("HTTPSB"):

![Step 1](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-a.png)

Now click the scope button and select the site-level scope in order to create permissions specific to this web site (that would be the top-left button):

![Step 2](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-b.png)

While in site-level scope, all rules created from now on while on this web site will apply *only* to this web site (<https://vimeo.com> in our example).

![Step 3](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-c.png)

Now click the "all" cell in the matrix (the top-left one) to turn it dark green, which means "whitelist all" by default. All the cells in the matrix which do not have explicit permissions (whether *allow* or *block*) will toggle state according to the *all* cell. Don't forget to lock the matrix state by clicking on the padlock tool at the top.

![Step 4](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-d.png)

Now leave the pop-up menu and let the page reload. Reopen the pop-up menu and see that new web requests
made by the page were not blocked. The only requests which are still blocked are the ones explicitly
blacklisted.

Note the same can be done without going into site-level scope, but then this broad whitelisting would apply
globally, i.e. to every page, not just the one you trust, hence the usefulness of the site-level scope feature in this case.

Keep in mind that when default is all being whitelisted, this means you need to blacklist selectively (as opposed to default blacklist-all/whitelist-selectively), so if after whitelisting all there is something you don't like in the matrix, you will have to selectively blacklist it. Example:

![Step 5](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-e.png)