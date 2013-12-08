A whole lot of web sites pull resources from 3rd parties (examples: `themes.googleusercontent.com`, `cloudfront.net`) thus giving these 3rd parties log data telling them that one specific IP address has been visiting one specific website. If you are really concerned with privacy, you might not want that.

The results below are my findings, and they are published in the spirit of informed consent.

### Methodology

- [Ghostery](https://chrome.google.com/webstore/detail/ghostery/mlomiejdfkolichcflejclcbmpeaniij)
    * version 5.0.0
    * "Block all", and nothing whitelisted.
- [Disconnect](https://chrome.google.com/webstore/detail/disconnect/jeoacafpbcihiomhlakheieifhpjdfeo)
    * version 5.10.2
    * Everything is blocked (green), and nothing whitelisted.
- [HTTP Switchboard](https://chrome.google.com/webstore/detail/http-switchboard/mghdpehejfekicfjcdbfofhcmnjhgaag)
    * version 0.6.6
    * Out of the box settings.
    * Domain of visited site whitelisted.

- Steps:
    * Browser cache was cleared.
    * Target web page was forced refresh.
    * Data was pulled from the developer console.
    * Only `{scheme}://{hostname}` is listed below, often many requests to same hostnames, for various type of data (javascript, font, css, etc.)

### Results

Various random sites tested.

***

### http://www.upworthy.com

#### Ghostery says it blocks
* ![Ghostery said it blocked these](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-1-ghostery.png)
#### Ghostery did allow:
    - `http://www.google.com`
    - `http://themes.googleusercontent.com`
    - `http://fonts.googleapis.com`
    - `http://platform.twitter.com`
    - `http://d8rk54i4mohrb.cloudfront.net`
    - `http://upw-prod-images.global.ssl.fastly.net`

#### Disconnect says it blocks
* ![Disconnect said it blocked all](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-1-disconnect.png)
#### Disconnect did allow:
    - `cc.simplereach.com`
    - `fonts.googleapis.com`
    - `d8rk54i4mohrb.cloudfront.net`
    - `upw-prod-images.global.ssl.fastly.net`

#### HTTP Switchboard says it blocks:
* ![HTTPSB said it blocked these](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-1-httpsb.png)
#### HTTPSB did allow:
    - `http://upw-prod-images.global.ssl.fastly.net`

### [a few more results coming]