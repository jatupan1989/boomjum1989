There is a web site you trust completely and you just want to whitelist all by default on
this web site, rather than hunting exactly for what should be whitelisted. I will use an
example to demonstrate how to proceed to whitelist all by default for a site you trust (like,
say, your bank).

Suppose I totally trust <https://vimeo.com/> (it's just an example, I actually trust nothing), and
I want to whitelist all by default for that site, that is, current web requests and whatever
future web requests the site might make. So here it is:

This is what you would see normally using out-of-the-box permissions (aka rules) of *HTTP Switchboard* ("HTTPSP"):

![Step 1](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-a.png)

Now click the page-scope button in order to create permissions specific to this page:

![Step 2](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-b.png)


![Step 3](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-c.png)


![Step 4](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-003-d.png)