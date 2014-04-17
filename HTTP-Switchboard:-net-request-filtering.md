### Overview

![Net request filtering](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-overview.png)

### Matrix filtering

With _HTTP Switchboard_ version 0.8.7.0, the master switch (which was the left-most button in the matrix toolbar) is gone, and has been replaced with a new **scope-based** master switch. There are many advantages for having a master switch which applies **only** to the current scope.

It may happen a user give up in trying to figure the proper set of matrix rules in order to make a web site work properly. Sometimes, ubiquitously blacklisted hostnames must unfortunately be un-blacklisted for a web page to work properly. It may quickly become bothersome, to the point where a user was simply switching off HTTPSB completely just because of one specific web page.

So it is now possible to completely turn off matrix filtering for a specific scope, which will leave all other scopes unaffected. Here is a comparison of three matrix states, [block-all / allow-exceptionally](https://github.com/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-block-allallow-exceptionally-approach), [allow-all / block-exceptionally](https://github.com/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-allow-allblock-exceptionally-approach), and matrix filtering off:

![Matrix filtering](https://raw.githubusercontent.com/gorhill/httpswitchboard/a65026f65973c1a81ba69ecbc5041da5fe956054/doc/img/mtx-filtering-switch.gif)

With the addition of the matrix filtering switch, I took the opportunity to make these other changes in order to increase consistency:

- The new matrix filtering switch is _independent_ from the ABP filtering switch: one can disable matrix filtering and still benefit from ABP filtering.
- The new matrix filtering button shows the number of requests blocked in a badge, just like the ABP filtering button.

Note that the state of the matrix filtering switch is persisted as part of a scope state (just like the ABP filtering switch).

The matrix filtering switch **will not** modify in any way the matrix rules of the scope, it just allows to bypass these rules. This means that the persisted state of the matrix rules will stay visible even though all the cells in the matrix are turned green when matrix filtering is off.

It is **not** possible to edit the matrix rules when matrix filtering is off.

### ABP filtering

[to do]