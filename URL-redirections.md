Starting with version 0.7.7.0, URL redirections are now reported in the matrix.

There was an outstanding issue ([#112](/gorhill/httpswitchboard/issues/112)) in order to figure a way to report URL redirections, but the [Window Resizer](http://chrisbalt.com/blog/2013/12/20/link-hijacking-through-chrome-extensions-and-other-security-risks.html) saga reminded me this important to address the issue sooner than later.

URL redirections are recognizable in the matrix from domain name entries for which all cells are empty. An example using the above-mentioned Window Resizer link high-jacking (search term in `google.com` was "deception"):

![matrix](https://raw2.github.com/gorhill/httpswitchboard/3cd5eacc40de0c344494bfcc5eb62cfcfffbafa1/doc/img/redirection-example-1-matrix.png)

Notice that all cells from `ecosia.org` **and** related subdomains are empty. This is the telltale sign that the current page was the result of a redirect from a request to `ecosia.org` in this example.

The log of requests will also provide a clue about the URL redirection:

![log](https://raw2.github.com/gorhill/httpswitchboard/3cd5eacc40de0c344494bfcc5eb62cfcfffbafa1/doc/img/redirection-example-1-log.png)
