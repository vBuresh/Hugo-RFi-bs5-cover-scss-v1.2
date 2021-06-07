---
title: Users Shortcodes
date: 2020-07-20T09:24:46+03:00
draft: false
# summary:
# summaryImage: images/
categories:
  - webDev
tags:
  - content management
  - shortcodes
toc: true
---

Hugo comes with a set of shortcodes that facilitate development by allowing the author to focus only on the content. It is easy to achieve the desired markdown purity with them.


## Shortcodes with Markdown

In Hugo 0.55 we changed how the % delimiter works. Shortcodes using the % as the outer-most delimiter will now be fully rendered when sent to the content renderer (e.g. Blackfriday for Markdown), meaning they can be part of the generated table of contents, footnotes, etc.

If you want the old behavior, you can put the following line in the start of your shortcode template:

{{ $_hugo_config := `{ "version": 1 }` }}
