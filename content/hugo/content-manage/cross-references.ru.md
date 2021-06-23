---
title: Ссылки и перекрестные ссылки
date: 2021-06-07T14:00:55+03:00
Lastmod: 2021-06-22T13:09:21+03:00
# summary: краткое изложение - зачем читать сие
Lastmod: 2021-06-07T14:00:55+03:00
draft: false
description: "Shortcodes for creating links to documents."
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: ['управление контентом', 'примеры']
tags: ['hugo', 'фронт-енд']
toc: true
---

The `ref` and `relref` shortcodes display the absolute and relative permalinks to a document, respectively.

## Use `ref` and `relref`

```go-html-template
{{</* ref "document" */>}}
{{</* ref "document#anchor" */>}}
{{</* ref "document.md" */>}}
{{</* ref "document.md#anchor" */>}}
{{</* ref "#anchor" */>}}
{{</* ref "/blog/my-post" */>}}
{{</* ref "/blog/my-post.md" */>}}
{{</* relref "document" */>}}
{{</* relref "document.md" */>}}
{{</* relref "#anchor" */>}}
{{</* relref "/blog/my-post.md" */>}}
```

To generate a hyperlink using `ref` or `relref` in markdown:

```md
[About]({{</* ref "/page/about" */>}} "About Us")
```

The `ref` and `relref` shortcodes require a single parameter: the path to a content document, with or without a file extension, with or without an anchor.

**Paths without a leading `/` are first resolved relative to the current page, then to the remainder of the site.

Hugo emits an error or warning if a document cannot be uniquely resolved. The error behavior is configurable; see below.

### Link to another language version

To link to another language version of a document, use this syntax:

```go-html-template
{{</* relref path="document.md" lang="ja" */>}}
```

### Get another Output Format

To link to another Output Format of a document, use this syntax:

```go-html-template
{{</* relref path="document.md" outputFormat="rss" */>}}
```

### Heading IDs

When using Markdown document types, Hugo generates element IDs for every heading on a page. For example:

```md
## Reference
```

produces this HTML:

```html
<h2 id="reference">Reference</h2>
```

Get the permalink to a heading by appending the ID to the path when using the `ref` or `relref` shortcodes:

```go-html-template
{{</* ref "document.md#reference" */>}}
{{</* relref "document.md#reference" */>}}
```

Generate a custom heading ID by including an attribute. For example:

```md
## Reference A {#foo}
## Reference B {id="bar"}
```

produces this HTML:

```html
<h2 id="foo">Reference A</h2>
<h2 id="bar">Reference B</h2>
```

Hugo will generate unique element IDs if the same heading appears more than once on a page. For example:

```md
## Reference
## Reference
## Reference
```

produces this HTML:

```html
<h2 id="reference">Reference</h2>
<h2 id="reference-1">Reference</h2>
<h2 id="reference-2">Reference</h2>
```

## Ref and RelRef Configuration

The behavior can, since Hugo 0.45, be configured in `config.toml`:

refLinksErrorLevel ("ERROR")
: When using `ref` or `relref` to resolve page links and a link cannot resolved, it will be logged with this log level. Valid values are `ERROR` (default) or `WARNING`. Any `ERROR` will fail the build (`exit -1`).

refLinksNotFoundURL
: URL to be used as a placeholder when a page reference cannot be found in `ref` or `relref`. Is used as-is.


## Hugo Symbolic Links

