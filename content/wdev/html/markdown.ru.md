---
title: Markdown
subtitle: очень интересный язык разметки
date: 2021-05-25T12:19:37+03:00
Lastmod: 2021-06-10T06:19:37+03:00
draft: false
description: "- популярный язык разметки"
summary: "Markdown (маркда́ун) — это одним из самых распространенных языков разметки в мире. Его отличает необычайная логичность и легкость. В соответствии простым синтаксисом (от греч. ‘строй, порядок’) элементы форматирования размещаются непосредственно в тексте документа Markdown. При этом полностью сохраняется читаемость документа человеком. Кроме того достигается высокая готовность текста к машинной обработке с целью преобразования в многочисленные языки и форматы, в том числе: HTML, Rich Text, .odt, .txt PDF и пр."
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [веб-разработка]
# categories: ['web development']
tags: [HTML, markdown, code]
toc: true
---

Markdown (маркда́ун) - очень интересный язык разметки. Главное его отличие от HTML - низкий порог вхождения.

<!--  — это одним из самых распространенных языков разметки в мире. Его отличает необычайная логичность, простота и легкость. Элементы форматирования помещаются непосредственно в текст документа в соответствии с синтаксисом (от греч. 'строй, порядок') Markdown. При этом полностью сохраняется читаемость документа человеком. Кроме того достигается высокая готовность текста к машинной обработке с целью преобразования в многочисленные языки и форматы, в том числе: HTML, Rich Text, .odt, .txt PDF и пр. -->

## Популярный язык разметки

