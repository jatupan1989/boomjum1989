Recipes to import in *Rule manager*. More will be added over time.

The following recipes are all web site-scoped. For example, the permissions for the "Google Plus" recipe apply only while you are on a web page which URL starts with `https://plus.google.com`. On any other web page, the rules won't apply, meaning `plus.google.com` would be blocked, unless you have your own existing rules which whitelist `plus.google.com`.

Other users are starting to provide rules, so for now I will link to these external recipes:

- <http://www.wilderssecurity.com/showthread.php?p=2322738#post2322738>
- <http://www.wilderssecurity.com/showthread.php?p=2322822#post2322822>

### Google account login (updated 2013-12-24)

Works for everywhere you need to login into a Google service through <https://accounts.google.com>:

    https%3A%2F%2Faccounts.google.com%0A%09w
    hitelist%0A%09%09sub_frame%20youtube.com
    %0A%09%09*%20youtube.com%0A%09%09*%20gst
    atic.com%0A%09%09*%20googleusercontent.c
    om%0A%09%09*%20fonts.googleapis.com%0A%0
    9%09*%20google.com%0A%09blacklist%0A%09%
    09sub_frame%20*%0A%09%09*%20*%0A

### Google Plus

For <https://plus.google.com>:

    https%3A%2F%2Fplus.google.com%0A%09white
    list%0A%09%09*%20gstatic.com%0A%09%09*%2
    0google.com%0A%09%09image%20*%0A%09black
    list%0A%09%09sub_frame%20*%0A%09%09objec
    t%20*%0A%09%09*%20*%0A

### Youtube, with comments enabled (updated 2013-12-24)

For <https://www.youtube.com>:

    https%3A%2F%2Fwww.youtube.com%0A%09white
    list%0A%09%09*%20plus.googleapis.com%0A%
    09%09*%20google.com%0A%09%09*%20googlevi
    deo.com%0A%09%09*%20youtube.com%0A%09%09
    *%20ytimg.com%0A%09%09image%20*%0A%09%09
    sub_frame%20accounts.google.com%0A%09%09
    sub_frame%20googleapis.com%0A%09%09xmlht
    tprequest%20googleapis.com%0A%09blacklis
    t%0A%09%09*%20*%0A

### Facebook (without an account)

For <https://www.facebook.com>:

    https%3A%2F%2Fwww.facebook.com%0A%09whit
    elist%0A%09%09*%20akamaihd.net%0A%09%09*
    %20facebook.com%0A%09%09*%20fbcdn.net%0A
    %09%09*%20fbstatic-a.akamaihd.net%0A%09%
    09image%20*%0A%09blacklist%0A%09%09objec
    t%20*%0A%09%09sub_frame%20*%0A%09%09*%20
    *%0A*%0A%09blacklist%0A%09%09*%20faceboo
    k.com%0A%09%09*%20facebook.net%0A%09%09*
    %20fbcdn.net%0A
