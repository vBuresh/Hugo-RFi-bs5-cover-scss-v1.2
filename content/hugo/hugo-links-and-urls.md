---
title: "Ссылки и URL в Hugo"
subtitle: "Shortcodes for creating links to documents"
date: 2019-12-07T07:19:46+03:00
draft: true
summary: "Ссылки в Hugo - дело мудреное. Задаются они шорткодами"
description: "Ссылки в Hugo имеют ряд особенностей. Для грамотной разработки контента и гибкого управления им необходимо правильно применять все виды ссылок с учетом места их использования."
pageTop: false
navvvPravo: true
toc: true
tags: ["webDev"]
---

# Ссылки и управление URL-адресам

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

## Permalinks Configuration Example

<summary> code_tabs.html </summary>

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


See example of use [here](https://rjordaney.is/code_exercises/staircase_n_steps/)

</details>
