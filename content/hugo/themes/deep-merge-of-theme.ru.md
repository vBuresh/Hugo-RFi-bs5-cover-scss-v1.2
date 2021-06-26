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

До этого в Hugo выполнялось лишь неглубокое слияние параметров темы в конфигурацию:

``` yaml
params:
  colours:
    blue: "#337DFF"
    green: "#68FF33"
    red: "#FF3358"
```

Если вы хотите использовать указанную выше тему, но хотите другого оттенка красного, вам раньше приходилось копировать весь блок, даже те цвета, которые вам полностью нравятся. Это было болезненно даже в самой простой установке.

Теперь достаточно переопределить ключи параметров, которые нужно изменить, например:

``` yaml
params:
  colours:
    red: "#fc0f03"
```

Для получения дополнительной информации, и особенно о том, как вы можете отказаться от вышеуказанного действия, см. [Merge Configuration from Themes](https://gohugo.io/getting-started/configuration/#merge-configuration-from-themes).

## Themes now support the config directory

Теперь и проект, и темы / модули могут хранить свою конфигурацию как в файле конфигурации верхнего уровня (например, config.toml), так и в каталоге конфигурации. См. [Configuration Directory](https://gohugo.io/getting-started/configuration/#configuration-directory).
