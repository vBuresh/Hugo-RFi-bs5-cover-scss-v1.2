---
title: "Ночной режим"
# subtitle: continuer of the title in a two words
date: 2021-06-15T23:41:31+03:00
Lastmod: 2021-16-17T04:59:31+03:00
draft: false
description: A short description of this page, «в двух словах»
# summary: ответ на вопрос - «зачем читать я буду это?»
author:
given_name: Eric
family_name: Fandorin
display_name: erfandor, wBuresh
categories: [interface]
categories: [интерфейс]
tags: ['bootstrap', 'темы оформления', 'ночной режим']
# tags: ['bootstrap', 'themes', dark mode']
tags: ['bootstrap', 'themes', 'ночной режим']
---

<!-- типа вступление -->

Что такое ночной режим и зачем он нужен.

Перлы в тему:

- [3 безумно простых способа](переключить сайт в темный режим)
- [Ночной режим](https://webformyself.com/nochnoj-rezhim-dlya-vashego-sajta-chast-1/)

# Dark Mode Switch (ночной переключатель)

Данный элемент 🌓 позволяет переключить тему сайта в светлые/тёмные тона для удобства работы с сайтом.

## Получение дистрибутива

Вначале необходимо скачать последнюю версию **Dark Mode Switch**. Это можно сделать несколькими способами:

1. Клонировать GitHub репозиторий **Dark Mode Switch**: `git clone https://github.com/coliff/dark-mode-switch.git`
2. Установить - c помощью **npm**:  `npm install dark-mode-switch`
3. Инсталлировать  **Dark Mode Switch** с использованием **yarn** `add dark-mode-switch`

## Добавление в проект

Для добавления компонентов **Dark Mode Switch** в проект нужно:

1. Скопировать файлы js и css: `/dark-mode-switch/dark-mode.css` и `/dark-mode-switch/dark-mode-switch.js`
из дистрибутива в соответствующие директории js и css проекта.
2. Форму переключателя (см исходный код примера dark-mode-switch/index.html, строки 44-49):

{{< highlight html "linenos=true, linenostart=44" >}}
<div class="form-check form-switch">
<input type="checkbox" class="form-check-input" id="darkSwitch" />
<label class="custom-control-label" for="darkSwitch">Dark Mode</label>
</div>
{{< /highlight >}}

Добавить в исходный код группы вводного содержимого `<header>`(если он является дочерним элементом `<body>`), либо - в `<nav>` (если есть). См. [Основы html]({{< ref "theory" >}})

3. Подключить скопированные в проект css и js:

- css нужно поместить в `<head>` - элемент метаданных документа:

``` html
<link rel="stylesheet" type="text/css" href="/css/dark-mode.css">
```

- js лучше поместить за группой конечного контента страницы - `<footer>`:

``` html
<script src="dark-mode-switch.min.js"></script>
```

## Проверка работоспособности

После этого можно провести проверку работоспособности переключателя режимов **Dark Mode Switch**

При правильном подключении все должно отображаться без искажений и корректно работать (в режимах "включен/выключен") во всех браузерах, [поддерживаюших Bootstrap v5.0](https://getbootstrap.com/docs/5.0/getting-started/browsers-devices/#supported-browsers)

## Как это работает

При переключении в темный режим, в тег `body` добавляется следующий код - `data-theme="dark"`. Кроме того можно направить CSS на элементы страницы. Это делается следующим образом:

{{< highlight css >}}
[data-theme="dark"] {
  background-color: #111 !important;
  color: #eee;
}
{{< /highlight >}}


## Кастомизация

Bootstrap - есть выбор: `text-dark bg-light` - `text-white bg-dark`. См. assets/bootstrap/scss/_variables.scss

### Иконки - в переменных _variables.scss:

Инспектор


_form-check.scss:110

{{< highlight scss "linenos=true, linenostart=103" >}}
//
// Switch
//

.form-switch {
  padding-left: $form-switch-padding-start;

  .form-check-input {
    width: $form-switch-width;
    margin-left: $form-switch-padding-start * -1;
    background-image: escape-svg($form-switch-bg-image);
    background-position: left center;
    @include border-radius($form-switch-border-radius);
    @include transition($form-switch-transition);

    &:focus {
      background-image: escape-svg($form-switch-focus-bg-image);
    }

    &:checked {
      background-position: $form-switch-checked-bg-position;

      @if $enable-gradients {
        background-image: escape-svg($form-switch-checked-bg-image), var(--#{$variable-prefix}gradient);
      } @else {
        background-image: escape-svg($form-switch-checked-bg-image);
      }
    }
  }
}
{{< /highlight >}}


{{< highlight css>}}
/* _form-check.scss:110 */
.form-switch .form-check-input
width: 2em;
margin-left: -2.5em;
background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='-4 -4 8 8'%3e%3ccircle r='3' fill='rgba%280, 0, 0, 0.25%29'/%3e%3c/svg%3e");
background-position: left center;
border-radius: 2em;
transition: background-position 0.15s ease-in-out;
{{< /highlight >}}



#### строка 751

``` html
$form-check-input-checked-bg-image:       url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 20 20'><path fill='none' stroke='#{$form-check-input-checked-color}' stroke-linecap='round' stroke-linejoin='round' stroke-width='3' d='M6 10l3 3l6-6'/></svg>") !default;
```

#### строка 752

``` html
$form-check-radio-checked-bg-image:       url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='-4 -4 8 8'><circle r='2' fill='#{$form-check-input-checked-color}'/></svg>") !default;
```
#### строка 757

``` html
$form-check-input-indeterminate-bg-image:       url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 20 20'><path fill='none' stroke='#{$form-check-input-indeterminate-color}' stroke-linecap='round' stroke-linejoin='round' stroke-width='3' d='M6 10h8'/></svg>") !default;
```

#### строка 770

``` html
$form-switch-bg-image:            url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='-4 -4 8 8'><circle r='3' fill='#{$form-switch-color}'/></svg>") !default;
```

#### строка 775

``` html
$form-switch-focus-bg-image:      url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='-4 -4 8 8'><circle r='3' fill='#{$form-switch-focus-color}'/></svg>") !default;
```

#### строка 807

``` html
$form-select-indicator:             url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'><path fill='none' stroke='#{$form-select-indicator-color}' stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M2 5l6 6 6-6'/></svg>") !default;
```
