---
title: Hugo-TOC
date: 2019-12-03T21:51:13+03:00
draft: true
summary: Автоматическое формирование оглавления в Hugo
description: "В Hugo предусмотрена возможность автоматического формирования оглавления. Правда, это прекрасно работает только в .md. Автоматически сформировать оглавление html документа пока не удалось. Но можно легко это сделать вручную. Ведь доля html страниц, в проекте невелика. Интересны оба варианта."
tags:
- ReFreshing
- Hugo
---


<!--TODO  Продумать, как лучше
Содержание это перечень, оно описывает краткое название составных частей (глав, параграфов, разделов, ингредиентов, веществ - смотря в каком контексте). Синоним Оглавление

В то время как содержи́мое, это как раз то, что содержится внутри чего-либо : Для книг или статей - это сама текстовая информация; для любых продуктов и веществ - ингредиенты и простые вещества и элементы их составляющие; для механизмов и устройств - части, их составляющие. Иными словами, это то, что содержится внутри "общего целого" объекта. -->

>Википедия
>Оглавле́ние — указатель заголовков издания, отражающий рубрикацию произведения и ускоряющий поиск частей издания.
>
>В оглавлении произведения, разбитого на части, разделы, подразделы, главы, подглавы, параграфы, подпараграфы, примечания и т. п., устанавливающие соподчиненность отдельных частей произведения, последовательно приводятся наименования частей, разделов, глав, параграфов в полном объёме, так, как они даны в тексте, и указываются страницы, на которых начинается рубрика. Рубрики последней ступени — подзаголовки, взятые в тексте рукописи в подбор, — в оглавлении могут не приводиться. Взаимоподчиненность частей произведения в оглавлении передают средствами полиграфического оформления: выделением в красную строку, шрифтами и набором рубрик с отступом от левого края полосы[1].
>
>В отличие от содержания, характеризующего состав сборника произведений, оглавление раскрывает в первую очередь строение произведения в моноиздании (роман, повесть, и т. д.) или только строение сборника (из каких частей или разделов он состоит)[2].


В Hugo предусмотрена возможность автоматического формирования оглавления. Правда, это прекрасно работает только в .md. Автоматически сформировать оглавление html документа пока не удалось. Но можно легко это сделать вручную. Ведь доля html страниц, в проекте невелика. Интересны оба варианта.

# Оглавление для html страниц

_Оглавление_

