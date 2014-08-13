---
layout: page
title: Carlos Antonio da Silva
github_url: https://github.com/carlosantoniodasilva
profile_image: https://avatars2.githubusercontent.com/u/26328
---

**1) Who are you, and what do you do?**

My name is Carlos Antonio, I'm currently working at Plataformatec as a Software Developer, and I'm part of the Rails Core Team.


**2) What's your involvement and background with Rails I18n?**


I've been working with Ruby on Rails for around 6~7 years, and I've participated in many different projects, from "rails new" to completely legacy ones. Probably most of them are somehow related to Brazilian companies, which means they generally needed some sort of I18n integration, for displaying texts, error messages, numeric formats, and so on, both for input and output values.

I think I could say I've been a good I18n user for most applications I've worked with, and that's probably gonna stay like that as more and more applications need to be translated to different languages. This also led me to want to work and improve the library and its integration with Rails, to make sure it'll continue be maintained and useful for everyone as it's been for me.


**3) What made you go into I18n in the first place?**

My real contact with I18n internals other than messing around was developing a personal project, [I18n Alchemy](https://github.com/carlosantoniodasilva/i18n_alchemy), which is a small library to receive translated input and convert it to a Ruby format that could be properly handled by Active Record / pure Ruby objects. I started this project back in 2011 as part of the [Ruby Mendicant University](http://mendicantuniversity.org/)  (which now dropped "Ruby" from its name), a project started by Gregory Brown that used to run some classes for improving your Ruby and development skills. It was very challenging for me at that time and I'm still using and maintaining the library.

**4) Let's say I'm a completely new developer just getting into I18n for the very first time. I've read the docs, and I'm ready to roll. What surprises will I encounter, still? What are some of the common pitfalls people stumble on?**

One document I'd definitely recommend newcomers to read is the [I18n Rails guide](http://guides.rubyonrails.org/i18n.html), it contains lots of useful information about the APIs Rails provides for internationalization. It's super important not to be caught up doing manual work that Rails can do for you, for example: automatic translation of mailer subjects, so learning about these APIs is a great start.

Something to keep in mind is how to add HTML to your translations: make sure you never call "raw" or "html_safe" directly on translations that could receive an interpolated user argument, or you might be opening a security hole in your app; use *_html keys in I18n so that Rails will cover you by properly escaping the arguments. There's an example about that on the I18n guide linked above.

And one small thing that keeps bothering me: the localize method of I18n raises in case you don't give it a Date or Time object - and I think that's just fine from the I18n side. But it's very annoying having to add conditionals in our code for optional date/time fields to call this method, so I think that maybe Rails could abstract that for us - or not, maybe that's something we can think more about and fix some day.

Last but not least, learn what you can do with YAML to reuse translations rather than duplicating strings, and make sure to always move your error messages to the locale files rather than adding error strings to your models, this will save you some day.



**Rails I18n is the core -- but there are many tools that can help developers make use of it, like other gems, Web translation front-ends, and even text editor plugins. What are some of your favorite extras? What are the coolest tools to add on top of Rails I18n for maximum comfort and speed?**

I'd definitely recommend taking a look at I18n Alchemy if you need to receive translated input from your users :). Self-promotion apart, I used to use the [delocalize gem](https://github.com/clemens/delocalize) a lot, which does pretty much the same thing but felt a little bit more invasive in its approach to me (that was one of the reasons I have picked up this challenge as my personal project), anyway it used to work nicely. Other gem I usually add to my projects is [rails-i18n](https://github.com/svenfuchs/rails-i18n), which contains all necessary Rails translations for most of the languages.

Besides that, I've used [Locale App](https://www.localeapp.com/) in one project lately to translate texts between 6 different languages. It worked very well for our needs and it was super easy for translators to do their work and for us to sync everything to the app, so I definitely recommend taking a look if you need something like that. Locale App is also used to translate some known open source tools like devise and rails-i18n.