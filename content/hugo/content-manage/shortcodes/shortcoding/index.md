+++
title="Шорткоды в Hugo"
date="2019-12-09T09:34:39+03:00"
draft="true"
summary="Шорткоды - подготовленные фрагменты кода, ускоряющие разработку"
pygmentsUseClasses="true"
toc="true"
description="Шорткоды - это простые фрагменты, размещаемые в исходном тексте файлов директории content. Hugo предлагает довольно внушительный список шаблонов. Его можно расширить путем добавления своих собственных"
summaryImage="hugo-shordcodes.jpg"
# pageTop: true
navvvPravo=true
tags=["devTools", "шорткоды"]
+++

# Пользовательские шорткоды

Для пользовательских шорткодов обычно создается директория `layouts/shortcodes`

Имя html файла шорткода следует тщательно продумать. Оно будет использоваться, при вызове для добавления в текст, но без расширения **html**.

Например, `layouts/shortcodes/wBlockquote.html` будет вызываться, в зависимо+сти от выбранных параметров:

``` hugo
{{&lt; wBlockquote /&gt;}}`

// либо

2{% wBlockquote %}2
```

При необходимости можно добавлять поддиректории e.g. in layouts/shortcodes/boxes

При этом шорткод будет доступен по относительной ссылке e.g:

``` go
{{&lt; boxes/wBlockquote &gt;}}
```

## Shortcodes немного теории

Если вы пишете в Markdown и обнаруживаете, что часто встраиваете свой контент в необработанный HTML, Hugo предоставляет встроенные функции шорткодов. Это одна из самых мощных функций Hugo, позволяющая очень быстро создавать собственные расширения Markdown.

{{< note >}}
См. документацию [Shortcodes](https://gohugo.io/content-management/shortcodes/) для применения (преимущественно) встроенных шорткодов, поставляемых с Hugo, [Shortcode Templating](https://gohugo.io/templates/shortcode-templates/), чтобы узнать, как создать свой собственный шорткод.
{{< /note>}}

{{% bQuote %}}
Hugo любит Markdown за его простой формат контента, но бывают случаи, когда Markdown терпит неудачу. Часто авторы контента вынуждены добавлять необработанный HTML (например, видео `<iframes>`) к контенту Markdown. Мы думаем, что это противоречит прекрасной простоте синтаксиса Markdown.
{{% /bQuote %}}

Хьюго создал шорткоды, чтобы обойти эти ограничения.

Шорткод - это простой фрагмент внутри файла содержимого, который Hugo будет отображать с использованием предварительно определенного шаблона. Обратите внимание, что шорткоды не будут работать в файлах шаблонов. Если вам нужен тип встроенной функции, предоставляемой шорткодами, но в шаблоне, вам, скорее всего, потребуется частичный шаблон.

В дополнение к более чистому Markdown, шорткоды могут быть обновлены в любое время, чтобы отразить новые классы, методы или стандарты. В момент создания сайта шорткоды Hugo легко сливаются с вашими изменениями. Вы избегаете возможно сложной операции поиска и замены.

in your content files, a shortcode can be called by calling... перевод:
- **Это яндекс:** в файлы контента, шорткод можно назвать по телефону
- **Это Гугл:** В ваших файлах контента шорткод может быть вызван путем вызова

В переводе с я_русского и г_русского на русский это означает:

В ваших пользовательских файлах шорткод может быть вызван путем:


- **Это яндекс:** Параметры шорткода есть пробелы, и параметры внутреннего пространства можно цитировать.
- **Это Гугл:** Параметры шорткода разделены пробелами, а параметры с внутренними пробелами могут быть заключены в кавычки

Прекрасный перевод делает Гугл. Достоточно небольшого уточнения:

Параметры шорткода разделяются пробелами, а параметры с внутренними пробелами могут быть заключены в кавычки.



<details>
<summary> title1.html, title2.html, title3.html, title4.html, title5.html, title6.html </summary>

Usage example:

```
{< title1 "My awesome title" "my-title-id">}
```

The **first parameter** is the title of the shortcode (in this example is "My awesome title").<br>
The **second paramter** is the ID of the shortcode (in this example is "my-title-id").<br>
It can be used in links to the same page as:

```
[link to the title](#my-title-id)
```
</details>

### Shortcodes - шорткоды by Roberto Jordaney


``` bash
themes/hugo-refresh/layouts/shortcodes
```

Список шорткодов, которые можно использовать в своих статьях с описанием:
1. book.html
1. box.html
1. code.html
1. codeAll.html
1. codeInline.html
1. code_tabs.html
1. exercise.html
1. figure.html
1. link.html
1. message_blue.html
1. message_dark.html
1. message_green.html
1. message_red.html
1. message_yellow.html
1. newLine.html
1. notificationBlue.html
1. notificationGreen.html
1. notificationRed.html
1. notificationYellow.html
1. site_blue.html
1. site_green.html
1. site_lightgreen.html
1. site_red.html
1. site_yellow.html
1. subtitle1.html
1. subtitle2.html
1. subtitle3.html
1. subtitle4.html
1. subtitle5.html
1. subtitle6.html
1. title1.html
1. title2.html
1. title3.html
1. title4.html
1. title5.html
1. title6.html
1. twoFigure.html


### Применение шорткодов

{{% bQuote %}}
Иными словами, чтобы не портить, как выразился специалист Hugo, "который любит Markdown" и старается не противоречить "прекрасной простоте синтаксиса" этого великолепного языка разметки, придумали шорткоды. Особенно это важно, когда  приходится часто встраивать свой контент в необработанный HTML.

Hugo предоставляет встроенные функции шорткодов. Это одна из самых мощных функций Hugo, позволяющая очень быстро создавать собственные расширения Markdown.
{{% /bQuote %}}

### Исходный код

``` html
<div class="row text-center container">
    <div class="col">
        <div class="notification pslink">
            <p>{{ .Inner  | markdownify }}</p>
        </div>
    </div>
</div>
```

``` bash
$ sudo bash -c 'echo 0 > /proc/sys/kernel/randomize_va_space'

```

## Card

Вот так это выглядит в коде.


Ещё был сделан сниппет для Atom.
