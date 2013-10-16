# HTTP Switchboard: Extremely quick tour

(I am working on better doc...)

![An example](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/001.png)

Description of what is going on in the above snapshot of HTTP Switchboard matrix:

- Dark red means: expressly blacklisted. In the above picture, 'master switch' ('all'), 'facebook.com', 'facebook.net' and 'cookie @ radio-canada.ca' are all expressly blacklisted.
- Dark green means: expressly whitelisted.
- Pale red and pale green means the cells are graylisted, which means they inherit their blacklist or whitelist status from a cell with a higher precedence.
- The number in the smaller cells indicate the number of distinct requests for a specific type of items for a specific domain.
- Precedence hierarchy is as follow, from highest precedence to lowest precedence:
    - Specific type/specific domain, like the 'cookie/radio-canada.ca' cell in the above picture.
    - Any type/specific domain, like the 'facebook.com' cell in the picture above.
    - Specific type/any domain, like the 'image' cell in the picture above.
    - Any type/any domain, which is essentially the 'master switch'.
- In the top left corner, the 'all' cell (the "master switch") is dark red, which means: "blacklist all graylisted cells *by default*".
- At the top, the 'image' cell is dark green, which means: "override the 'master switch' state and whitelist all images *by default*". The little green half-circle on the left of the cell means: "remember my whitelist state next time chromium is launched".
- On the left, second row, the 'radio-canada.ca' cell is dark green, which means: "override 'master switch' and 'typed' cells states and whitelist everything from 'radio-canada.ca' and its subdomains". Notice there is no little half-circle on this cell, which means the cell will be back to its natural graylist status next time chromium is launched. All cells are naturally graylisted, execpt for the 'master switch'.
- At the intersection of the 'cookie' cell and 'radio-canada.ca' cell, the is a dark red cell with the number '8' in it, which means: "blacklist all 'cookies' from 'radio-canada.ca'".
- All the sites which are automatically blacklisted using community-contributed lists are permanently blacklisted. You can temporarily gray or whitelist them, but next time you launch chromium, they will be back to being expressly blacklisted.
- So you can fiddle as much as you want with the black, gray or whitelist status, all will be reset next time chromium launches. (This is the opposite of other blockers where temporary unblocking is an exception.)