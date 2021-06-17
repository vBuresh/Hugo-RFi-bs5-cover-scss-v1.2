---
title: "Hugo поддержка SVG"
date: 2019-11-13T19:35:27+03:00
Lastmod: 2021-06-08T16:43:44+03:00
draft: false
# description: "- дополнение к заголовку (подзаголовок)"
# summary: краткое изложение - зачем читать сие
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: ['примеры']
tags: ['hugo', 'SVG']
toc: true
---



Inline SVGs can be styled with CSS. Is there already a way to inline SVGs in templates (and maybe also with a shortcode)?

This could be done with a partial, but is that the best way?


Встроенные SVG могут быть стилизованы с помощью CSS. Есть ли способ встроить SVG в шаблоны (и, возможно, также с помощью шорткода)?

Это может быть сделано с partial, но это лучший способ?

[Using dict to pass multiple values to a partial](https://gohugo.io/functions/dict/#example-using-dict-to-pass-multiple-values-to-a-partial)

``` Hugo
{{ partial "img/icons.svg"  }}
```

## Example: Using dict to pass multiple values to a partial

The partial below creates a SVG and expects fill, height and width from the caller:

### Partial definition

layouts/partials/svg/rfi-hugo-logo.svg

```
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
fill="{{ .fill }}" width="{{ .width }}" height="{{ .height }}" viewBox="0 0 32 32" aria-label="External Link">
<path d="M25.152 16.576v5.696q0 2.144-1.504 3.648t-3.648 1.504h-14.848q-2.144 0-3.648-1.504t-1.504-3.648v-14.848q0-2.112 1.504-3.616t3.648-1.536h12.576q0.224 0 0.384 0.16t0.16 0.416v1.152q0 0.256-0.16 0.416t-0.384 0.16h-12.576q-1.184 0-2.016 0.832t-0.864 2.016v14.848q0 1.184 0.864 2.016t2.016 0.864h14.848q1.184 0 2.016-0.864t0.832-2.016v-5.696q0-0.256 0.16-0.416t0.416-0.16h1.152q0.256 0 0.416 0.16t0.16 0.416zM32 1.152v9.12q0 0.48-0.352 0.8t-0.8 0.352-0.8-0.352l-3.136-3.136-11.648 11.648q-0.16 0.192-0.416 0.192t-0.384-0.192l-2.048-2.048q-0.192-0.16-0.192-0.384t0.192-0.416l11.648-11.648-3.136-3.136q-0.352-0.352-0.352-0.8t0.352-0.8 0.8-0.352h9.12q0.48 0 0.8 0.352t0.352 0.8z"></path>
</svg>
```

### Partial call

The fill, height and width values can be stored in one object with dict and passed to the partial:

`layouts/_default/list.html`

``` html
{{ partial "svgs/external-links.svg" (dict "fill" "#01589B" "width" 10 "height" 20 ) }}
---

> This could be done with a partial, but is that the best way?

An SVG can be inlined by using readfile (or a readfile shortcode). It may be necessary to change the width, height, id, and/or class attributes of the `<svg>` tag; or to wrap the element in a `<div>` with an id and/or class.

SVG может быть встроен с помощью `readfile` (или шорткода `readfile`). Может потребоваться изменить атрибуты width, height, id и/или class тега `<svg>`; или обернуть элемент в `<div>` с идентификатором и/или классом.


``` go
{ readFile "/static/img/filename.svg" }2
```

## Use readFile

См. документацию - [Use readFile](https://gohugo.io/templates/files/#use-readfile)

The [`readfile` function](https://gohugo.io/functions/readfile/) reads a file from disk and converts it into a string to be manipulated by other Hugo functions or `added as-is`. readFile takes the file, including path, as an argument passed to the function.

    To use the readFile function in your templates, make sure the path is relative to your Hugo project’s root directory:

``` go
  2{ readFile "/content/templates/local-file-templates" }
```

## readFile Example: Add a Project File to Content

As readFile is a function, it is only available to you in your templates and not your content. However, we can create a simple [shortcode template](https://gohugo.io/templates/shortcode-templates/) that calls readFile, passes the first argument through the function, and then allows an optional second argument to send the file through the Blackfriday markdown processor. The pattern for adding this shortcode to your content will be as follows:

{{< highlight go >}}

{{ < readfile file="/path/to/local/file.txt" markdown="true" >}}

{{< /highlight >}}


>If you are going to create custom shortcodes with readFile for a theme, note that usage of the shortcode will refer to the project root and not your themes directory.






См. документацию -  [Includes](https://gohugo.io/templates/introduction/#includes)




[Inject an SVG file into my HTML](https://discourse.gohugo.io/t/solved-inject-an-svg-file-into-my-html/7446)
