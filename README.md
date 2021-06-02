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

2. Поместить (в режиме "как есть" - copy/paste) содержимое соответствующих фрагментов файла `cover.html` (согласно комментариям) в файлы:

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

В документации **Hugo** приводится файл `\_default/baseof.html` в таком виде:

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

> Наши "вдохновители" демонстрируют более глубокую разработку `<title>`.


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

```html
<!-- Источник: Override the Base Template (https://gohugo.io/templates/base/#override-the-base-template) -->
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

[Example Single Page Templates](https://gohugo.io/templates/single-page-templates/)

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

1.  Создать необходимые Gulp задачи и сформировать актуальные "активы" проекта (предварительно следует очистить устаревшие):

    -   assets/bootstrap/scss
    -   assets/css/cover.css
    -   assets/css/dark-mode.css
    -   assets/css/refreshing.css
    -   assets/js/bootstrap.bundle.min.js
    -   assets/js/dark-mode-switch.js
    -   static/js/bootstrap.bundle.min.js.map

2.  автоматизировать формирование метаданных в элементе [`<head>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/head):

    -   разработать и подключить автономные файлы активов:

        -   layouts/partials/scripts.html
        -   layouts/partials/stylesheets.html
        -   layouts/partials/favicons.html

3.  подключить `sidebar` и автоматизировать его (теги),
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
