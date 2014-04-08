Using notable news headlines as examples of how HTTP Switchboard helps users.

### The Verge: "How advertising cookies let observers follow you across the web"

Date: April 4, 2014

Link: http://www.theverge.com/2014/4/4/5581884/how-advertising-cookies-let-observers-follow-you-across-the-web

> Back in December, documents revealed the NSA had been using Google's ad-tracking cookies to follow browsers across the web, effectively coopting ad networks into surveillance networks. A new paper from computer scientists at Princeton breaks down exactly how easy it is, even without the resources and access of the NSA. The researchers were able to reconstuct as much as 90% of a user's web activity just from monitoring traffic to ad-trackers like Google's DoubleClick. Crucially, the researchers didn't need any special access to the ad data. They just sat back and watched public traffic across the network.

HTTP Switchboard strips non-whitelisted cookie information out of request headers.

Furthermore, one can blacklist explicitly the `cookie` column, so that cookie information is removed even for whitelisted hosts (this is actually my choice of settings). For example, the screenshot below show that Google won't receive any cookies from me even though `google.ca` is whitelisted:

![Blacklisted cookies](https://raw.githubusercontent.com/gorhill/httpswitchboard/893b621213d70c9d0a420938827d87845fc398f6/doc/img/httpsb-blacklist-cookies.png)

Note that removing cookie information synchronously from request headers (what HTTPSB does) is a much more reliable way to deal with cookies than just deleting them asynchronously from the browser.

### Incapsula: "One of World’s Largest Websites Hacked: Turns Visitors into 'DDoS Zombies' "

Date: April 3, 2014

Link: http://www.incapsula.com/blog/world-largest-site-xss-ddos-zombies.html

> As a result, each time a legitimate visitor landed on that page, his browser automatically executed the injected JavaScript, which in turn injected a hidden <iframe> with the address of the DDoSer’s C&C domain. There, an Ajax-scripted DDoS tool hijacked the browser, forcing it to issue a DDoS request at a rate of one request per second.

HTTP Switchboard would have protected a user in many ways.

- If first-party javascript is disabled, the malicious code would not execute.
- If first-party javascript is enabled, the malicious code then creates an `iframe` object
- The malicious `iframe` object attempts to load more malicious javascript code from a host belonging to the malicious party, but HTTP Switchboard protects you doubly here:
    * `iframe` object are blacklisted out-of-the-box.
    * All hosts are blacklisted by default out-of-the-box, i.e. the malicious host is rather unlikely to have been whitelisted by a user, thus it defaults to being blocked.