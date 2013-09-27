HTTP Switchboard requires the following permissions to work properly:

    "permissions": [
        "contentSettings",
        "cookies",
        "storage",
        "tabs",
        "webNavigation",
        "webRequest",
        "webRequestBlocking",
        "<all_urls>"
    ],

* **contentSettings**: to enable/disable javascript or cookies for a web page.
* **cookies**: to allow the removal of blocked cookies.
* **storage**: to store your own whitelist/blacklist domains/objects.
* **tabs**: to enable forcing a reload of the content of a tab (when the content of the whitelist/blacklist change), and to enable injecting code into a page which reports whether at least one `<script>` tag is used on the page.
* **webNavigation**: to allow redirecting the URL of a blocked page or frame to a dummy page.
* **webRequest**: to allow intercepting all requests in order to inspect them.
* **webRequestBlocking**: to be able to block a request if the object of the request is blacklisted.
* `<all_urls>`: to be able to inspect traffic for all URLs.