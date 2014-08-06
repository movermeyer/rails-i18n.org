---
layout: page
title: Christopher Dell // tigrish
github_url: https://github.com/tigrish
profile_image: https://avatars2.githubusercontent.com/u/37666
---

**1) Who are you, and what do you do?**

I’m an entrepreneur and Ruby developer living in France’s gastronomic capital, Lyon, with my wife and baby daughter. In what little spare time I have, I organise a tasty food-focused tech conference in Paris called La Conf.

During the day, my “real” job is managing a localization app for Rails developers called [Locale](http://www.localeapp.com).

**2) What’s your involvement and background with Rails I18n?**

I started contributing to rails-i18n back in 2011 and since then I’ve dabbled in a whole load of related projects from i18n itself to ruby-cldr.

I also maintain a few of my own gems that are related to internationalization like [i18n-spec](http://rubygems.org/gems/i18n-spec) to test your locale files, the [iso gem](http://rubygems.org/gems/iso) to get a list of languages and regions and various translations for other existing gems (eg. [devise-i18n](http://rubygems.org/gems/devise-i18n), [kaminari-i18n](http://rubygems.org/gems/kaminari-i18n)).

**3) What made you go into I18n in the first place? **

The need to get involved in I18n came about because of a project I was working on at the time that used languages as a way of expanding into new markets.

That gamble paid off since the project is still happily running and counts over 30 localizations to this date. Booya!

I can’t recommend this strategy enough as often the cost of localization is insignificant compared to the cost of internationalization (which is a one-time thing), so if you support say, two languages, you might as well reap the commercial benefits of having ten languages.


**4) Let’s say I’m a completely new developer just getting into I18n for the very first time. I’ve read the docs, and I’m ready to roll. What surprises will I encounter, still? What are some of the common pitfalls people stumble on?**

First of all, it’s important to acknowledge that internationalization is a very difficult process! Unless, you understand the grammer of every single language on the planet you are probably going to get some things wrong until a native speaker points out a problem to you. But don’t fret, this stuff is super hard and you will figure it out eventually!

The following three tips should help you avoid 80% of the most common mistakes new I18n-ers make (statistic may not be totally accurate):

* Avoid using interpolation whenever possible. It sounds like I’m recommending to discard one of the most basic features of the I18n gem - and that’s absolutely correct! What might seem like an easy interplation to make in English will always, always turn out to be a problem for a different locale because of its need to adjust for things like gender, pluralizations, conjugation and a range of other grammatical particularities. Proper nouns are the only things that seem reasonable to interpolate and even then…
* Do not be ashamed of duplication. I know, this goes against every idea you hold sacred as a developer, but trust me, it will work out better in the long run. This problem pops up very often when using English as the base language and developers are trying to re-use existing translations. The issue here is that other languages often use different words in different contexts, whereas English will use the same one everywhere (stupid English…). Just create a new translation key for that specific context and send it off to your translator with your head held up high: you are winning at I18n.
* I could talk about this last one for hours as it is the source of so much confusion and again, native English speakers (but not only!) find this hard to grasp: pluralization and pluralization rules. We’re used to the idea that when there’s one of something we use the singular form, otherwise we use the plural form. This is actually an accurate description of the pluralization rule for English. In some other very common languages though, the rules are much more complex. Some use the singular form for numbers that end with a 1 like 21, 31, 41 (but often not 11…). Others have multiple plural forms like “few” for the number 4 and “many” for the number 10. It can all get quite mind boggling, but the main takeaway should be to always include a %{count} variable in your pluralization strings - it’s never OK to assume that because we’re dealing with a singular form, that %{count} can be replaced with a 1. The same applies to the “zero” form.

**5) Rails I18n is the core – but there are many tools that can help developers make use of it, like other gems, Web translation front-ends, and even text editor plugins. What are some of your favorite extras? What are the coolest tools to add on top of Rails I18n for maximum comfort and speed?**

Obviously I’m biased towards using Locale as a translation managment tool, but there are now many other excellent options like [Phraseapp](http://phraseapp.com/) or [Transifex](https://opentranslators.transifex.com/).

There’s a project by Gleb Mazovetskiy that I’m really in admiration of called [i18n-tasks](https://github.com/glebm/i18n-tasks) that has a whole range of commands to help you manage your locale files - I highly recommend checking it out!