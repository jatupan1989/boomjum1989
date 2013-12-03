By design, whitelist and blacklist rules are temporary by default. Once you are satisfied with a rule, to make it permanent, you must lock it down:

![How to make a rule permanent](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/rule-padlock.gif)

This is by design. At first, this may feel bothersome when you need to create all the set of rules for the web  sites you trust completely. Eventually, soon enough, once all your basic set of rules is created, you will be happy that rules are temporary by default.

This way you won't end up bloating your ruleset for the common case of just unblocking a web page which you don't want to permanently whitelist.