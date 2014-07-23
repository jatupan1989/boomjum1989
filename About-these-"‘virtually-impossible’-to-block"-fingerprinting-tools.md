This is getting ridiculous. It's not impossible to block. It's rather easy. There are various ways, and the one techniques you choose depends on how much tolerance you have to site breakage. Here:

### Low breakage

Just block the domains known to engage in tracking. That will teach them.

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-2.gif)

### Rather low breakage

Just use the preset blocked hostnames that come out of the box with HTTP Switchboard (`addthis.com` has been blocked by these lists since forever).

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-3.png)

### Kind of low breakage

Just prevent whatever fingerprinting information from leaving your browser, so that whatever information was collected can not leave your browser.

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-1.gif)

### Kind of high breakage

Block javascript (common recommendation, but you need to not be annoyed by high breakage)

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-5.png)

### High breakage

Don't let anybody in by default. This requires patience, gain is peace of mind. You would be surprised at how many web pages still display properly and can be read just fine. (Scopes can be used to selectively unbreak your favorite web sites).

![](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/counter-fingerprinting-4.gif)
