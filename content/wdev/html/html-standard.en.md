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
tags: [SVG, Favicons, Icons]
toc: true
---

[4.3.6 The h1, h2, h3, h4, h5, and h6 elements](https://html.spec.whatwg.org/multipage/sections.html#the-h1,-h2,-h3,-h4,-h5,-and-h6-elements)

The hgroup element represents the heading of a section, which consists of all the h1–h6 element children of the hgroup element. The element is used to group a set of h1–h6 elements when the heading has multiple levels, such as subheadings, alternative titles, or taglines.

The rank of an hgroup element is the rank of the highest-ranked h1–h6 element descendant of the hgroup element, if there are any such elements, or otherwise the same as for an h1 element (the highest rank). Other h1–h6 elements of heading content in the hgroup element indicate subheadings or subtitles or (secondary) alternative titles.

The section on headings and sections defines how hgroup elements are assigned to individual sections.

<hgroup class="pb-0">
  <h1>Wallet Setup</h1>
  <h2>Configure your Wallet funding source</h2>
</hgroup>
