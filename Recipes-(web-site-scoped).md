Recipes to import in *Rule manager*.

### Google account login

Works for everywhere you need to login into a Google service:

    https%3A%2F%2Faccounts.google.com%0A%09w
    hitelist%0A%09%09*%20google.ca%0A%09%09*
    %20google.com%0A%09%09*%20googleusercont
    ent.com%0A%09%09*%20youtube.com%0A%09%09
    image%20*%0A%09%09sub_frame%20google.com
    %0A%09%09sub_frame%20youtube.com%0A%09bl
    acklist%0A%09%09object%20*%0A%09%09sub_f
    rame%20*%0A%09%09*%20*%0A

### Google Plus

For https://plus.google.com :

    https%3A%2F%2Fplus.google.com%0A%09white
    list%0A%09%09*%20gstatic.com%0A%09%09*%2
    0google.com%0A%09%09image%20*%0A%09black
    list%0A%09%09sub_frame%20*%0A%09%09objec
    t%20*%0A%09%09*%20*%0A

### Youtube, with comments enabled

For https://www.youtube.com :

    https%3A%2F%2Fwww.youtube.com%0A%09white
    list%0A%09%09xmlhttprequest%20googleapis
    .com%0A%09%09sub_frame%20googleapis.com%
    0A%09%09*%20google.com%0A%09%09*%20youtu
    be.com%0A%09%09*%20ytimg.com%0A%09%09ima
    ge%20*%0A%09%09object%20googlevideo.com%
    0A%09%09object%20youtube.com%0A%09%09obj
    ect%20ytimg.com%0A%09%09sub_frame%20acco
    unts.google.com%0A%09%09sub_frame%20goog
    le.com%0A%09%09xmlhttprequest%20googlevi
    deo.com%0A%09blacklist%0A%09%09object%20
    *%0A%09%09sub_frame%20*%0A%09%09*%20*%0A

### Facebook blocked everywhere except `facebook.com`

For https://www.facebook.com :

    https%3A%2F%2Fwww.facebook.com%0A%09whit
    elist%0A%09%09*%20akamaihd.net%0A%09%09*
    %20facebook.com%0A%09%09*%20fbcdn.net%0A
    %09%09*%20fbstatic-a.akamaihd.net%0A%09%
    09image%20*%0A%09blacklist%0A%09%09objec
    t%20*%0A%09%09sub_frame%20*%0A%09%09*%20
    *%0A*%0A%09blacklist%0A%09%09*%20faceboo
    k.com%0A%09%09*%20facebook.net%0A%09%09*
    %20fbcdn.net%0A