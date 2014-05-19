You can configure _HTTP Switchboard_ in such a way as to make it behaves close to how typical ad blockers work.

Here is how the matrix would look like:

![HTTPSB as an ad blocker](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-as-abp.png)

I created a backup file which can be restored (from the _About_ tab) in order to make HTTPSB behave close to how ad blockers works:

<https://raw.githubusercontent.com/gorhill/httpswitchboard/master/stuff/httpsb-just-block-ads-setup.txt>.

From this point, you can head to the _Ubiquitous rules_  tab in the dashboard and select more third-party lists to enhance privacy, etc. The preset lists enabled with this setup are:

- <https://raw.githubusercontent.com/gorhill/httpswitchboard/master/assets/thirdparties/pgl.yoyo.org/as/serverlist>
- <https://raw.githubusercontent.com/gorhill/httpswitchboard/master/assets/thirdparties/hosts-file.net/ad-servers>
- <https://raw.githubusercontent.com/gorhill/httpswitchboard/master/assets/thirdparties/someonewhocares.org/hosts/hosts>
- <https://raw.githubusercontent.com/gorhill/httpswitchboard/master/assets/thirdparties/easylist-downloads.adblockplus.org/easylist.txt>

Remember: Restoring data from a full backup file will overwrite all your settings!