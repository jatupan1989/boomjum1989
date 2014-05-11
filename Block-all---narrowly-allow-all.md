This mode is interesting for people who wants to be protected by default when landing on any web site, and yet wish to be able to allow the whole web site - but **only** that web site -- with a single click, so as to skip having to hunt for the proper set of rules to make a "broken" web site work if needed.

Through the use of a matrix scope, it is possible to allow a whole site without affecting the default block-all status of all other web sites.

Here is how the matrix would look like right after landing on the web site:

![Block-all](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-block-all-narrowly-allow-all.png)

Notice in the screenshot above that a domain-level scope was auto-created by HTTPSB (`*.wired.com`), therefore new permissions will apply *only* to web pages from `wired.com`.

Now from this point, you have choice to soft-allow all or hard-allow all (or whatever else, really).

Soft-allowing all will whitelist the whole matrix **except** the ubiquitously blocked hostnames. This is simple done by whitelisting the `all` cell:

![Block-all / soft allow all](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-block-all-narrowly-allow-all-soft.png)

Hard-allowing all will whitelist the whole matrix **including** the ubiquitously blocked hostnames. This is unfortunately needed sometimes as some web sites require some of these nuisance servers to be reachable in order for a page to work properly. This is simply done by disabling matrix filtering:

![Block-all / hard allow all](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-block-all-narrowly-allow-all-hard.png)

In both cases above, soft- or hard-allowing all applies **ONLY** to web pages sitting on the `wired.com` domain, everything else would still be blocked by default. Also, remember that all changes are temporary, until you click the padlock.

I created a backup file which can be restored (from the _About_ tab) in order to make HTTPSB behave as described above:

<https://raw.githubusercontent.com/gorhill/httpswitchboard/master/stuff/httpsb-block-all-narrowly-allow-all-setup.txt>.

Remember: Restoring data from a full backup file will overwrite all your settings!