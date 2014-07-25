This is getting ridiculous. It's not impossible to block. It's rather easy. There are various ways, and the one techniques you choose depends on how much tolerance you have to site breakage. Here:

### Low breakage

Just block the domains known to engage in tracking, using techniques like canvas-fingerprinting or hum, just plain logging of IP addresses. If no requests can reach their servers, this means their scripts won't reach your browser, and you won't leave IP address marks on their servers. You cease to exist from their point of views.

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-2.gif)

### Rather low breakage

Just use the preset blocked hostnames that come out of the box with HTTP Switchboard (`addthis.com`, `ligatus.com` have been blocked by these lists since forever). Somebody did the work for you to find out those engaged in tracking. You will cease to exist from the point of view of a whole lot of servers.

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-3.png)

### Kind of low breakage

Just prevent whatever fingerprinting information from leaving your browser. Note this addresses many kind of fingerprinting (`canvas` is just one among many), and also other creepy things such as tracking user's mouse etc. (for example, see `bounceexchange.com`). This won't prevent your IP address from being logged onto their server though, since you did not prevent **all** requests from reaching their server (see above for this).

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-1.gif)

### Kind of high breakage

Block javascript (common recommendation, but you need to not be annoyed by high breakage). If the only resource downloaded from the server is a script, then blocking the script will prevent your IP address from being logged. They also commonly use 1-pixel image, or sometimes a CSS file, so you might prefer blocking the domain outright if you don't even want your IP address in their log.

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-5.png)

### High breakage

Don't let anybody in by default. This requires patience, gain is peace of mind. You would be surprised at how many web pages still display properly and can be read just fine. (Scopes can be used to selectively unbreak your favorite web sites). Just look at how many domains were **not** reached in this mode (compare with screenshots above).

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-4.gif)
