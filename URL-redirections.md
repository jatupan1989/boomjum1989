Starting with version 0.7.7.0, [URL redirections](http://en.wikipedia.org/wiki/URL_redirection) are now reported in the matrix.

There was an outstanding issue ([#112](/gorhill/httpswitchboard/issues/112)) in order to figure a way to report URL redirections, but the [Window Resizer](http://chrisbalt.com/blog/2013/12/20/link-hijacking-through-chrome-extensions-and-other-security-risks.html) saga reminded me this was important to address the issue sooner than later.

URL redirections are recognizable in the matrix from domain name entries for which all cells are empty. An example using the above-mentioned Window Resizer URL hijacking (search term in `google.com` was "deception"):

![matrix](https://raw2.github.com/gorhill/httpswitchboard/3cd5eacc40de0c344494bfcc5eb62cfcfffbafa1/doc/img/redirection-example-1-matrix.png)

Notice that all cells from `ecosia.org` **and** related subdomains are empty. This is a good hint that the current page was the result of a redirect from a request to third-party (from the point of view of the viewed page) `ecosia.org` in this example.

The log of requests will also provide a clue about the URL redirection:

![log](https://raw2.github.com/gorhill/httpswitchboard/3cd5eacc40de0c344494bfcc5eb62cfcfffbafa1/doc/img/redirection-example-1-log.png)

### Important notes

Notice that it *may* happen that a web page is so bare that it does not request any external resource, in which case all the cells for such a page would also be empty, however this is rather rare.

Also, until [issue #93](https://github.com/gorhill/httpswitchboard/issues/93) is fixed, there can be occurrences of all cells being empty for a whole domain and associated subdomains due to objects from cache not be reported in the matrix.