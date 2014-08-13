---
layout: page
title: Gleb Mazovetskiy
github_url: https://github.com/glebm
profile_image: glebm.jpg
---

**1) Who are you, and what do you do?**

I am a nomadic [software developer](https://github.com/glebm) and an [entrepreneur](https://www.linkedin.com/in/glebm). Lately I've been moving around Europe.

**2) What's your involvement and background with Rails I18n?**

I started using Rails I18n when working on [Just Landed](http://www.justlanded.com/), a web portal connecting expats in 150 countries and 16 languages. Later I wrote a tool ([i18n-tasks][i18n-tasks]) to handle the common pitfalls of maintaining large locale files.

**3) Let's say I'm a completely new developer just getting into I18n for the very first time. I've read the docs, and I'm ready to roll. What surprises will I encounter, still? What are some of the common pitfalls people stumble on?**

As you are getting started with i18n, complexity and diversity of language rules might surprise you. For example, in Rails I18n you can specify plural keys, and one is automatically selected based on the `count` interpolation variable:

```yaml
friends:
  one:   '%{count} friend'
  other: '%{count} friends'
```

```rb
t('friends', count: 10) #=> "10 friends"
```

However, some languages use [declension](http://en.wikipedia.org/wiki/Declension) when counting. In Russian, the noun changes based on *the last digit*:

| Last digit       | Declension case     | Examples (transliterated) |
|------------------|---------------------|---------------------------|
| 1                | Nominative Singular | 1 drug, 21 drug           |
| 2 3 4            | Genetive Singular   | 2 druga, 33 druga         | 
| 0 5 6 7 8 9      | Genetive Plural     | 5 druzej, 10 druzej       |

Thanks to i18n gem modularity, Russian pluralization can be supported with a custom backend. You can find these backends for many languages on Github.

Interpolations are a key feature of i18n gem, but be careful if you use them: 

```yaml
page_title: '%{category} Jobs'
categories:
  dev: 'Developer'
```

In English, both of the keys above can be used. However, interpolating the value will likely result in an incorrect sentence in languages with declensions. 

```rb
# Either this makes no sense in Russian
t('page_title', category: I18n.t('categories.dev'))
# Or this makes no sense in Russian
t('categories.dev')
```

The easiest way to deal with this is to separate the keys out:

```yaml
page_title: 'Developer Jobs'
categories:
  dev: 'Developer'
```

Gems such as [i18n-inflector][i18n-inflector] enable using multiple word forms in the translations. However, separating the keys out is generally better, as it spares translators from working with these codes. 

**4) Rails I18n is the core -- but there are many tools that can help developers make use of it. What are some of your favorite extras? What are the coolest tools to add on top of Rails I18n for maximum comfort and speed?**

[i18n-tasks][i18n-tasks] is a tool I [wrote](http://blog.glebm.com/2014/02/27/i18n-made-easier-with-static-analysis.html) to find missing and unused translations automatically with static analysis. It can also pre-fill the missing ones, using a placeholder or Google Translate. 

If you use ActiveRecord have a look at [globalize][globalize] for model and data translation. 

For actual translation, there are commercial SaaS front-ends such as [Locale][localeapp], and open source ones such as [translation_center](https://github.com/badrit/translation_center). 

My favourite IDE for this is RubyMine, it autocompletes keys, and shows values where the keys are used.

[i18n-tasks]: https://github.com/glebm/i18n-tasks
[i18n-inflector]: https://github.com/siefca/i18n-inflector
[localeapp]: https://www.localeapp.com/
[globalize]: https://github.com/globalize/globalize