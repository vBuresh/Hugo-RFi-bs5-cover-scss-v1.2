---
title: Shirtcodes пользователя
date: 2020-07-20T09:24:46+03:00
Lastmod: 2021-06-07T12:19:37+03:00
draft: false
# summary:
# summaryImage: images/
author:
  # given_name: Vladimir
  # family_name: Buresh
  display_name: ['Hugo Authors', 'wBuresh']
categories: ['управление контентом']
tags: [hugo, шаблоны]
# categories: [content-management]
# tags: [hugo, templates, taxonomy]
toc: true
---

Hugo поставляется с набором шорткодов (shortcodes), которые облегчают разработку, позволяя автору сосредоточиться только на содержимом. С ними легко достичь желаемой чистоты Markdown.


## Shortcodes в Markdown

В Hugo 0.55 была измена, работа разделителя` %`. Shortcodes, использующие `%` как самый внешний разделитель, полностью отображаться при отправке в средство визуализации содержимого. (например Blackfriday или Goldmark), поэтому могут быть частью сгенерированного оглавления, сносок и пр.


## Shortcodes без Markdown

Символ `<` указывает на то, что контент shortcode’s нуждается в дальнейшей обработке. Обычно это встречается в shortcodes, не содержащих markdown, а  только HTML:

{{< highlight go-html-template >}}
❴❴< myshortcode >❵❵
<button type="button" class="btn btn-outline-info">Info</button>
<button type="button" class="btn btn-outline-light">Light</button>
<button type="button" class="btn btn-outline-dark">Dark</button>
❴❴< /myshortcode >❵❵
{{< /highlight >}}

Подсветка кода html

{{< highlight html >}}
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavDarkDropdown" aria-controls="navbarNavDarkDropdown" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavDarkDropdown">
      <ul class="navbar-nav">
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDarkDropdownMenuLink" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Dropdown
          </a>
          <ul class="dropdown-menu dropdown-menu-dark" aria-labelledby="navbarDarkDropdownMenuLink">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</nav>
{{< /highlight >}}


With options

{{< highlight html >}}
<div class="card" style="width: 22rem;">
  <img src="svg/rfi-plaseholder.svg" class="img-thumbnail" alt="rfi-plaseholder">
  <div class="card-body bg-light">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
{{< /highlight >}}

Вот еще один пример. На сей раз с SVG

{{< highlight svg >}}
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="500" heith="333"
  viewBox="0 0 1000 667" >
  <title>rfi-placeholder</title>
<symbol id="bi-grid-1x2-fill" viewBox="0 0 16 16">
    <path d="M0 1a1 1 0 0 1 1-1h5a1 1 0 0 1 1 1v14a1 1 0 0 1-1 1H1a1 1 0 0 1-1-1V1zm9 0a1 1 0 0 1 1-1h5a1 1 0 0 1 1 1v5a1 1 0 0 1-1 1h-5a1 1 0 0 1-1-1V1zm0 9a1 1 0 0 1 1-1h5a1 1 0 0 1 1 1v5a1 1 0 0 1-1 1h-5a1 1 0 0 1-1-1v-5z"/>
</symbol>
    <rect width="1000" height="667" fill="#0a1922" stroke="none"  />
    <circle cx="500" cy="333" r="270" fill="none" stroke="#00D1B2" stroke-width="3" />
    <use xlink:href="#bi-grid-1x2-fill" transform="translate(250, 170) scale(.5)" fill="#e0f2f1" />
</svg>
{{< /highlight >}}

With rfi SVG

{{< highlight html >}}
<div class="card" style="width: 21rem;">
  <img src="svg/rfi-plaseholder.svg" class="img-thumbnail" alt="rfi-plaseholder">
  <div class="card-body bg-light">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick highlight text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
{{< /highlight >}}
