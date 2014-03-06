The parsing and enforcing of Adblock Plus ("ABP") complex filters (those filters which purpose is to block more than just a plain hostname) was introduced in version 0.8.4.0 (an about face to [my resistance to support ABP filter syntax](/gorhill/httpswitchboard/issues/149#issuecomment-32471021)).

So here is a collection of observations and facts randomly thrown for the record regarding the use of ABP complex filters by HTTPSB.

#### How much do the ABP complex filters contribute to the blocking power of HTTPSB?

I ran [this benchmark](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites) and obtained the following result:

- With HTTPSB with out-of-the-box settings: Adblock+ complex filters blocked 110 requests -- **22.4% of all blocked requests**.
- With HTTPSB in [allow-all/block-exceptionally](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-allow-allblock-exceptionally-approach) mode: Adblock+ complex filters blocked 425 requests -- **32.4% of all blocked requests**.

I have to say I was rather surprised to see that ABP complex filters still contributed to block over 22% of requests when using HTTPSB with it's very restrictive out-of-the-box settings.

#### Did you get code from Adblock Plus project to implement this feature?

No code was borrowed from ABP, and no code was inspired by ABP's code: I actually didn't even want to look at ABP code before starting, in order to keep a complete "blank slate" mind on to how best implement this with regard to performance and memory footprint.

Once I came up with my own approach, I did look at ABP code in order to understand why the huge memory footprint (at least the Chromium version, I don't know about the Firefox version) and the overall performance. My findings is that there are key areas which can be improved in Adblock Plus, and one is the hashing mechanism used to store the filters in its dictionary.

With HTTPSB, this was the first problem I saw with the first prototype of code to store the filters. Using only the tokens extracted from the filter was causing some entries in the dictionary to contain way to many filter instances, whereas each of these filter instances have to be checked for a match.

So the challenge was to find a way to increase the number of bits in the hash, and the solution I came up with is to see a token as an **anchor** in the string to test. When the tokens are seen as anchors, then whatever characters surrounding a token-anchor can be used to contribute bits to the hash value. This allows to reduce **significantly** the maximum number of filters to process per dictionary entry. This results in more dictionary entries, but with less items in them. Since looking-up a dictionary entry is always fast, the important part is to reduce the maximum number of filters to test per entry. This was the first key step to good performance.

Another problem with ABP current implementation is the use of regular expression to test filter entries. I learned a while ago now that for performance critical code using Javascript, and to maintain smaller memory footprint, avoid using regular expression *whenever possible*. HTTPSB simply uses `String.indexOf` to match a filter against a target portion of the URL, which is [significantly faster](http://jsperf.com/regexp-vs-indexof) than using regular expression -- and also easier on memory footprint.