You can configure _HTTP Switchboard_ in such a way as to make it behaves close to how [RequestPolicy for Firefox](https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/) works.

Here is how the matrix would look like:

![HTTPSB as RequestPolicy](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-as-requestpolicy.png)

In the above setup, all the request types are graylisted by default, and "Auto-whitelist page domain" is enabled.

I created a backup file which can be restored (from the _About_ tab) in order to make HTTPSB behave close to how _RequestPolicy_ works:

<https://raw.githubusercontent.com/gorhill/httpswitchboard/master/stuff/httpsb-requestpolicy-like-setup.txt>.

Remember: Restoring data from a full backup file will overwrite all your settings!