[Symbolic Links suddenly stopped](https://discourse.gohugo.io/t/symbolic-links-suddenly-stopped-from-version-v0-56-0/19878/2) (from version v0.56.0)

{{< bQuote >}}
<h4>Notes</h4>
<ul>
<li>We have removed the “auto theme namespacing” of params from theme configuration. This was an undocumented and hidden feature that wasn’t useful in practice.
<ul>
<li>We have revised and improved the symlinks support in Hugo: In earlier versions, symlinks were only fully supported for the content folders. With the introduction of the new very flexible file mounts, with content support even for what we have traditionally named “themes”, we needed a more precise definition of symlink support in Hugo:</li>
<li>Symlinks are not supported outside of the main project ((the project you run hugo or hugo server from).</li>
<li>In the main project static mounts, only symlinks to files are supported.</li>
<li>In all other mounts in the main project, both file and directory symlinks are allowed.</li>
</ul>
</li>
</ul>

<footer class="blockquote-footer text-right font-italic pt-3">
Bjørn Erik Pedersen: See
<a href="https://gohugo.io/news/0.56.0-relnotes#notes">Hugo 0.56.0, Notes</a>
</footer>
{{< /bQuote >}}

The short version:

{{< bQuote >}}
<ul>
<li>The overall symlink support is much improved.</li>
<li>But it’s more restrictive for themes (for security and … practial reason; symlinks are hard to reason about, and even harder when you reason about some other person’s symlinks)</li>
<li>You now have a powerful mounts feature that can do most of what the old symlinks hacks can do.</li>
</ul>
<footer class="blockquote-footer text-right font-italic pt-3 mb-0">
Bjørn Erik Pedersen
<a href="https://discourse.gohugo.io/t/symbolic-links-suddenly-stopped-from-version-v0-56-0/19878/2">The short version</a>
</footer>
{{< /bQuote >}}

## From hugo-links-and-urls

See example of use [here](https://rjordaney.is/code_exercises/staircase_n_steps/)

### Ссылки и управление URL-адресам

Hugo поддерживает:

- постоянные ссылки (permalinks),
- псевдонимы (aliases),
- канонизацию ссылок (link canonicalization),
- атакже и несколько вариантов обработки URL-адресов:
  - relative URLs относительных,
	- absolute URLs - абсолютных.


Постоянные ссылки (permalinks)"

По умолчанию целевой директорией Hugo для вашего встроенного веб-сайта служит директория
'public /'. Однако её можно изменить, указав другой параметр **publishDir** в конфигурации сайта. Директории, созданные во время сборки для раздела, отражают положение каталога содержимого в папке content и пространство имен, соответствующее его макету в иерархии **contentdir**.

<!-- The permalinks option in your site configuration allows you to adjust the directory paths (i.e., the URLs) on a per-section basis. This will change where the files are written to and will change the page’s internal “canonical” location, such that template references to .RelPermalink will honor the adjustments made as a result of the mappings in this option. -->

Опция permalinks в конфигурации сайта позволяет настраивать пути к директориям (то есть URL-адреса) для каждого раздела. Это изменит место, куда записываются файлы, и изменит внутреннее «каноническое» расположение страницы, так что ссылки на шаблоны в .RelPermalink будут учитывать изменения, сделанные в результате сопоставлений в этом параметре.

>These examples use the default values for `publishDir` and `contentDir`; i.e., `public` and `content`, respectively. You can override the default values in your site’s config file.

For example, if one of your sections is called posts and you want to adjust the canonical path to be hierarchical based on the year, month, and post title, you could set up the following configurations in YAML and TOML, respectively.

### Permalinks Configuration Example


Usage example:

```
{< code_tabs
  file1="/content/code_exercises/staircase_n_steps/code/solution_python.md" title1="Python" icon1="python"
  file2="/content/code_exercises/staircase_n_steps/code/solution_c.md" title2="C" icon2="c"
  file3="/content/code_exercises/staircase_n_steps/code/solution_java.md" title3="Java" icon3="java"
  >}
```


The parameter **file1** is the name of the markdown file to be displayed in the first tab.
The path needs to start from the `content` folder.<br>
The **title1** is the title of the first tab.<br>
The **icon1** is the icon to be shown at the right of the title, it is an optional parameter. See the partial code `icon.html` for the available icons.

There are 6 tabs supported at this moment

* the files parameters are **file1**, **file2**, **file3**, **file4**, **file5**, **file6**

* the titles parameters are **title1**, **title2**, **title3**, **title4**, **title5**, **title6**

* the icons parameters are **icon1**, **icon2**, **icon3**, **icon4**, **icon5**, **icon6**
