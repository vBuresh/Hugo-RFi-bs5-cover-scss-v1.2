---
title: "Основы html"
date: 2021-05-24T19:33:05+03:00
Lastmod: 2021-07-01T21:14:21+03
draft: false
description: "элементы html документа (код и примеры)"
author:
  given_name: serg
  display_name: g8, b6
categories:
  - webDev
tags: [HTML, MD]
toc: true
---

<hgroup>
  <h1 class="allcaps">HTML</h1>
  <h2 id="living-standard" class="no-num no-toc">Living Standard — Last Updated <span class="text-muted">30 June 2021</span></h2>
</hgroup>


HTML использует разметку ("markup") для отображения текста, изображений и другого контента в веб-браузере. HTML-разметка включает в себя специальные "элементы", такие как `<head>, <title>, <body>, <header>, <footer>, <article>, <section>, <p>, <div>, <span>, <img>, <aside>, <audio>, <canvas>, <datalist>, <details>, <embed>, <nav>, <output>, <progress>, <video>` и многие
другие. Подробнее... [MDN: "HTML Руководства для начинающих"](https://developer.mozilla.org/ru/docs/Web/HTML/Element/head)

<h2> Основные определения, <small>которые необходимо ясно понимать</small></h2>

1. `<body>` - это контент (содержимое) документа HTML. На каждой странице может быть только один элемент `<body>`

1. `<head>`элемент метаданных документа, содержащий машиночитаемую информацию о нем.
1. **`<main>`** предназначен для содержимого, уникального для этой страницы. Используйте `<main>` только один раз на странице и размещайте прямо внутри `<body>`. В идеале он не должен быть вложен в другие элементы.
1. **`<article>`** окружает блок связанного содержимого, который имеет смысл сам по себе без остальной части страницы (например, один пост в блоге).
1. **`<section>`** подобен `<article>`, но больше подходит для группирования одной части страницы, которая представляет собой одну часть функциональности (например, мини-карту или набор заголовков статей и сводок). Считается хорошей практикой начинать каждый раздел с заголовка. Также обратите внимание, что в зависимости от контекста вы можете разбить `<article>` на несколько `<section>` или, наоборот, `<section>` на несколько `<article>`.
1. **`<aside>`** содержит контент, который не имеет прямого отношения к основному содержимому, но может содержать дополнительную информацию, косвенно связанную с ним (словарь, биография автора, связанные ссылки и т. д.).
1. **`<header>`** представляет собой группу вводного содержимого. Если он дочерний элемент `<body>`, то он определяет глобальный заголовок веб-страницы, но если он дочерний элемент `<article>` или `<section>`, то определяет конкретный заголовок для этого раздела (постарайтесь не путать его с `titles` и `headings`).
1. **`<nav>`** содержит основные функции навигации для страницы. Так же часто в нем можно увидеть логотип и/или название сайта или компании. Вторичные ссылки и т. д. не входят в навигацию.
1. **`<footer>`** представляет собой группу конечного контента для страницы.

Наглядные примеры практического применения подавляющего большинства элементы HTML-разметки приведены в документации [Bootstrap](https://getbootstrap.com/docs/5.0/getting-started/introduction/).

### `<head>`

`<head>`: элемент метаданных документа.
HTML-элемент `<head>` содержит машиночитаемую информацию (metadata) о документе, например его заголовок, скрипты и страницы стилей.</article>

```HTML
<!doctype html>
<html>
  <head>
    <title>Заголовок страницы</title>
  </head>
</html>
```
> [Источник: MDN](https://developer.mozilla.org/ru/docs/Web/HTML/Element/head)

See w3c html standard

>[4.3.8 The header element](https://html.spec.whatwg.org/multipage/sections.html#the-header-element)

``` HTML
<body>
 <header>
  <h1>Little Green Guys With Guns</h1>
  <nav>
   <ul>
    <li><a href="/games">Games</a>
    <li><a href="/forum">Forum</a>
    <li><a href="/download">Download</a>
   </ul>
  </nav>
  <h2>Important News</h2> <!-- this starts a second subsection -->
  <!-- this is part of the subsection entitled "Important News" -->
  <p>To play today's games you will need to update your client.</p>
  <h2>Games</h2> <!-- this starts a third subsection -->
 </header>
 <p>You have three active games:</p>
 <!-- this is still part of the subsection entitled "Games" -->
 ...
```



## `<body>`

HTML-элемент `<body>` представляет собой контент (содержимое) документа HTML. В документе может быть только один элемент `<body>`.

```HTML
<html>
  <head>
    <title>Заголовок документа</title>
  </head>
  <body>
    <p>Это параграф</p>
  </body>
</html>
```
>[Источник: MDN](https://developer.mozilla.org/ru/docs/Web/HTML/Element/body)


## `<main>`

HTML-элемент `<main>` предназначен для основного контента (содержимого) `<body>` документа (страницы). Основной контент состоит из контента, который непосредственно относится к главной теме документа или её развивает.

```HTML
<main>
  <h1>Яблоки</h1>
  <p>Яблоко - плод яблони, который употребляется в пищу в свежем виде, служит сырьём в кулинарии и для приготовления напитков.</p>

  <article>
    <h2>Сорт "Ред Делишес"</h2>
    <p>Эти ярко-красные яблоки являются одними из самых популярных в Соединённых Штатах.</p>
    <p>... </p>
    <p>... </p>
  </article>

  <article>
    <h2>Сорт "Гренни Смит";/h2>
    <p>Эти сочные, зелёные яблоки являются одними из самых популярных в мире.</p>
    <p>... </p>
    <p>... </p>
  </article>
</main>
```
>[Источник: MDN](https://developer.mozilla.org/ru/docs/Web/HTML/Element/main)

## `<footer>`

HTML-элемент `<footer>` представляет собой нижний колонтитул (футер, подвал) для своего ближайшего секционного контента или секционного корня. Футер обычно содержит информацию об авторе раздела, информацию об авторском праве или ссылки на связанные документы.

``` html
<footer>
  Какая-то информация об авторском праве или может
  информация об авторе статьи?
</footer>
```
>[Источник: MDN](https://developer.mozilla.org/ru/docs/Web/HTML/Element/footer)

See w3c html standard [4.3.9 The footer element](https://html.spec.whatwg.org/multipage/sections.html#the-footer-element)

## `<aside>`

HTML-элемент <aside> представляет собой часть документа, чьё содержимое только косвенно связанно с основным содержимым документа. Чаще всего представлен в виде боковой панели, сносок или меток. Подробнее.. [MDN: <aside>](https://developer.mozilla.org/ru/docs/Web/HTML/Element/aside).

## `<article>`

HTML-элемент `<article>` представляет самостоятельную часть документа, страницы, приложения или сайта, предназначенную для независимого распространения или повторного использования. Этот элемент может представлять статью на форуме, статью в журнале или газете, запись в блоге или какой-либо другой самостоятельный фрагмент содержимого.

``` HTML
<article class="film_review">
  <header>
    <h2>Парк Юрского периода</h2>
  </header>
  <section class="main_review">
    <p>Динозавры были величественны!</p>
  </section>
  <section class="user_reviews">
    <article class="user_review">
      <p>Слишком страшно для меня.</p>
      <footer>
        <p>
          Опубликовано
          <time datetime="2015-05-16 19:00">16 мая</time>
          Лизой.
        </p>
      </footer>
    </article>
    <article class="user_review">
      <p>Я согласен, динозавры мои любимцы.</p>
      <footer>
        <p>
          Опубликовано
          <time datetime="2015-05-17 19:00">17 мая</time>
          Томом.
        </p>
      </footer>
    </article>
  </section>
  <footer>
    <p>
      Опубликовано
      <time datetime="2015-05-15 19:00">15 мая</time>
      Стаффом.
    </p>
  </footer>
</article>
```
>[Источник: MDN](https://developer.mozilla.org/ru/docs/Web/HTML/Element/article)


## `<section>`

HTML-элемент `<section>` представляет собой автономный раздел — который не может быть представлен более точным по семантике элементом — внутри HTML-документа. Как правило, но не всегда, разделы имеют заголовок.

**Пример:**
**До**
```HTML
<div>
  <h1>Заголовок</h1>
  <p>Много замечательного контента</p>
</div>
```
**После**
```HTML
<section>
  <h2>Заголовок</h2>
  <img src="bird.jpg" alt="птица">
</section>
```

>[Источник: MDN](https://developer.mozilla.org/ru/docs/Web/HTML/Element/section)


## html страница Bootstrap

Стартовый шаблон

Be sure to have your pages set up with the latest design and development standards. That means using an HTML5 doctype and including a viewport meta tag for proper responsive behaviors. Put it all together and your pages should look like this:

Убедитесь, что ваши страницы настроены в соответствии с последними стандартами дизайна и разработки. Cтраницы должны выглядеть примерно так:

``` html
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-+0n0xVW2eSR5OomGNYDnhzAbDsOXxcvSN1TPprVMTNDbiYZCxYbOOl7+AMvyTG2x" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>

    <!-- Optional JavaScript; choose one of the two! -->

    <!-- Option 1: Bootstrap Bundle with Popper -->

    <script src="..."></script>

  </body>
</html>
```
[Bootstrap starting](https://getbootstrap.com/docs/5.0/getting-started/introduction/)

## Структура документа и веб-сайта

- [MDN: "Структура документа и веб-сайта"](https://developer.mozilla.org/ru/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)


В тему:

- [MDN: "Структура документа и веб-сайта"](https://developer.mozilla.org/ru/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)
- [MDN: "Использование разделов и создание структуры HTML документа"](https://developer.mozilla.org/ru/docs/Web/Guide/HTML/Using_HTML_sections_and_outlines)

- [MDN: "Introduction to HTML (Введение в HTML)"](https://developer.mozilla.org/ru/docs/Learn/HTML/Introduction_to_HTML)
