*HTTP Switchboard* supports per-page permissions. Here is a typical case example to illustrate why per-page permissions are useful, and how to use per-page permissions.

Some [hostnames](https://en.wikipedia.org/wiki/Hostname) are ubiquitous on the internet.

For example, assets from `facebook.com` are pulled from countless web pages. Whenever a web page request assets from `facebook.com`, *Facebook*, through its logs, has the ability to use plenty of metadata from your IP (or yourself if you are logged in permanently) to infer a pretty good picture of your browsing habits.

Not everybody is comfortable with this and for [good reasons](https://www.eff.org/deeplinks/2013/04/disconcerting-details-how-facebook-teams-data-brokers-show-you-targeted-ads). If you are not comfortable with this, it is nice to be able to blacklist `facebook.com` using *HTTP Switchboard*:

![`facebook.com` blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/per-permission-facebook-1.png)

But now what if you want to visit a web page on `facebook.com` or if you have an account on `facebook.com` which you still want to use?

![`facebook.com` blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/per-permission-facebook-2.png)

This is the dilemma: preventing `facebook.com` from tracking you, while being able to visit web pages on `facebook.com` itself. This is where *HTTP Switchboard's* **per-page permissions** come to the rescue:

![`facebook.com` blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/per-permission-facebook-3.png)

Here, per-page permissions for `https://www.facebook.com` are created. Notice the visual cue: when per-page permissions are active, the top of the pop-up menu is blueish, and the badge on the extension icon is blue.

![`facebook.com` blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/per-permission-facebook-4.png)

Whatever you whitelist/blacklist in per-page permissions mode will apply **strictly** to `https://www.facebook.com` in the above example. Any page which does not start **exactly** with `https://www.facebook.com` will not use the permissions specific to `https://www.facebook.com`.

The specific permissions created above will *not* apply to `http://www.facebook.com`, `https://facebook.com`, `https://www.facebook.net`, etc.

![`facebook.com` blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/per-permission-facebook-5.png)

Per-page permissions must also be padlocked to stick, just like global permissions.

After you have created whitelist permissions specific to `https://www.facebook.com`, `facebook.com` is still blacklisted globally:

![`facebook.com` blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/per-permission-facebook-1.png)

So *Facebook* is from then on forbidden to log which web pages you are visiting, except when you visit web pages on `https://www.facebook.com`.

You can do the same for other ubiquitous hostnames which serve as assets store for countless web pages (ex. `google.com`), while these hostnames also have web pages providing useful services: "blacklist `google.com` except when I use a web page on `https://www.google.com`". Etc. etc.

<sup>Disclaimer: the author doesn't have a *Facebook* account, and doesn't read *CNN*...</sup>