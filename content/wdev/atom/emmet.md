---
title: Emmet
subtitle: '— набор полезных плагинов'
date: 2020-03-04T10:43:01+03:00
lastmod: 2021-06-22T11:29:01+03:00
description: 'Emmet — это набор плагинов для текстовых редакторов, ускоряющих написание кода HTML, XML, XSL, и некоторых других языков.'
summary: Emmet — это плагин для текстового редактора Atom, VScode и др.
draft: false
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [веб-разработка]
tags: ['Atom', 'Плагины', 'Code']
# categories: ['web development']
# tags: ['Atom', spell-check]
toc: true
---

См. GitHub [emmet-docs](https://github.com/emmetio/emmet-docs/blob/master/src/documents/)

Emmet — the essential toolkit for web-developers

Emmet is a web-developer’s toolkit that can greatly improve your HTML & CSS workflow:

``` html
<!doctype html>
  <html lang="en">
    <head>
      <title>Demo</title>
    </head>
    <body> | </body>
  </html>
```

<pre>
~~~ tooltip: Type CSS-like abbreviation type: ul#nav>li.item$*4>a{Item $} wait: 1000 tooltip: Run “Expand Abbreviation” action to expand it into HTML ::: “Expand Abbreviation” (Tab key) wait: 600 run: emmet.expand_abbreviation wait: 1000 tooltip: Traverse between important code points with “Next/Previous Edit Point” action ::: “Next Edit Point” (Ctrl-Alt-→)
“Previous Edit Point” (Ctrl-Alt-←) wait: 1000 run: {command: 'emmet.next_edit_point', times: 7} wait: 1000 tooltip: Select tags with “Balance” action ::: “Balance” (Cmd-D) run: {command: 'emmet.balance_outward', times: 3} wait: 1000 moveTo: 102 tooltip: Select important parts with “Select Next/Previous Item” action ::: “Select Next Item” (Shift-Cmd-.)
“Select Previous Item” (Shift-Cmd-,) run: {command: 'emmet.select_next_item', times: 7, beforeDelay: 300} wait: 2000 moveTo: 95 wait: 1000 tooltip: Quickly comment full tag with “Toggle Comment” action ::: “Toggle Comment” (Cmd-/) run: {command: 'emmet.toggle_comment', times: 2, beforeDelay: 1000} </textarea>
</pre>

Basically, most text editors out there allow you to store and re-use commonly used code chunks, called “snippets”. While snippets are a good way to boost your productivity, all implementations have common pitfalls: you have to define the snippet first and you can’t extend them in runtime.

Emmet takes the snippets idea to a whole new level: you can type CSS-like expressions that can be dynamically parsed, and produce output depending on what you type in the abbreviation. Emmet is developed and optimised for web-developers whose workflow depends on HTML/XML and CSS, but can be used with programming languages too.
