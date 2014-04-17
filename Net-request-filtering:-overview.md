<p align="center">
    <img src="https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-overview.png" />
</p>

## Matrix filtering: overview

Matrix filtering uses a inheritance model to transfer the block or allow status of a node to a lower precedence node:

<p align="center">
    <img src="https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-mtxfiltering-overview.png" />
</p>

To use a concrete example, let's take the following URL: `https://www.example.com/image.png`.

The hostname and the type of the request is extracted from the URL:

- Hostname: `www.example.com`
- Type: `image`

To evaluate whether the request should be blocked or allowed, matrix filtering will first look-up the block/allow status using exactly the hostname and type:

- Is `image` from `www.example.com` whitelisted?
- Yes: request is allowed
- No: Is `image` from `www.example.com` blacklisted?
- Yes: request is blocked
- No: Go up one step in the precedence hierarchy
- Is `image` from `example.com` whitelisted?
- Yes: request is allowed
- No: Is `image` from `example.com` blacklisted?
- Yes: request is blocked
- No: Go up one step in the precedence hierarchy
- Is everything from `example.com` whitelisted?
- Yes: request is allowed
- No: Is everything from `example.com` blacklisted?
- Yes: request is blocked
- No: Go up one step in the precedence hierarchy
- Is `image` from anywhere whitelisted?
- Yes: request is allowed
- No: Is `image` from anywhere blacklisted?
- Yes: request is blocked
- No: Go up one step in the precedence hierarchy
- Is everything from anywhere whitelisted?
- Yes: request is allowed
- No: Is everything from anywhere blacklisted?
- Yes: request is blocked

Actually, things are a bit more complicated, as the pseudo-code above doesn't take into account that hostname/type nodes inherit from two ancestors. HTTPSB deals with the ambiguity by allowing such requests **if and only if** both ancestor nodes evaluate as "allowed". However, if strict blocking is disabled, the hostname ancestor node has precedence over the type ancestor node.

The hierarchical evaluation in matrix filtering allows a user to easily toggle whole set of block/allow permissions by just blacklisting or whitelisting a single node. For instance, whitelisting (or blacklisting) the "all" node allows to turn all graylisted descendant nodes into allow (or block) mode.