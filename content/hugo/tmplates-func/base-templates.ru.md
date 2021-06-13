---
title: Базовае шаблоны и блоки
# subtitle: continuer of the title in a two words
date: 2021-06-09T08:36:12+03:00
Lastmod: 2021-06-09T08:36:12+03:00
draft: false
description: The base and block constructs allow you to define the outer shell of your master templates (i.e., the chrome of the page).
# summary: краткое изложение - зачем читать сие
# summaryImage: images/
author:
  display_name: [Hugo Authors]
categories: [примеры']
tags: [hugo, шаблоны]
toc: true
---

The `block` keyword allows you to define the outer shell of your pages' one or more master template(s) and then fill in or override portions as necessary.

В руководстве Hugo сказано, что ключевое слово `block` позволяет определять внешнюю оболочку пользовательских страниц - один или несколько основных шаблонов, а затем при необходимости заполнить или переопределить соответствующие части. Подробнее... [Base Templates and Blocks](https://gohugo.io/templates/base/)

См. также ролик от специалистов Hugo:

{{< youtube id="QVOMCYitLEc" class="mb-3" title="Hugo о шаблонах и блоках" >}}

## Порядок поиска в базовом шаблоне

Порядок поиска в базовом шаблоне точно следует шаблону, к которому он применяется. То есть ищется макет для данной страницы в четко определенном порядке. Начинается поиск - с самого конкретного
(e.g. `_default/list.html`). Подробнее... [Template Lookup Order](https://gohugo.io/templates/lookup-order/)

## Определяем базовый шаблон

Простой базовый шаблон по умолчанию:  `_default / baseof.html`. Представляет собой оболочку, из которой будут отображаться все сайта, если не будет указан другой `* baseof.html`, расположенный ближе к началу порядка поиска.

{{< highlight html "linenos=table">}}

  <!DOCTYPE html>
  <html>
    <head>
      <meta charset="utf-8">
      <title>{{ block "title" . }}
        <!-- Blocks may include default content. -->
        {{ .Site.Title }}
      {{ end }}</title>
    </head>
    <body>
      <!-- Code that all your templates share, like a header -->
      {{ block "main" . }}
        <!-- The part of the page that begins to differ between templates --  >
      {{ end }}
      {{ block "footer" . }}
      <!-- More shared highlight, perhaps a footer but that can be   overridden if need be in  -->
      {{ end }}
    </body>
  </html>
{{< /highlight >}}

## Override the Base Template

From the above base template, you can define a [default list template][hugolists]. The default list template will inherit all of the highlight defined above and can then implement its own `"main"` block from:

{{< highlight html >}}
{{ define "main" }}
  <h1>Posts</h1>
  {{ range .Pages }}
    <article>
      <h2>{{ .Title }}</h2>
      {{ .Content }}
    </article>
  {{ end }}
{{ end }}
{{< /highlight >}}

This replaces the contents of our (basically empty) "main" block with something useful for the list template. In this case, we didn't define a `"title"` block, so the contents from our base template remain unchanged in lists.

Внимание!
:Code that you put outside the block definitions *can* break your layout. This even includes HTML comments. For example:

```
<!-- Seemingly harmless HTML comment..that will break your layout at build -->
{{ define "main" }}
...your highlight here
{{ end }}
```
[See this thread from the Hugo discussion forums.](https://discourse.gohugo.io/t/baseof-html-block-templates-and-list-types-results-in-empty-pages/5612/6)


The following shows how you can override both the `"main"` and `"title"` block areas from the base template with highlight unique to your [default single page template](https://gohugo.io/templates/single-page-templates/):

{{< highlight go >}}
{{ define "title" }}
  {{ .Title }} &ndash; {{ .Site.Title }}
{{ end }}
{{ define "main" }}
  <h1>{{ .Title }}</h1>
  {{ .Content }}
{{ end }}
{{< /highlight >}}
