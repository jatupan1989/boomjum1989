You can configure _HTTP Switchboard_ in such a way as to make it behaves close to how [NoScript for Firefox](https://addons.mozilla.org/en-US/firefox/addon/noscript/) works.

Here is how the matrix would look like:

![HTTPSB as NoScript](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-as-noscript.png)

I created a backup file which can be restored (from the _About_ tab) in order to make HTTPSB behave close to how _NoScript_ works:

<https://raw.githubusercontent.com/gorhill/httpswitchboard/master/stuff/httpsb-noscript-like-setup.txt>.

_NoScript_ comes with a preset list of hostnames for which javascript is allowed, this list has been included in the above setup file as ubiquitously whitelisted hostnames. In order for this whitelist to work properly, ["strict blocking"](/gorhill/httpswitchboard/wiki/%22Strict-blocking%22-illustrated) is disabled in the above setup file.

Remember: Restoring data from a full backup file will overwrite all your settings!

### HTTP Switchboard "seems to need more micromanagement" compared to NoScript

Not really. I supposed the erroneous impression stems from all the cells in the matrix. It does not require more management. If a user wants to allow one script from one page, one click is sufficient with _HTTP Switchboard_, just like _NoScript_. Admittedly though, if a user wants to allow one or more scripts **permanently**, an extra click is required, to tell _HTTPSB_ to persist the whitelisted cells in the matrix, since by design, all permissions are temporary -- with the benefit that as opposed to _NoScript_, there is no need to duplicate every hostname in the menu (one for temporary permission, one for permanent permission.)

####Consider _NoScript_:

![arstechnica.com with NoScript](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/ns-vs-httpsb-1-ns.png)

####And now _HTTPSB_:

![arstechnica.com with HTTPSB](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/ns-vs-httpsb-1-httpsb.png)

In both case, one single click was required to enable scripts temporarily from `arstechnica.com`.

From the two screenshots, one can see however that _HTTPSB_ refers to more hostnames than _NoScript_: It is because _HTTPSB_ will report **all** net traffic, i.e. not just that of scripts on the page. In the example above, one can see that with out-of-the-box settings, _HTTPSB_ also blocked a tracking pixel from `condenast.112.2o7.net`.

Of course, the more scripts allowed by a user, the more tracking pixels and other annoyances are going to be reported by _HTTPSB_. To get ~~the same~~ similar (but falling short) level of information and control, a user would have to also install _Request Policy_ aside _NoScript_. (I say "falling short" because _Request Policy_ categorizes request only using their hostname, it does not further categorize requests by type.)