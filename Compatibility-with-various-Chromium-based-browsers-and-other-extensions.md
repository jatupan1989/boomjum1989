**TL;DR I can't guarantee HTTPSB will run flawlessly on a development version of a Chromium-based browser.**

**TL;DR I can't guarantee HTTPSB will run flawlessly when installed aside an other extension which also modifies HTTP headers.**

I develop and test HTTPSB using the latest official releases of Chromium (currently v34/Linux).

Before publishing to their respective web stores, I test Chrome (v34/Linux&Windows) and Opera (v20/Windows). Once in a while I test the official release of Yandex (it has been a while though). I guess I should set-up a _development_ version of Chromium, but I do not have much time currently to do so.

I know it often happens people report that HTTPSB has some malfunctions with a development version of one of the Chromium-based browsers, malfunctions which I often can't reproduce on an official release.

### Compatibility with other extensions

I will list here known issues, benign or serious, with other extensions.

### Any extension which modifies request and/or response headers

**NOT COMPATIBLE.**

"Not compatible" in the strictest sense, but sometimes the parts that are "broken" may not be enough to justify the removal of the "incompatible" extension.

Chrome API allows [only **ONE** extension to modify request or response headers](https://developer.chrome.com/extensions/webRequest#implementation), and the last one installed wins.

Since modifying request and response headers is **key** for HTTPSB to perform its duty reliably (disabling javascript execution, stripping outgoing cookies, referer, etc.), consider that any extension which requires modifying HTTP headers is strictly incompatible with HTTPSB: One of the two extensions won't be able to do its job, which in the case of HTTPSB is **critical**.

Note that their is no way for HTTPSB to find out and notify the user on whether it failed to properly modify the headers, so you are ultimately responsible for ensuring HTTPSB is the **only extension installed** which modifies headers, or its the **last one installed** (in which case other extensions which modify headers won't work properly).

This warning applies to all extensions listed below, I didn't specifically check whether they modify HTTP headers, so aside the specific issues found, you will have to ensure as well they do not modify HTTP headers.

I know many users install other sort of blockers alongside HTTPSB, so if any of these blockers modifies the headers, than the resulting protection you get **could be less** than if you were using any of them alone.

[TODO: feature comparison with other blockers so that people can make an informed choice]

[TODO: provide diagnostic pages at <http://raymondhill.net/httpsb>]

### [Adblock Plus](https://chrome.google.com/webstore/detail/adblock-plus/cfhdojbkjhnklbpkdaibdccddilifddb)

Compatible.

Both extensions may try to replace the content of `<iframe>` objects with harmless content using a redirect operation. When this happens, the browser will warn of a conflict, but the result is harmless because whoever wins, the `<iframe>` objects will end up being properly neutralized.

### [Privacy Badger](https://www.eff.org/privacybadger) (from EFF)

Strictly speaking, not compatible, but still can be used together meaningfully is you install Privacy Badger with HTTPSB and accept that some of privacy-related features of one of the extensions will not work (reliably).

Both extensions modify outgoing request headers, and since the chrome API (as of Chromium 34) does not allow more than one extension to modify HTTP headers, one of the two extensions may end up being unable to do what is is supposed to do.

As per chrome API, the last extension _installed_ (not the same as _enabled_) wins. So this means:

- If Privacy Badger is installed last, then HTTPSB...
    - will **not** be able to remove outbound cookies as per matrix
    - will still be able to delete them from the browser
    - will **not** be able to strip referer information as per matrix
    - will **not** be able to spoof user-agent information
- If HTTPSB is installed last, then Privacy Badger...
    - will **not** be able to remove outbound cookies as per its own heuristic
    - will **not** be able to inject the [Do Not Track](https://en.wikipedia.org/wiki/Do_Not_Track) header into request headers

After having read how Privacy Badger works, I actually think it is an excellent complementary extension to use aside HTTPSB, **especially** if you use HTTPSB in a permissive way (for example [allow-all/block-exceptionally](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-allow-allblock-exceptionally-approach)).

So if you wish to use HTTPSB along with Privacy Badger, installing Privacy Badger **before** or **after** depends on the results you wish:

If you want Privacy Badger to completely control your outbound cookies as per its own "training" heuristic, install Privacy Badger **after** HTTPSB.

If you want HTTPSB to completely control your outbound cookies as per its matrix state, install HTTPSB **after** Privacy Badger.

Regardless of the choice, Privacy Badger will still be able to be "trained" and block net requests to servers which are deemed untrustworthy (as per "training"), and HTTPSB will still be able to block net requests as per its matrix and ABP filtering engines.

**IMPORTANT:** Privacy Badger relies on being able to perform [XmlHttpRequests](https://en.wikipedia.org/wiki/XMLHttpRequest) to the servers it evaluates (it requests their `dnt-policy.txt` file). Therefore this means you will have to ensure the `XHR` cell in the matrix is whitelisted for the `chromium-behind-the-scene` scope in order to not trip Privacy Badger's evaluation of 3rd-parties.

### [ScriptSafe](https://chrome.google.com/webstore/detail/scriptsafe/oiigbmnaadbkfbmpbfijlflahbdbdgdf)

ScriptSafe doesn't work properly with HTTPSB when scripts are blocked by HTTPSB.

HTTPSB blocks javascript execution using a [Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy) directive (ScriptSafe uses [chrome.contentSettings.javascript.set](https://developer.chrome.com/extensions/contentSettings#property-javascript).)

The use of a Content Security Policy by HTTPSB prevents script files from even being requested, and as a result [chrome.webRequest.OnBeforeRequest](https://developer.chrome.com/extensions/webRequest#event-onBeforeRequest) is not fired for these external files, which causes ScriptSafe to not see the existence of these files, therefore they won't appears in ScriptSafe user interface, therefore they can't be whitelisted.

Allowing 1st-party scripts in HTTPSB causes ScriptSafe to be able to see external scripts.

Since their purpose overlap a lot, my advice is to stick to one extension or the other, and not have both installed and enabled at the same time.
