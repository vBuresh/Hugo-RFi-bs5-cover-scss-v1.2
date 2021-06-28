# Тема ReFreshing-bs5-cover для Hugo

**ReFreshing-bs5-cover** is a theme for the [Hugo](https://gohugo.io) - world’s fastest framework for building websites which is based on sleek, intuitive, and powerful front-end framework [Bootstrap 5](https://github.com/twbs/bootstrap). The **ReFreshing-bs5-cover** theme is most suitable for for personal website and magazine like blog template with header, navigation, featured content.

> Quickly get a project started with any of our examples ranging from using parts of the framework to custom components and layouts.

Цель проекта **Hugo-RFi-bs5-cover** - создать тему для популярного генератора статических сайтов **Hugo** с применением [Bootstrap 5](https://github.com/twbs/bootstrap) и шаблона **Cover**, представленного на Bootstrap в качестве одного из [примеров](https://getbootstrap.com/docs/5.0/examples/), разработанных командой фреймворка. Эти примеры хорошо помогают пользователям быстро начать свой проект.

## Шаблон "Cover"

> A one-page template for building simple and beautiful home pages

Одностраничный шаблон **Cover**  (разработчик: Mark Otto - <a href="https://twitter.com/mdo" class="text-white">@mdo</a>), который предлагается использовать для создания простых и красивых домашних страниц, привлекает своей простотой и лаконичностью (без аскетизма), а также компактностью и гармоничностью. Он обладает и рядом других достоинств.

## Разработка темы для Hugo на основе "Cover"

<!-- Исходники проекта [размещены на GitHub](https://github.com/vBuresh/Hugo-RFi-bs5-cover). Нужно "форкнуть" проект и найти его в своем репозитории GitHub. Затем, переименовать его, присвоив имя Hugo-RFm-bs5-cover. После этого - клонировать проект в рабочую директорию: `./atom-sites/`

Исходники примера "Cover" - в директории `exampleSite/examples_bs5-cover`. Здесь же находится и файл `cover.html`. Полный путь к нему: `/home/w/vdev/atom-sites/_RFi-cover/exampleSite/examples_bs5-cover/cover.html`. Это полный действующий автономный пример "Cover" (использует интернет-ресурсы, необходимо интернет-подключение!). -->

Для начала работы и определения задач и этапов их выполнения необходимо сформировать файл `cover.html`, содержащий исходный код примера. Нужно внимательно изучить его, выделить фрагменты, для формирования файлов-шаблонов в директории `layouts`:

1.  default/baseof.html
2.  partials/head.html
3.  partials/header.html
4.  partials/footer.html
5.  index.html

Каждый фрагмент следует дополнить комментариями, чтобы было ясно - куда его копировать из `cover.html` в соответствующий файл директории `layouts`. При этом важно помнить, что крайне нежелательно дублирование фрагментов.

### Первый этап

На первом этапе копируются соответствующие фрагменты в вышеперечисленные файлы.

1.  Файл `default/baseof.html`.

Файл `default/baseof.html` поставляется с таким кодом:

```html
<!DOCTYPE html>
<html>
    {{- partial "head.html" . -}}
    <body>
        {{- partial "header.html" . -}}
        <div id="content">
        {{- block "main" . }}{{- end }}
        </div>
        {{- partial "footer.html" . -}}
    </body>
</html>
```

Требуется привести  теги `<html>`, `<body>`, `<div id="content">` в соответствие с примером `cover.html`

2.  Поместить (в режиме "как есть" - copy/paste) содержимое соответствующих фрагментов файла `cover.html` (согласно комментариям) в следующие файлы:

    -   layouts/partials/head.html
    -   layouts/partials/header.html
    -   layouts/partials/footer.html
    -   layouts/index.html

Следует обратить внимание, что файл `layouts/index.html` по умолчанию, содержит шаблон главной страницы (homepage) создаваемого сайта. В начале его кода помещается определение: `{{ define "main" }}`, а в конце - закрывается: `{{ end }}`).

> _Важно:_
> _Отсутствие определения `define "main"` может исказить отображение главной страницы в браузере._

В завершении нужно собрать сайт (командой `hugo server`), его в браузере. В другом окне браузера - открыть файл `cover.html`. Сравнить и убедится, что оба файла выглядят абсолютно одинаково. Если нет - найти и устранить причины искажений. Цель - получить такой же внешний вид главной страницы, как на образце.

После тщательного тестирования "закоммитить" изменения в каждом файле проекта (stage, commit to muster) и "залить" изменения в удаленный репозиторий GitHub (Push).

### Второй этап

На этом этапе требуется привести в соответствие с рекомендациями разработчиков Hugo следующие шаблоны:

-   layouts/\_default/baseof.html
-   layouts/index.html
-   layouts/\_default/list.html
-   layouts/\_default/single.html

#### Шаблон `\_default/baseof.html`

В [документации](https://gohugo.io/templates/base/#define-the-base-template) **Hugo** приводится файл `\_default/baseof.html` в таком виде:

```html
<!-- Источник: Define the Base Template (https://gohugo.io/templates/base/#define-the-base-template) -->
<!DOCTYPE html>
  <html>
    <head>
      <meta charset="utf-8">
        <title>{{ block "title" . }}
          <!-- Blocks may include default content. -->
          {{ .Site.Title }}
          {{ end }}</title>
    </head>
    <body>
       <!-- Code that all your templates share, like a header -->
       {{ block "main" . }}
       <!-- The part of the page that begins to differ between templates -->
       {{ end }}
       {{ block "footer" . }}
       <!-- More shared code, perhaps a footer but that can be overridden if need be in  -->
       {{ end }}
    </body>
</html>
```

Пример демонстрирует содержимое элемента [`<head>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/head), задача которого — хранить метаданные документа. Интересен и пример автоматизации: `block "title"`, тег `<title>`. В комментариях сообщается, что в блок можно поместить постоянное содержимое, кроме того, сюда же автоматически "подтягивается" информация из поля `title:` конфигурационного файла, который содержит глобальные настройки и данные и сведения.

> Наши "вдохновители" демонстрируют более интересную разработку `<title>`.

#### Шаблон homepage - `layouts/index.html`

Особенности разработки шаблона главной страницы (homepage) `layouts/index.html` хорошо изложены на странице [Homepage Template](https://gohugo.io/templates/homepage/). Там же приведен следующий пример:

```html
<!--
Источник: Homepage Template (https://gohugo.io/templates/homepage/)
 -->
{{ define "main" }}
<main aria-role="main">
  <header class="homepage-header">
    <h1>{{.Title}}</h1>
    {{ with .Params.subtitle }}
    <span class="subtitle">{{.}}</span>
    {{ end }}
  </header>
  <div class="homepage-content">
  <!-- Note that the content for index.html, as a sort of list page, will pull from content/_index.md -->
  {{.Content}}
  </div>
  <div>
  {{ range first 10 .Site.RegularPages }}
  {{ .Render "summary"}}
  {{ end }}
  </div>
</main>
{{ end }}
```

#### Шаблон - `layouts/\_default/list.html`

```html
<!-- Источник: Override the Base Template (https://gohugo.io/templates/base/#override-the-base-template) -->
{{ define "main" }}
  <h1>Posts</h1>
  {{ range .Pages }}
    <article>
      <h2>{{ .Title }}</h2>
      {{ .Content }}
    </article>
  {{ end }}
{{ end }}
```

#### Шаблон - `layouts/\_default/single.html`

##### Пример 1

См. [Example: Override the Base Template](https://gohugo.io/templates/base/#override-the-base-template)

```html
{{ define "title" }}
  <!-- This will override the default value set in baseof.html; i.e., "{{.Site.Title}}" in the original example-->
  {{ .Title }} &ndash; {{ .Site.Title }}
{{ end }}
{{ define "main" }}
  <h1>{{ .Title }}</h1>
  {{ .Content }}
{{ end }}
```

##### Пример 2

См. [Example Single Page Templates](https://gohugo.io/templates/single-page-templates/)

posts/single.html
This single page template makes use of Hugo base templates, the .Format function for dates, the .WordCount page variable, and ranges through the single content’s specific taxonomies. with is also used to check whether the taxonomies are set in the front matter.

```html
{{ define "main" }}
<section id="main">
  <h1 id="title">{{ .Title }}</h1>
  <div>
        <article id="content">
           {{ .Content }}
        </article>
  </div>
</section>
<aside id="meta">
    <div>
    <section>
      <h4 id="date"> {{ .Date.Format "Mon Jan 2, 2006" }} </h4>
      <h5 id="wordcount"> {{ .WordCount }} Words </h5>
    </section>
    {{ with .Params.topics }}
    <ul id="topics">
      {{ range . }}
        <li><a href="{{ "topics" | absURL}}{{ . | urlize }}">{{ . }}</a> </li>
      {{ end }}
    </ul>
    {{ end }}
    {{ with .Params.tags }}
    <ul id="tags">
      {{ range . }}
        <li> <a href="{{ "tags" | absURL }}{{ . | urlize }}">{{ . }}</a> </li>
      {{ end }}
    </ul>
    {{ end }}
    </div>
    <div>
        {{ with .PrevInSection }}
          <a class="previous" href="{{.Permalink}}"> {{.Title}}</a>
        {{ end }}
        {{ with .NextInSection }}
          <a class="next" href="{{.Permalink}}"> {{.Title}}</a>
        {{ end }}
    </div>
</aside>
{{ end }}
```

### Третий этап

На третьем этапе требуется:

1.  Подключить `sidebar` и автоматизировать его (теги)

См. bs5 Documents: [Offcanvas](https://getbootstrap.com/docs/5.0/components/offcanvas/)

#### Подключение сайдбара

Для подключения сайдбара потребуется создать два файла:

-   `layouts/partials/sidebar-btn-inset.html` - для кода кнопки управления
-   `layouts/partials/sidebar.html` - для основного кода сайдбара.

Начнем с малого - в файл `layouts/partials/sidebar-btn-inset.html` поместим следующий код [из комплекта Icons](https://icons.getbootstrap.com/icons/layout-sidebar-inset/):

```html
<!-- прверить: id="offcanvasWithBackdrop" -->
<a class="btn pt-3" data-bs-toggle="offcanvas" href="#offcanvasWithBackdrop" role="button" aria-controls="offcanvasWithBackdrop">
  <svg id="layout-sidebar-inset" width="1.5em" height="1.5em" fill="#00D1B2" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
    <path d="M14 2a1 1 0 0 1 1 1v10a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V3a1 1 0 0 1 1-1h12zM2 1a2 2 0 0 0-2 2v10a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V3a2 2 0 0 0-2-2H2z" />
    <path d="M3 4a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v8a1 1 0 0 1-1 1H4a1 1 0 0 1-1-1V4z" />
  </svg>
</a>
```

После этого в файл `layouts/partials/sidebar.html` скопируем код из примера [Live demo](https://getbootstrap.com/docs/5.0/components/offcanvas/#live-demo). Первые два aбзаца с примером кнопок управления нужно удалить, так как ранее эта кнопка уже была сделана. Затем нужно найти ID, адреса и пр., с префиксом "offcanvasExample" и заменить на "offcanvasWithBackdrop" (Find/Replace).

После этого помещаем кнопку в navbar, код которого пока находится в файле `layouts/partials/header.html`. Просто заменяем тег `h3` его содержимое следующим кодом:

```html
<h3 class="float-md-start mb-0">
  {{- partial "sidebar-btn-inset.html" . -}}
  Cover
</h3>
```

Собираем сайт и проверяем работоспособность сайдбара.

> Внимание!
>
> Работа сайдбрара невозможна без подключенных js.

Необходимо убедиться, что в файле примера cover.html после тега `<footer>` есть следующая строка:

```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-gtEjrD/SeCtmISkJkNUaaKMoLD0//ElJ19smozuHV6z3Iehds+3Ulb9Bn9Plx0x4" crossorigin="anonymous"></script>
```

Если такой строки нет, то ее необходимо добавить в файл примера cover.html, и в файл `layouts/partials/footer.html`.

При проверке работоспособности сайдбара следует обратить внимание на его открытие кнопкой, вставленной нами в `navbar`, а также на закрытие - щелчком мыши вне его или нажатием кнопки `[ X ]` в шапке сайдбара. Эту кнопку можно заменить на парную той, что мы вставили в `navbar`. Вероятно, для пользователей так будет понятнее пользователю: "Чем открыли - тем и закрываем. И никаких крестов!". Для этого нужно создать еще один файл - `layouts/partials/sidebar-btn-inset.html`

Содержимое файла `layouts/partials/sidebar-btn-inset-reverse.html` - layout-sidebar-inset [из комплекта Icons](https://icons.getbootstrap.com/icons/layout-sidebar-inset-reverse/):

```html
<!-- id="offcanvasWithBackdrop" -->
<a class="btn" data-bs-toggle="offcanvas" href="#offcanvasWithBackdrop" role="button" aria-controls="offcanvasWithBackdrop">
  <svg id="sidebar-inset-reverse" width="1.5em" height="1.5em" fill="#00D1B2" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
    <path d="M2 2a1 1 0 0 0-1 1v10a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1V3a1 1 0 0 0-1-1H2zm12-1a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V3a2 2 0 0 1 2-2h12z"/>
  <path d="M13 4a1 1 0 0 0-1-1h-2a1 1 0 0 0-1 1v8a1 1 0 0 0 1 1h2a1 1 0 0 0 1-1V4z"/>
  </svg>
</a>
```

Осталось только заменить в строке 5 файла `_hugo-RFi-bs5-cover/layouts/partials/sidebar.html` содержимое тега `<button>` на:

```html
<!-- <button type="button" class="btn-close text-reset" data-bs-dismiss="offcanvas" aria-label="Close"></button> -->
      {{- partial "sidebar-btn-reverse.html" . -}}
```

Снова проверяем работоспособность сайбара и действие кнопок. При этом обратим внимание на его кнопку в `navbar`. Она вписывается, точнее, "вторгается" в логотип. С таким решением могут не согласиться некоторые пользователи, Так как обычно особое внимание придается всякого рода "брендам". Поэтому эту кнопку вынести к левой границе экрана.
для этого удаляем в строку 5 файла `_hugo-RFi-bs5-cover/layouts/partials/sidebar.html` и переносим ее содержимое `{{- partial "sidebar-btn.html" . -}}` в файл `layouts/_default/baseof.html`, сразу после открывающего  тега `<body>`:

```html
  <body class="d-flex h-100 text-center text-white bg-dark">
    {{- partial "sidebar-btn-inset.html" . -}}
  <div class="cover-container d-flex w-100 h-100 p-3 mx-auto flex-column">
```

Вновь проверяем работоспособность сайбара и действие кнопок. Также убеждаемся в целесообразности замены "креста на кнопку". Затем - следующая задача.

2.  Сформировать "активы" проекта (scss, css, js, icons, images):

#### Автоматизация компонентов

Для активов проекта предназначены директории:

-   `assets` - содержит активы, подлежащие обработке Hugo (по умолчанию - отсутствует).
-   `static` - хранит активы, которые не требуют обработки Hugo и будут загружены в соответствуюшие директории готового сайта "как есть".

Для работы сайта требуется следующие активы:

-   assets/bootstrap/scss
-   assets/css/cover.css
-   assets/css/dark-mode.css
-   assets/css/refreshing.css
-   assets/js/bootstrap.bundle.min.js
-   assets/js/dark-mode-switch.js
-   static/js/bootstrap.bundle.min.js.map

Из можно загрузить вручную, но это "не наши методы". Нужно автоматизировать задачу при помощи Gulp или WebPack.

3.  автоматизировать формирование метаданных в элементе [`<head>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/head):

Сначала необходимо разработать и подключить автономные файлы активов:

1.  layouts/partials/stylesheets.html
1.  layouts/partials/scripts.html

Наполнение - см. первоначальную  разработку.

В файл конфигурации добавляем настройки обработки активов:

``` yaml
params:

  # option to specify the favicon image of the site
  # the path is relative to the folder "assetDir" of this configuration
  favicon: "/images/favicon-rfi.svg"

  # parameter used to specify if you want to minify the imported js
  jsMinify: false
  # parameter used to specify if you want to minify the imported css
  cssMinify: false
  # parameter used to specify if you want to calculate the css integrity
  cssIntegrity: true
  # parameter used to specify if you want to calculate the js integrity
  jsIntegrity: true
  # option to specify the main colour of the theme
  mainColour: "#F39200"
```

Для подключения favicons предусмотрен файл:  `layouts/partials/favicons.html`. Его наполнение рассмотрим в конце разработки. Сейчас в конфигурации определено: `favicon: "/images/favicon-rfi.svg"`).

- Местоположение: ./assets/images/favicon-rfi.svg
- Допустимо:      ./static/images/favicon-rfi.svg

среда, 9 июня 2021 г., 12:42

Подробно об изменениях см. в коммитах.

##### Таксономия

Это одна из интереснейших возможностей Hugo, которую нужно грамотно реализовать. Значит в очередной раз придается изучить и понять следующие страница руководства Hugo:

1.  [taxonomies](<https://gohugo.io/content-management/1. taxonomies>)
2.  Taxonomy Templates
3.  Archetypes
4.  Lists of Content in Hugo
5.  Taxonomy Variables
6.  Front Matter


4.  автоматизировать `navbar` (автоматическое формирование -по таксономии),
5.  автоматизировать [footer](https://developer.mozilla.org/ru/docs/Web/HTML/Element/footer)
6.  подключить `dark-mode switcher`
7.  разработать `config.yaml`

## Разработка `config.yaml`

Настройка оглавления [Table Of Contents](https://gohugo.io/getting-started/configuration-markup#table-of-contents)

```yaml
markup:
  goldmark:
    renderer:
      unsafe:            true
  highlight:
    noClasses:           false
  tableOfContents:
    startLevel: 2
    endLevel: 4
    ordered: false
```

These settings only works for the **Goldmark** renderer:

-   **startLevel** - The heading level, values starting at 1 (h1), to start render the table of contents.
-   **endLevel** - The heading level, inclusive, to stop render the table of contents.
-   **ordered** - Whether or not to generate an ordered list instead of an unordered list.