- [Ссылки с помощью шорткодами](#linksShortcodes)

Одна из первых проблем с которой сталкиваются многие пользователи Hugo. Это ссылки. Для правильного их применения нужно знать некоторые правила и особенности, которые изложены в документации [Links and Cross References](https://gohugo.io/content-management/cross-references/).


## Ссылки с помощью шорткодов

Ссылки на документы указываются **шорткодами**.

{{ ref . "hugo-shortcodes.md" }}

{{< highlight go-html-template >}}
❴❴< ref "/hugo-sass-scss" >❵❵
{{< /highlight >}}

ик

{{< highlight go-html-template >}}
❴❴< relref "/hugo-sass-scss" >❵❵
{{< /highlight >}}

[Шорткоды в Hugo]({{< relref "/shortcodes" >}})

Шорткод `ref` и `relref` разрешает абсолютную или относительную постоянную ссылку, заданную путем к документу.

ref и relref ищут страницу содержимого по логическому имени (ref) или относительному пути (relref), чтобы получить постоянную ссылку:

```
{{ relref . "about.md" }}
```

Шорткод от Poberto Jordaney

``` md
[link to the title](#my-title-id)
```

>relref looks up Hugo “Regular Pages” only. It can’t be used for the homepage, section pages, etc.
relref ищет только «Обычные страницы». Его нельзя использовать для домашней страницы, страниц разделов и т. Д.


Shortcodes for creating links to documents.
The ref and relref shortcode resolves the absolute or relative permalink given a path to a document.

Use ref and relref

### Применение `ref` и `relref`

relref
Поиск страницы содержимого по относительному пути.

Syntax

``` go
relref . CONTENT
```

Единственным параметром для `ref` является строка с именем документа содержимого (например, **about.md**) с или без добавленной привязки в документе (**#who**) без пробелов. Hugo очень гибок в поиске документов, поэтому суффикс файла может быть опущен. Эта гибкость явно почувствовалась при формировании примеров кода. Hugo их сразу принимала всерьез, и в запушенный сервер показывал ошибки (`вывод ошибок в Hugo настраеваемый`). Пришлось даже "стрелки" `< и >` менять на  `&lt; и &gt;` и отказаться от принятой формы демонстрации исходного кода. Поэтому он и приводится списоком и без подстветки.

1. {{&lt; ref "document.md" &gt;}}
1. {{&lt; ref "#anchor" &gt;}}
1. {{&lt; ref "document.md#anchor" &gt;}}
1. {{&lt; ref "/blog/my-post" &gt;}}
1. {{&lt; ref "/blog/my-post.md" &gt;}}
1. {{&lt; relref "document.md" &gt;}}
1. {{&lt; relref "#anchor" &gt;}}
1. {{&lt; relref "document.md#anchor" &gt;}}

Пример применения ссылок:

Обратите внимание, что расширение имени файла назначения
можно не указавать

Работающий пример
[Шорткоды в Hugo]({{< relref "/shortcodes" >}})



``` html
1. ref "hugo-and-gulp.md"
1. ref "hugo-and-gulp"
```

<!-- Hugo 0.32 announced page-relative images and other resources packaged into Page Bundles.

These terms are connected, and you also need to read about Page Resources and Image Processing to get the full picture.

links

- внешние
- внуриенние
  - абсолютные
  - относительные

## Управление URL-адресами
-->

<!-- [Управление URL-адресами](#url-management) -->
Hugo поддерживает:

- постоянные ссылки (permalinks),
- псевдонимы (aliases),
- канонизацию ссылок (link canonicalization),
- несколько вариантов обработки
  - относительных (relative URLs) и
	- абсолютных (absolute URLs) URL-адресов.

<!--
	Permalinks

	The default Hugo target directory for your built website is public/. However, you can change this value by specifying a different publishDir in your site configuration. The directories created at build time for a section reflect the position of the content’s directory within the content folder and namespace matching its layout within the contentdir hierarchy.

	The permalinks option in your site configuration allows you to adjust the directory paths (i.e., the URLs) on a per-section basis. This will change where the files are written to and will change the page’s internal “canonical” location, such that template references to .RelPermalink will honor the adjustments made as a result of the mappings in this option.

	These examples use the default values for publishDir and contentDir; i.e., public and content, respectively. You can override the default values in your site’s config file.

	For example, if one of your sections is called posts and you want to adjust the canonical path to be hierarchical based on the year, month, and post title, you could set up the following configurations in YAML and TOML, respectively.
 -->




## Anchors

Якоря (anchor) указвывются в обычном порядке - после `#`  указывается уникальный идентификатор `id` определенного места текущей статьи (страницы){--: `relref "#anchors"`--}.

Если ссылка должна привести к определенному месту другой статьи (страницы) то, после указания пути и имени {--(с расширением)--} после `#`  указывается уникальный идентификатор `id` определенного места статьи (страницы) назначения.

{{&lt; relref "#anchors" &gt;}} => #anchors:9decaf7

The above examples render as follows for this very page as well as a reference to the “Content” heading in the Hugo docs features pageyoursite
Приведенные выше примеры для этой самой страницы выглядят так же, как и ссылка на заголовок «Content» в Hugo docs functions pageyoursite


{{&lt; relref "#who" &gt;}} => #who:9decaf7
{{&lt; relref "/blog/post.md#who" &gt;}} => /blog/post/#who:badcafe

Ref and RelRef Configuration

The behaviour can, since Hugo 0.45, be configured in config.toml:

refLinksErrorLevel (“ERROR”)
    When using ref or relref to resolve page links and a link cannot resolved, it will be logged with this log level. Valid values are ERROR (default) or WARNING. Any ERROR will fail the build (exit -1).

refLinksNotFoundURL
    URL to be used as a placeholder when a page reference cannot be found in ref or relref. Is used as-is.


## Table of Contents - TOC

[Table of Contents - TOC](https://gohugo.io/content-management/toc/#template-example-toc-partial)

Hugo can automatically parse Markdown content and create a Table of Contents you can use in your templates.

Currently, the {{.TableOfContents}} page variable does not allow you to specify which heading levels you want the TOC to render. See the related GitHub discussion (#1778). As such, the resulting `<nav id="TableOfContents"><ul></ul></nav>` is going to start at `<h1>` when pulling from `{{.Content}}`.

Hugo может автоматически анализировать содержимое Markdown и создавать оглавление, которое вы можете использовать в своих шаблонах.
В настоящее время переменная страницы {{.TableOfContents}} не позволяет вам указать, какие уровни заголовков вы хотите отображать в оглавлении. Смотрите соответствующее [обсуждение GitHub (# 1778)](https://github.com/gohugoio/hugo/issues/1778).

>Таким образом, результирующий `<nav id="TableOfContents"> <ul> </ul> </nav>` будет начинаться с `<h1>` при извлечении из `{{.Content}}`.



#### emplate Example: TOC Partial

The following is a partial template that adds slightly more logic for page-level control over your table of contents. It assumes you are using a toc field in your content’s front matter that, unless specifically set to false, will add a TOC to any page with a .WordCount (see Page Variables) greater than 400. This example also demonstrates how to use conditionals in your templating:

`layouts/partials/toc.html`

```
{{ if and (gt .WordCount 400 ) (.Params.toc) }}
<aside>
    <header>
    <h2>{{.Title}}</h2>
    </header>
    {{.TableOfContents}}
</aside>
{{ end }}
```


With the preceding example, even pages with > 400 words and toc not set to false will not render a table of contents if there are no headings in the page for the {{.TableOfContents}} variable to pull from.
