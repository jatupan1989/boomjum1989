# HTTP Switchboard -- Quick tour #1: 3/7

[Previous](Quick-tour-%231%3A-3-of-7) | [Next](Quick-tour-%231%3A-5-of-7)

![An example](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/quicktour-001-d.jpg)

(Below text from image is replicated for search engines to find this page for anyone seeking help)
- "Just to demonstrate de precedence thingy when it comes to white or blacklisting"
- "This is the **master switch**"
- "I can blacklist **cookies** from **radio-canada.ca** (and whatever subomains it has) even though **radio-canada.ca** is whitelisted"
- "This cell is blocked, because between it and the **master switch**, **cookies** for **radio-canada.ca** are blacklisted"
- "This cell is allowed, because between it and the **master switch**, **radio-canada.ca** is whitelisted"
- "This cell is blocked, because between it and the **master switch**, there is nothing expressly black or whitelisted, so the **master switch** decides"
- "This cell is allowed, because between it and the **master switch**, **images** are whitelisted"