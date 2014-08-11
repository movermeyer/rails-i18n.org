---
layout: page
title: Henrik Nyh
github_url: https://github.com/henrik
profile_image: https://avatars1.githubusercontent.com/u/216
---

**1) Who are you, and what do you do?**

I'm Henrik Nyh, a Swedish web developer working for [Barsoom](http://barsoom.se), mostly on [Auctionet.com](http://auctionet.com).

**2) What's your involvement and background with Rails I18n?**

I've worked with localized sites for the last five years or so. I was part of localizing my previous employer's site to Swedish, English and Finnish, and Auctionet.com has Swedish, English and German.

I've contributed [some minor fixes](https://github.com/svenfuchs/rails-i18n/commits?author=henrik) to the Swedish rails-i18n defaults, and written some i18n tools.

**3) What made you go into I18n in the first place?**

While it was my employer's needs that made me start working with i18n, I've definitely taken a larger interest in it than my co-workers have.

I guess it helped that I studied linguistics at university and have a degree in computational linguistics. I love language, especially quirks of grammar.

I really enjoyed getting to deal with Finnish noun cases at work, but I think I was alone in that…

**4) Let's say I'm a completely new developer just getting into I18n for the very first time. I've read the docs, and I'm ready to roll. What surprises will I encounter, still? What are some of the common pitfalls people stumble on?**

It's easy to forget that locale is independent of e.g. country or currency. If some special circumstances apply only to users in Sweden, don't just stick them in the Swedish translations. You may have both Swedish-locale and English-locale visitors in Sweden. And both Swedish-locale and English-locale visitors in another country.

Another pitfall is the quirks of the YML format. Make sure to use quotes around any of the values "true", "false", "yes", "no", "on", "off", "y", "n" or they may be treated as booleans rather than strings.

And one thing you may not realize is that a non-negligible part of i18n is unbreaking layouts. Some of those long Finnish words may make your spacious English layout burst. Or replacing an English word with a single Chinese character may leave it looking bare.

**5) Rails I18n is the core -- but there are many tools that can help developers make use of it, like other gems, Web translation front-ends, and even text editor plugins. What are some of your favorite extras? What are the coolest tools to add on top of Rails I18n for maximum comfort and speed?**

We plan on looking into translation front-ends quite soon. We've been getting by with asking in-house translators and updating our YML files, but it's getting increasingly inconvenient.

At my last job, we used [webtranslateit](https://webtranslateit.com) which was OK, but not great. I haven't looked in years, though.

I [wrote up some i18n tips](http://thepugautomatic.com/2012/07/rails-i18n-tips/) a while back, which includes some tools, like [vim-yaml-flattener](https://github.com/henrik/vim-yaml-flattener) to edit YML files flattened ("sv.items.show.title") instead of nested.

My [i18n_utils](https://github.com/henrik/i18n_utils) library has convenient `t_model` and `t_attribute` helpers; I don't like the default Rails APIs for model and attribute name translations.

We built the [Traco](https://github.com/barsoom/traco) library for translated model attribute values. It uses per-locale columns in your model for simplicity. If you want separate translation tables (perhaps if you have a lot of locales), have a look at [Globalize](https://github.com/globalize/globalize).