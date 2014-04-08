Using notable news headlines as examples of how HTTP Switchboard helps users.

### The Verge: "How advertising cookies let observers follow you across the web"

Link: http://www.theverge.com/2014/4/4/5581884/how-advertising-cookies-let-observers-follow-you-across-the-web

> Back in December, documents revealed the NSA had been using Google's ad-tracking cookies to follow browsers across the web, effectively coopting ad networks into surveillance networks. A new paper from computer scientists at Princeton breaks down exactly how easy it is, even without the resources and access of the NSA. The researchers were able to reconstuct as much as 90% of a user's web activity just from monitoring traffic to ad-trackers like Google's DoubleClick. Crucially, the researchers didn't need any special access to the ad data. They just sat back and watched public traffic across the network.

HTTP Switchboard strips non-whitelisted cookie information out of request headers. Furthermore, one can blacklist explicitly the `cookie` column, so that cookie information is removed even for whitelisted hosts (this is actually my choice of settings.)

Note that removing cookie information synchronously from request headers (what HTTPSB does) is a much more reliable way to deal with cookies than just deleting them asynchronously from the browser.

