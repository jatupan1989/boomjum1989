There is a conflict, but it is completely benign.

The conflict is that both extensions try to replace the content of `<iframe>` objects with harmless content.

However Chrome API will allow [only one extension to successfully redirect](http://developer.chrome.com/extensions/webRequest.html#conflict_resolution), while the redirect attempt by the other extension will fail. There is no real harmful consequences in the current case, it's just that Chrome makes it appears more dramatic by slapping a little error icon on top of one of the extensions.

As long as the content of blacklisted `<iframe>` objects is redirected to load harmless content, all is fine.