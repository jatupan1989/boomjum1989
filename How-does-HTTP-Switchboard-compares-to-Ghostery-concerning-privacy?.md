A whole lot of web sites pull resources from 3rd parties (examples: `themes.googleusercontent.com`, `cloudfront.net`) thus giving these 3rd parties log data telling them that one specific IP address has been visiting one specific website. If you are really concerned with privacy, you might not want that.

The results below are my findings, because I care about informed consent.

Settings:
- Ghostery
    * version 5.0.0
    * "Block all", and nothing whitelisted.
- HTTPSB
    * version 0.6.6
    * Out of the box settings.
    * Domain of visited site whitelisted.

Various sites tested, results:

### http://www.upworthy.com

* Ghostery said:
    - ![Ghostery said it blocked these](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-1-ghostery.png)
* Ghostery did allow these 3rd parties:
    - `http://www.google.com/uds/api/ads/3.0/01478b579c57efb8589bd6564832cfea/search.I.js`
    - `http://themes.googleusercontent.com/static/fonts/droidserif/v3/QQt14e8dY39u-eYBZmppwTqR_3kx9_hJXbbyU8S6IN0.woff`
    - `http://themes.googleusercontent.com/static/fonts/sourcesanspro/v6/ODelI1aHBYDBqgeIAH2zlBM0YzuT7MdOe03otPbuUS0.woff`
    - `http://platform.twitter.com/widgets.js`
    - `http://themes.googleusercontent.com/static/fonts/droidserif/v3/c92rD_x0V1LslSFt3-QEpgRV2F9RPTaqyJ4QibDfkzM.woff`
    - `http://themes.googleusercontent.com/static/fonts/sourcesanspro/v6/toadOcfmlt9b38dHJxOBGFkQc6VGVFSmCnC_l7QZG60.woff`
    - `http://themes.googleusercontent.com/static/fonts/droidserif/v3/cj2hUnSRBhwmSPr9kS5899kZXW4sYc4BjuAIFc1SXII.woff`
    - `http://d8rk54i4mohrb.cloudfront.net/js/reach.js`
    - `http://platform.twitter.com/js/tfw/hub/client.js`
    - `http://www.google.com/jsapi?autoload=%7B%22modules%22%3A%5B%7B%22name%22%3A%22search%22%2C%22version%22%3A%221.0%22%2C%22callback%22%3A%22__gcse.scb%22%2C%22style%22%3A%22http%3A%2F%2Fwww.google.com%2Fcse%2Fstyle%2Flook%2Fminimalist.css%22%2C%22language%22%3A%22en%22%7D%2C%7B%22name%22%3A%22ads%22%2C%22version%22%3A%223%22%2C%22packages%22%3A%5B%22search%22%5D%2C%22callback%22%3A%22__gcse.sacb%22%7D%5D%7D`
    - `http://www.google.com/cse/style/look/minimalist.css`
    - `http://www.google.com/cse/cse.js?cx=013565259187176721019:0gj-6p_qm34`
    - `http://fonts.googleapis.com/css?family=Source+Sans+Pro:400,700,400italic,700italic|Droid+Serif:400,700,400italic,700italic`
    - `http://www.google.com/csi?s=csa&v=3&action=pplal&rt=jlt.187,ol.228`
    - `http://www.google.com/csi?s=csa&v=3&action=pjsp&rt=pt.2`

* HTTPSB said:
    - ![HTTPSB said it blocked these](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/privacy-tour-1-httpsb.png)
* HTTPSB  allowed these 3rd parties:
    - [none]

### [a few more results coming]