Markdown создан Джоном Грубером [John Gruber](https://daringfireball.net/projects/markdown/) и Аароном Шварцем [Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz) в 2004 году. [Подробнее см. материал в Википедии...](https://ru.wikipedia.org/wiki/Markdown).

О высокой популярности Markdown свидетельствует обилие информации о нем в интернете. Вот, пожалуй, самые востребованные пособия по Markdown:

- [Markdown By John Gruber](https://daringfireball.net/projects/markdown/)
- [GitHub: markdown-guide](https://github.com/mattcone/markdown-guide)
- [site: Markdown Guide](https://www.markdownguide.org/)
- [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)

<a href="https://daringfireball.net/projects/markdown/">Daring Fireball: Markdown, John Gruber (Creator of Markdown)</a>
<a href="https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet">Markdown Cheatsheet, Adam Pritchard</a>
<a href="https://www.markdowntutorial.com/">Markdown Tutorial (Interactive), Garen Torikian</a>

### "Диалект" GitHub Flavored Markdown (GFM)


source.coffee, text.plain, text.html.basic
source.markdown, text.html.basic, source.asciidoc, source.gfm, text.git-commit, text.plain, text.plain.null-grammar, source.rst, text.restructuredtext


Markdown - это дружественный синтаксис для форматирования обычного текста. Документация GitHub написана на GFM - адаптированной версии Markdown, применяемой по всему GitHub.

is a human-friendly syntax for formatting plain text. Our documentation is written with GitHub Flavored Markdown, a custom version of Markdown used across GitHub.

This site's Markdown rendering is powered by /lib/render-content, which is in turn built on the remark Markdown processor.

Markdown - это удобный синтаксис для форматирования обычного текста. Наша документация написана с использованием GitHub Flavored Markdown, специальной версии Markdown, используемой на GitHub.

Визуализация Markdown на GitHub основана на `/lib/render-content`, построен на процессоре remark Markdown.

GitHub Flavored Markdown, сокращенно - GFM, основываясь на классическом языке Markdown, который по мнению специалистов GitHub:

{{< bQuote >}}
<p>... an easy-to-read, easy-to-write syntax for formatting plain text.</p>
<p class="text-muted">простой для чтения, простой для записи синтаксис для форматирования обычного текста.</p>
<p class="text-muted text-end small"><a href="https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/about-writing-and-formatting-on-github">GitHub Docs - About writing and formatting on GitHub</a></p>
{{< /bQuote >}}

Они добавили в Markdown ряд своих уникальных функций и возможностей, а также ввели некоторые упрощения и получился GFM, который используется на GitHub, для форматирования и письма "прозы и кода"   по всему сайту. По английски - "to format prose and code". Красивая игра слов. Аж захотелось перевести поближе к тексту. Однако разработчики GFM скромны. Языку оказались тесными обширные рамки GitHub. Он скоро вырвался за них, получил очень широкое распространение и успешно применяется всем "околокомпьютерным" сообществом. И не только. Известно, что некоторые писатели, не только технические, его успешно используют в своем творчестве. Ведь так хочется сразу увидеть свое произведение в том же виде, в каком оно выйдет в свет. Здесь это возможно сразу. Правда, писать текст придется в программах, таких как **Atom**, **VSCode** или **VSCodium**. В них даже версионный контроль можно применять, в тексты хранить на  хранить GitHub. Это хорошее преимущество, особенно для тех, у кого нет "зависимости от шариковой ручки". Можно также попробовать **Ghostwriter**.

You can also interact with other users in pull requests and issues using features like @mentions, issue and PR references, and emoji.

GitHub сочетает в себе синтаксис форматирования текста под названием GitHub Flavored Markdown с несколькими уникальными функциями письма.

Markdown - это простой для чтения и записи синтаксис для форматирования обычного текста.

Мы добавили некоторые настраиваемые функции для создания разметки GitHub Flavored Markdown, используемой для форматирования текста и кода на нашем сайте.

### Особенности применения Markdown

Применение Markdown отличается от использования редактора WYSIWYG. Например, в текстовых процессорах, таких, как libreOffise, Microsoft Word и др. для форматирования слов и фраз пользователь нажимает соответствующие кнопки, и изменения сразу видны, а в Markdown пользователь добавляет к тексту символы, определенные синтаксисом Markdown, чтобы указать, как должны выглядеть отмеченные ими элементы  текста (документа).

Чтобы обозначить заголовок, следует перед ним поместить знак числа (например, `# Заголовок один`). Или, чтобы выделить фразу жирным шрифтом, достаточно добавьте две звездочки до и после нее (например, **этот текст выделен жирным шрифтом**). Как уже отмечалось, чтобы привыкнуть к синтаксису Markdown потребуется совсем незначительное время. Скорее всего, - меньше одного часа.

Закрепить и углубить знания поможет это замечательное пособие

### Руководство Markdown Guide

[What is Markdown?](https://www.markdownguide.org/getting-started/#what-is-markdown)

Markdown Guide - это бесплатное справочное руководство с открытым исходным кодом, в котором объясняется, как использовать Markdown, простой и легкий в использовании язык разметки, который можно использовать для форматирования практически любого документа.

The Markdown Guide is a free and open-source reference guide that explains how to use Markdown, the simple and easy-to-use markup language you can use to format virtually any document.
    Markdown Guide - это бесплатное справочное руководство с открытым исходным кодом, в котором объясняется, как использовать Markdown, простой и легкий в использовании язык разметки, который можно использовать для форматирования практически любого документа., Руководство Markdown является свободным и открытым исходным кодом справочное руководство, которое объясняет, как использовать Markdown, простой и легкий в использовании язык разметки вы можете использовать для форматирования практически любой документ.



The Markdown Guide is a free and open-source reference guide that explains how to use Markdown, the simple and easy-to-use markup language you can use to format virtually any document.

Many Markdown applications allow you to use HTML tags in Markdown-formatted text. This is helpful if you prefer certain HTML tags to Markdown syntax. For example, some people find it easier to use HTML tags for images. Using HTML is also helpful when you need to change the attributes of an element, like specifying the color of text or changing the width of an image.

To use HTML, place the tags in the text of your Markdown-formatted file.

```html
This **word** is bold. This <em>word</em> is italic.
```

The rendered output looks like this:

This word is bold. This word is italic.

### HTML в документах Markdown

Источник: [HTML Best Practices](https://www.markdownguide.org/basic-syntax/#html-best-practices)

По соображениям безопасности не все приложения Markdown поддерживают HTML в документах Markdown. В случае сомнений проверьте документацию к вашему приложению Markdown. Некоторые приложения поддерживают только подмножество HTML-тегов.

Используйте пустые строки для отделения HTML-элементов уровня блока, таких как `<div>, <table>, <pre>` и `<p>`, от окружающего содержимого. Старайтесь не делать отступы в тегах табуляцией или пробелами - это может помешать форматированию.

Синтаксис Markdown нельзя использовать внутри блочных HTML-тегов. Например, `<p>italic and **bold**</p>` работать не будут.

## Extended Syntax

### Footnotes

[Footnotes](https://www.markdownguide.org/extended-syntax/#footnotes)

Here's a simple footnote,[^1] and here's a longer one.[^bignote]

[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.

### Heading IDs

Many Markdown processors support custom IDs for headings — some Markdown processors automatically add them. Adding custom IDs allows you to link directly to headings and modify them with CSS. To add a custom heading ID, enclose the custom ID in curly braces on the same line as the heading.

`### My Great Heading {#custom-id}`

The HTML looks like this:

`<h3 id="custom-id">My Great Heading</h3>`

### Definition Lists

Some Markdown processors allow you to create definition lists of terms and their corresponding definitions. To create a definition list, type the term on the first line. On the next line, type a colon followed by a space and the definition.

```md
First Term
: This is the definition of the first term.

Second Term
: This is one definition of the second term.
: This is another definition of the second term.
```

The HTML looks like this:

```html
<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>
```

### Task Lists

Task lists allow you to create a list of items with checkboxes. In Markdown applications that support task lists, checkboxes will be displayed next to the content. To create a task list, add dashes (-) and brackets with a space ([ ]) in front of task list items. To select a checkbox, add an x in between the brackets ([x]).

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

### Using Emoji Shortcodes

Some Markdown applications allow you to insert emoji by typing emoji shortcodes. These begin and end with a colon and include the name of an emoji.

Gone camping! :tent: Be back soon.

That is so funny! :joy:

### Рецензирование

Нужно найти!


### markdownify

[markdownify](https://gohugo.io/functions/markdownify/#readout)

Runs the provided string through the Markdown processor.

Syntax

`markdownify INPUT`

`{{ .Title | markdownify }}`

Note: if you need Render Hooks, which `markdownify` doesn’t currently support, use .RenderString instead.
