---
title: Favicons
description: иконка сайта, его «визитка»
date: 2021-06-09T16:52:00+03:00
Lastmod: 2021-06-09T16:52:00+03:00
draft: false
# summary: ответ на вопрос - «зачем читать я буду это?»
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [веб-разработка]
# categories: ['web development']
tags: [SVG, favicons, icons]
toc: true
---

В тему:

- HoroSamiK (она же Ульяна - UX/UI дизайнер) [Создание favicon для сайта 2020](https://habr.com/ru/post/522844/), Хабр: 10.10.2020

## форматы favicon

Все началось с иконок в формате .ICO. Сейчас распространен .PNG и не только. Вот, пожалуй минимально достаточный перечень


{{< highlight html>}}
<link rel="apple-touch-icon" href="/assets/img/favicons/apple-touch-icon.png" sizes="180x180">
<link rel="icon" href="/assets/img/favicons/favicon-32x32.png" sizes="32x32" type="image/png">
<link rel="icon" href="/assets/img/favicons/favicon-16x16.png" sizes="16x16" type="image/png">
<link rel="manifest" href="/assets/img/favicons/manifest.json">
<link rel="mask-icon" href="/assets/img/favicons/safari-pinned-tab.svg" color="#00d1b2">
<link rel="icon" href="/assets/img/favicons/favicon.ico">
<meta name="theme-color" content="#00d1b2">
{{< highlight html>}}
{{< /highlight >}}


Еще кое что о favicons и форматах:

Size                | File name                        | Purpose
--------------------|----------------------------------|-----------------------------------------------------------
114 x 114 | apple-touch-icon-precomposed.png | для: iPhone, iPod Touch, iPad и Android
110 x 110 | facebook.png                     | использует  Facebook для репостов и лайков
64 x 64   | favicon64.png                    | применяет IE; и браузеры поддерживающие высокое разрешение
32 x 32   | favicon32.png                    | &nbsp;
24 x 24   | favicon24.png                    | &nbsp;
16 x 16   | favicon16.png                    | &nbsp;


## Online Generator

[Favicon Generator. For real](https://realfavicongenerator.net/)
{{< highlight html>}}
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="manifest" href="/site.webmanifest">
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">
{{< /highlight >}}
