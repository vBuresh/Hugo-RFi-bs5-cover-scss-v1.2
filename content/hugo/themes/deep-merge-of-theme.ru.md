---
date: 2021-06-25T13:03:07+03:00
Lastmod: 2021-06-25T13:03:07+03:00
title: Deep Merge of Theme
subtitle: subtitle of the published article
description: short description of the article
summary: three-line summary of the article.
draft: false
author:
  # given_name: Vladimir
  # family_name: Buresh
  display_name: ['Hugo Authors', 'wBuresh']
categories: [веб-разработка]
# categories: ['web development']
# tags: [CSS, Foundation 6 +,]
tags: [CSS, Темы]
toc: true
---

В версии v0.84.0, помимо ряда исправлений и расширения возможностей Hugo, улучшена обработка конфигурации тем (themes).

## Deep merge of theme Params

До этого в Hugo выполнялось лишь неглубокое слияние параметров темы в конфигурацию.

With that, given this example from a theme configuration:

``` yaml
params:
  colours:
    blue: "#337DFF"
    green: "#68FF33"
    red: "#FF3358"
```

If you would like to use the above theme, but want a different shade of red, you earlier had to copy the entire block, even the colours you're totally happy with. This was painful even the simplest setup.

Now you can just override the params keys you want to change, e.g.:

``` yaml
params:
  colours:
    red: "#fc0f03"

For more information, and especially about the way you can opt out of the above behaviour, see [Merge Configuration from Themes](https://gohugo.io/getting-started/configuration/#merge-configuration-from-themes).

## Themes now support the config directory

Now both the project and themes/modules can store its configuration in both the top level config file (e.g. config.toml) or in the config directory. See [Configuration Directory](https://gohugo.io/getting-started/configuration/#configuration-directory).
