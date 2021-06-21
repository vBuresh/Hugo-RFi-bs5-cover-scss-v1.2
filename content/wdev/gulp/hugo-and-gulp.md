---
title: "Hugo с Gulp-ом"
subtitle: "- почти «залпом"
date: 2019-11-27T04:53:05+03:00
Lastmod: 2021-06-21T12:17:21+03
draft: false
description: "Очень интересное сочетание двух замечательных программ."
summary:  "Великолепные возможности Hugo удачно дополняются задачами Gulp в части подготовки и включения в проект стилей (SASS, SCSS, CSS), JS, изображений, аудио- и видео-материалов а также их своевременного обновления."
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [Веб-разработка]
# categories: ['web development']
tags: [Hugo, Gulp]
toc: true
---

# Building a production website with Hugo and GulpJS

Своему вдохновению обязан Дану Бахрами (Dan Bahrami) и его интересной статье [Using Gulp and UnCSS in Combination with Sass based Hugo themes](https://markus.oberlehner.net/blog/using-gulp-and-uncss-in-combination-with-sass-based-hugo-themes/), написанной еще в марте 2016 года. Конечно, с момента её написанияи произошли серьезные изменения. [Gulp](http://gulpjs.com) теперь поставляется в версии 4. Она существенно отличается от предыдущей. А [Hugo](https://gohugo.io) удерживает знание самого быстрого в мире фреймворка для создания вебсайтов.

Как отмечается на сайте [Hugo](https://gohugo.io), он является одним из наиболее популярных свободных генераторов статических сайтов (open-source static site generator - SSG). Благодаря своей удивительной скорости и гибкости, **Hugo** снова делает создание веб-сайтов увлекательным.

Я всегда с особой симпатией относился и отношусь к статическим сайтам. И собирал их при помощи **Gulp**. Но идея применения статического генератора сайтов мне очень понравилась.

Особенно порадовала, сочетаемость великолепных возможностей **Hugo** с обширным функционалом [Gulp](http://gulpjs.com) в части подготовки и включения в прект соответствующих ресурсов: стилей (SASS, SCSS, CSS), JS и изображений, а также их своевременного обновления.

Итак начнем

{{&lt; highlight bash "linenos=true,hl_lines=4 11,linenostart=27" >}}
 vblog
 ├── /archetypes
 ├── /config.toml
 ├── /content
 ├── /data
 ├── /layouts
 ├── /static
 └── /themes
   config.toml (.yaml, .json)
{{&lt; /highlight >}}

## Building a Gulp pipeline

  <p>The end result we want is a set of compiled assets to be placed in the <code>static/</code> directory for Hugo to use in it’s compile step. This will be Gulp’s output destination so we need a directory to keep our pre-processed working files. I like to keep mine in a <code>src/</code> directory. I will also create separate directories inside for SCSS, JS and images.</p>

Конечный результат, который нам нужен, - это набор скомпилированных ресурсов, которые нужно поместить в каталог <code> static / </code>, чтобы Hugo использовал на этапе компиляции. Это будет выходной каталог Gulp, поэтому нам нужен каталог для хранения предварительно обработанных рабочих файлов. Мне нравится хранить мои в каталоге <code> src / </code>. Я также создам отдельные каталоги внутри для SCSS, JS и изображений.

`mkdir -p src/{scss,js,images}`

``` html

```

`npm install --save-dev gulp`
