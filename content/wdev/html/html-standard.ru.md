---
date: 2021-07-01T20:31:58+03:00
Lastmod: 2021-07-01T20:31:58+03:00
title: Html Standard
subtitle: subtitle of the published article
description: short description of the article
summary: three-line summary of the article.
draft: false
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [Веб-разработка]
# categories: ['Web development']
tags: [HTML, Стандарты]
toc: true
---

<hgroup>
  <h1 class="allcaps">HTML</h1>
  <h2 id="living-standard" class="no-num no-toc">Living Standard — Last Updated <span class="text-muted">30 June 2021</span></h2>
</hgroup>

[4.3.6 The h1, h2, h3, h4, h5, and h6 elements](https://html.spec.whatwg.org/multipage/sections.html#the-h1,-h2,-h3,-h4,-h5,-and-h6-elements)

Элемент `hgroup` представляет заголовок раздела, который состоит из всех дочерних элементов `h1 – h6` элемента `hgroup`. Элемент используется для группировки набора элементов `h1 – h6`, когда заголовок имеет несколько уровней, например подзаголовки, альтернативные заголовки или слоганы.

Ранг элемента `hgroup` - это ранг элемента `h1 – h6` с наивысшим рангом, потомка элемента `hgroup`, если такие элементы есть, или в остальном то же самое, что и для элемента h1 (наивысший ранг). Другие элементы `h1 – h6` содержимого заголовка в элементе `hgroup` указывают подзаголовки или субтитры или (вторичные) альтернативные заголовки.

Раздел заголовков и разделов определяет, как элементы `hgroup` назначаются отдельным разделам.

<!--
The hgroup element represents the heading of a section, which consists of all the h1–h6 element children of the hgroup element. The element is used to group a set of h1–h6 elements when the heading has multiple levels, such as subheadings, alternative titles, or taglines.

The rank of an hgroup element is the rank of the highest-ranked h1–h6 element descendant of the hgroup element, if there are any such elements, or otherwise the same as for an h1 element (the highest rank). Other h1–h6 elements of heading content in the hgroup element indicate subheadings or subtitles or (secondary) alternative titles.

The section on headings and sections defines how hgroup elements are assigned to individual sections. -->

<hgroup>
 <h2>The reality dysfunction</h2>
 <h3>Space is not the only void</h3>
</hgroup>

Смысл использования hgroup в этих примерах состоит в том, чтобы не допустить, чтобы элемент h2 (который действует как вторичный заголовок) создавал отдельный раздел в любом контуре, и вместо этого заставляет содержимое h2 отображаться в визуализированном выводе из Обрисовать алгоритм каким-то образом, чтобы указать, что это не заголовок отдельного раздела, а просто вторичный заголовок в группе заголовков.

То, как пользовательский агент отображает такие многоуровневые заголовки в пользовательских интерфейсах (например, в оглавлении или результатах поиска), остается открытым для разработчиков, поскольку это проблема пользовательского интерфейса. Первый пример выше может быть представлен как:

Дисфункция реальности: космос - не единственная пустота

В качестве альтернативы это могло бы выглядеть так:

Дисфункция реальности (Космос - не единственная пустота)

В интерфейсах, где заголовок может отображаться на нескольких строках, он может отображаться следующим образом, возможно, с первой строкой с большим размером шрифта:

Дисфункция реальности
Космос - не единственная пустота

И еще. Заголовки в теге `hgroup` не отображаются в оглавлении, создаваемом Hugo, где бы они не находились. Пока?
