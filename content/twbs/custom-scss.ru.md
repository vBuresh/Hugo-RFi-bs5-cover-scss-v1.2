---
date: 2021-06-27T14:35:48+03:00
Lastmod: 2021-06-28T14:35:48+03:00
title: Custom Scss
subtitle: subtitle of the published article
description: short description of the article
summary: three-line summary of the article.
draft: false
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: ["Управление Контентом"]
tags: [Bootstrap, Настройки]
# categories: ['Content-management']
# tags: ['Bootstrap', 'Examples']
toc: true
---

По возможности избегайте изменения файлов ядра Bootstrap. Для Sass это означает создание собственной таблицы стилей, которая импортирует Bootstrap, чтобы вы могли изменять и расширять ее. Предполагая, что вы используете менеджер пакетов, такой как npm, у вас будет файловая структура, которая выглядит следующим образом:

```txt
your-project/
├── scss
│   └── custom.scss
└── node_modules/
    └── bootstrap
        ├── js
        └── scss
```

Если Вы загрузили наши исходные файлы и не используете менеджер пакетов, Вам нужно вручную настроить что-то похожее на эту структуру, сохраняя исходные файлы Bootstrap отдельно от Ваших собственных.

```txt
your-project/
├── scss
│   └── custom.scss
└── bootstrap/
    ├── js
    └── scss
```

## Значения переменных по умолчанию

Every Sass variable in Bootstrap includes the !default flag allowing you to override the variable’s default value in your own Sass without modifying Bootstrap’s source code. Copy and paste variables as needed, modify their values, and remove the !default flag. If a variable has already been assigned, then it won’t be re-assigned by the default values in Bootstrap.

> Не перевод, а уяснение...
> Каждая Sass переменная в Bootstrap имеет флаг `!default` позволяющий переопределить (override) значение переменной по умолчанию в одном или нескольких SASS файлах пользователя специально созданных для кастомизации. При этом исходный код Bootstrap пользователем не редактируется. По мере необходимости, переменные, подлежащие изменению, нужно скопировать пользовательский SASS файл, внести необходимые изменения и удалить флаг `!default`. Переменная не будет повторно назначена значениями по умолчанию Bootstrap, так как ранее она уже была определена пользователем.
>
> Полный список переменных Bootstrap приведен в файле `scss/_variables.scss`. Некоторые переменные имеют значение `null` - означающее, что свойства не выводятся, если они не переопределены в конфигурации пользователя.

А тут совсем непонятно - где "наши", где "ваши":

Дословно:

> Variable overrides must come after our functions are imported, but before the rest of the imports.

Перевод сообщества:

>Переопределения переменных должны происходить после импорта наших функций, но до остального импорта.

Перевод с русского - на русский (проверено, работает):

Порядок импорта

1. Пользовательские изменения Bootstrap (без флага `!default`);
2. Bootstrap (с флагом `!default`, если надо);
3. Все остальное (имеет высший приоритет).

Получается, что загрузка пользовательских SASS файлов, с переопределенными переменными должны происходить до (а не после) импорта функций Bootstrap и остального импорта.

## Hugo Подключение шрифтов

```txt
hugo-rfi-bs5cover/
└── bootstrap/
      ├── custom-bs/
      │     ├── _fonts.scss
      │     ├── _colors.scss
      │     └── core.scss
      └── scss/
```

Импорт - `assets/style.sass`:

```sass
@import "bootstrap/custom-bs/core"
@import "bootstrap/scss/bootstrap"
@import "scss-rfi/core"
```

### Как в bootstrap !default

bs5 _variables.scss 418-424

``` scss
// scss-docs-start font-variables
// stylelint-disable value-keyword-case

$font-family-sans-serif: system-ui,
-apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans",
"Liberation Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI
Symbol", "Noto Color Emoji" !default; $font-family-monospace: SFMono-Regular,
Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace !default;

// stylelint-enable value-keyword-case
$font-family-base: var(--#{$variable-prefix}font-sans-serif) !default;
$font-family-code: var(--#{$variable-prefix}font-monospace) !default;
````

### Имеем - без !default

hugo-rfi-bs5cover/assets/bootstrap/custom-bs/_fonts.scss

``` scss
$font-family-sans-serif: 'Fira Sans', 'Golos', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, 'Noto Sans', 'Liberation Sans', sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';

$font-family-monospace: 'Fira Code', SFMono-Regular, Menlo, Monaco, Consolas, 'Liberation Mono', 'Courier New', monospace;
```

Работает хорошо!

### Пример подключения в hugo теме [hugo-serif-theme]()

<!-- /atom-sites/themes_example/hugo-serif-theme/layouts/partials/google-fonts.html -->

layouts/partials/google-fonts.html

``` html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&display=swap" rel="stylesheet" />
```

This theme uses Google fonts. You can change the font snippet in `layouts/partials/google-fonts.html` and then update font variable in `scss/style.scss`

```scss
// scss/style.scss - у нас файл scss/style.sass

// Fonts
$font-family-base: Helvetica, Arial, sans-serif, -apple-system;
$font-family-heading: "Playfair Display", serif, -apple-system;
```

здесь же и подключение (глобально)!

```html
body { font-size: 16px; line-height: 1.2; font-family: $font-family-base;
@include media-breakpoint-up(md) { font-size: 16px; line-height: 1.3; } }
```

### Colors

You can edit the themes primary, secondary and neutral colors in `scss/style.scss`. To override the bootstrap colors simply edit `scss/_bootstrap-variables.scss`

```scss
// scss/style.scss

// Colors
$primary: #f24088;
$secondary: #f88379;
$black: #2f2f41;
$white: #ffffff;
$white-offset: #f6f7ff;
$steel: #5c5a5a;
```
