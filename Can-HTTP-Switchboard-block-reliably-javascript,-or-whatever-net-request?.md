Yes.

![HTTPSB can block reliably](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-can-block-reliably.png)

_HTTP Switchboard_ uses a different mechanism than previous Chromium blockers to prevent the execution of javascript, and this new mechanism take effect **before** the content of a web page is received.