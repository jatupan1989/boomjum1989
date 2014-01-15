There are two main ways to use *HTTP Switchboard* ("HTTPSB"), and then there is everything in between and beyond. Basically: your choice.

### The block-all/allow-exceptionally approach

![block-all/allow-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-basics-block-all-by-default.png)

This is the out-of-the-box setting:
- All is blocked by default (by means of the `all` cell being blacklisted).
- CSS and images are whitelisted.
- Frames are blacklisted.
- Preset blocked hosts are blacklisted.

...

- Advantages:
    * Security is greatly enhanced.
    * Privacy is greatly enhanced.
- Disadvantages:
    * Web pages are less likely to render and behave as they were designed to.

### The allow-all/block-exceptionally approach

![allow-all/block-exceptionally](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-basics-allow-all-by-default.png)

- All is allowed by default (by means of the `all` cell being whitelisted).
- Preset blocked hosts are blacklisted.

...

- Advantages:
    * Web pages are more likely to render and behave as they were designed to.
- Disadvantages:
    * Security is greatly diminished.
    * Privacy is greatly diminished.