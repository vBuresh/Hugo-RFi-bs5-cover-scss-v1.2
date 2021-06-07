---
title: "Hugo поддержка SVG"
date: 2019-11-13T19:35:27+03:00
draft: true
# description: "- дополнение к заголовку (подзаголовок)"
# summary: краткое изложение - зачем читать сие
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
toc: true
categories:
  - webDev
tags:
  - Hugo
  - SVG
---

Inline SVGs can be styled with CSS. Is there already a way to inline SVGs in templates (and maybe also with a shortcode)?

This could be done with a partial, but is that the best way?

Встроенные SVG могут быть стилизованы с помощью CSS. Есть ли способ встроить SVG в шаблоны (и, возможно, также с помощью шорткода)?

Это может быть сделано с partial, но это лучший способ?

``` Hugo
{{ partial "img/icons.svg"  }}
```

> This could be done with a partial, but is that the best way?

An SVG can be inlined by using readfile (or a readfile shortcode). It may be necessary to change the width, height, id, and/or class attributes of the `<svg>` tag; or to wrap the element in a `<div>` with an id and/or class.

SVG может быть встроен с помощью `readfile` (или шорткода `readfile`). Может потребоваться изменить атрибуты width, height, id и/или class тега `<svg>`; или обернуть элемент в `<div>` с идентификатором и/или классом.


``` go
{{ readFile "/static/img/filename.svg" }}
```

## Use readFile

См. документацию - [Use readFile](https://gohugo.io/templates/files/#use-readfile)

The [`readfile` function](https://gohugo.io/functions/readfile/) reads a file from disk and converts it into a string to be manipulated by other Hugo functions or `added as-is`. readFile takes the file, including path, as an argument passed to the function.

    To use the readFile function in your templates, make sure the path is relative to your Hugo project’s root directory:

``` go
  {{ readFile "/content/templates/local-file-templates" }}
```

## readFile Example: Add a Project File to Content

As readFile is a function, it is only available to you in your templates and not your content. However, we can create a simple [shortcode template](https://gohugo.io/templates/shortcode-templates/) that calls readFile, passes the first argument through the function, and then allows an optional second argument to send the file through the Blackfriday markdown processor. The pattern for adding this shortcode to your content will be as follows:

{{< highlight go >}}

{{ < readfile file="/path/to/local/file.txt" markdown="true" >}}

{{< /highlight >}}


>If you are going to create custom shortcodes with readFile for a theme, note that usage of the shortcode will refer to the project root and not your themes directory.






См. документацию -  [Includes](https://gohugo.io/templates/introduction/#includes)




[Inject an SVG file into my HTML](https://discourse.gohugo.io/t/solved-inject-an-svg-file-into-my-html/7446)
