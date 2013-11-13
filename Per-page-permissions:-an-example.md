*HTTP Switchboard* supports per-page permission. Here is a typical case example to illustrate why per-page permissions are useful, and how to create per-page permissions.

Some hostnames are ubiquitous on the internet.

For example, assets from `facebook.com` are pulled from countless web pages. Whenever a web page request assets from `facebook.com`, *Facebook*, through its logs, has the ability to use plenty of metadata from your IP (or yourself if you are logged in permanently) to infer a pretty good picture of your browsing habits.

Not everybody is comfortable with this and for good reasons. If you are not comfortable with this, it is nice to be able to blacklist `facebook.com` using *HTTP Switchboard*:

![`facebook.com` blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/per-permission-facebook-1.png)