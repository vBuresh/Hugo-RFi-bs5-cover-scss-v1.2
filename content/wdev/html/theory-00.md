---
title: "Основы html"
date: 2019-11-27T04:53:05+03:00
Lastmod: 2021-05-20T12:17:21+03
draft: true
description: "код и образцы"
author:
  given_name: serg
  display_name: g8
categories:
tags:
  - html
---

### <center>**`<head>`**</center>

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

---
## <center>**`<body>`**</center>

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
---

## <center>**`<main>`**</center>

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
---

## <center>**`<footer>`**</center>

HTML-элемент `<footer>` представляет собой нижний колонтитул (футер, подвал) для своего ближайшего секционного контента или секционного корня. Футер обычно содержит информацию об авторе раздела, информацию об авторском праве или ссылки на связанные документы.

```HTML
<footer>
  Какая-то информация об авторском праве или может
  информация об авторе статьи?
</footer>
```
>[Источник: MDN](https://developer.mozilla.org/ru/docs/Web/HTML/Element/footer)
---

## <center>**`<article>`**</center>

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
---

## <center>**`<section>`**</center>

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
---

## <center>**`html страница Bootstrap`**</center>

Starter template

Be sure to have your pages set up with the latest design and development standards. That means using an HTML5 doctype and including a viewport meta tag for proper responsive behaviors. Put it all together and your pages should look like this:
```HTML
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
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-gtEjrD/SeCtmISkJkNUaaKMoLD0//ElJ19smozuHV6z3Iehds+3Ulb9Bn9Plx0x4" crossorigin="anonymous"></script>

    <!-- Option 2: Separate Popper and Bootstrap JS -->
    <!--
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.min.js" integrity="sha384-Atwg2Pkwv9vp0ygtn1JAojH0nYbwNJLPhwyoVbhoPwBhjQPR5VtM2+xf0Uwh9KtT" crossorigin="anonymous"></script>
    -->
  </body>
</html>
```
[Bootstrap starting](https://getbootstrap.com/docs/5.0/getting-started/introduction/)
