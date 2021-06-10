---
title: Встроенные Hugo шорткоды
date: 2020-07-06T13:10:04+03:00
Lastmod: 2021-06-07T12:19:37+03:00
draft: false
categories:
  - webDev
tags:
categories: ['управление контентом']
tags: [hugo, шорткоды]
toc: true
---


Hugo поставляется с набором предопределенных коротких кодов, которые представляют собой очень распространенное использование. Эти шорткоды предоставлены для удобства автора и для поддержания чистоты содержания Markdown.
фигура

## Встроенный Hugo шорткод - `❴❴< highlight >❵❵`

Само название этого очень интересного и нужного шорткода говорит его назначении. Некоторые материалы по особенностям и практике применения этого шорткода изложены в статье [Подсветка синтаксиса]({{< relref "/code-highlighting" >}}).


**figure** - это расширение синтаксиса изображения в markdown, которое не обеспечивает сокращение для более семантического HTML5-элемента <figure>.

Шорткод рисунка может использовать следующие именованные параметры:

**src**<br>
URL of the image to be displayed.

**link**<br>
If the image needs to be hyperlinked, URL of the destination.

**target**<br>
Optional target attribute for the URL if link parameter is set.

**rel**<br>
Optional rel attribute for the URL if link parameter is set.

**alt**<br>
Alternate text for the image if the image cannot be displayed.

title
    Image title.
caption
    Image caption. Markdown within the value of caption will be rendered.
class
    class attribute of the HTML figure tag.
height
    height attribute of the image.
width
    width attribute of the image.
attr
    Image attribution text. Markdown within the value of attr will be rendered.
attrlink
    If the attribution text needs to be hyperlinked, URL of the destination.

Пример фигуры Input
figure-input-example.md

{{< figure src="/images/screenshot-o-b.png" class="figure-img float-left pr-5" width="610px" title="Hugo-ReFresing - главная страница (темная)" >}}
{{< figure src="/images/screenshot-o-w.png" class="figure-img" width="610px" title="Тема Hugo-ReFresing - главная страница (светлая)" >}}

{{< highlight html>}}
2{< figure src="/images/screenshot-o-b.png" class="figure-img float-left pr-5" width="610px" title="Hugo-ReFresing - главная страница (темная)" >}2
2{< figure src="/images/screenshot-o-w.png" class="figure-img" width="610px" title="Тема Hugo-ReFresing - главная страница (светлая)" >}2
{{< /highlight>}}

{{< figure src="/svg/rfi-plaseholder.svg" >}}

Пример фигуры Output
figure-output-example.html

{{< highlight html>}}
<figure>
  <img src="/images/rfi-homepage.png"  />
  <figcaption>
      <h4>Тема Hugo-ReFresing - скриншот главной страницы (темный режим)</h4>
  </figcaption>
</figure>
{{< /highlight >}}

Bootstrap представил свои стили:

{{< highlight html>}}
<figure class="figure">
  <img src="..." class="figure-img img-fluid rounded" alt="...">
  <figcaption class="figure-caption text-right">A caption for the above image.</figcaption>
</figure>
{{< /highlight >}}
