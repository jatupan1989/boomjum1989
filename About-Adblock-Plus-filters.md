The parsing and enforcing of Adblock Plus ("ABP") complex filters (those filters which purpose is to block more than just a plain hostname) was introduced in version 0.8.4.0 (an about face to [my resistance to support ABP filter syntax](/gorhill/httpswitchboard/issues/149#issuecomment-32471021)).

So here is a collection of observations and facts randomly thrown for the record regarding the use of ABP complex filters by HTTPSB.

#### How much do the ABP complex filters contribute to the blocking power of HTTPSB?

I ran [this benchmark](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites) and obtained the following result:

- With HTTPSB with out-of-the-box settings: Adblock+ complex filters blocked 110 requests -- or 22.4% of all blocked requests.
- With HTTPSB in [allow-all/block-exceptionally](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-allow-allblock-exceptionally-approach) mode: Adblock+ complex filters blocked 425 (32.4% of all blocked requests.