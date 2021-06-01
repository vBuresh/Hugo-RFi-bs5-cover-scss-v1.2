# Тема ReFreshing-bs5-cover для Hugo

На сайте Bootstrap даются [примеры сайтов](https://getbootstrap.com/docs/5.0/examples/), разработанных командой Bootstrap. Они предназначены для оказания помощи пользователям быстро начать свой проект - от использования частей фреймворка до настраиваемых компонентов `partials` и `layouts`, на основе любого образца.

## Шаблон "Cover"

> Quickly get a project started with any of our examples ranging from using parts of the framework to custom components and layouts.

Среди примеров по-своему интересен одностраничный шаблон **Cover**, предлагаемый для создания простых и красивых домашних страниц.

> A one-page template for building simple and beautiful home pages

Он отличается, прежде всего, простотой и лаконичностью (без аскетизма), компактностью, гармоничностью и прочими достоинствами.

## Практика применения шаблона "Cover" в Hugo

Исходники проекта [размещены на GitHub](https://github.com/vBuresh/Hugo-RFi-bs5-cover). Нужно "форкнуть" проект и найти его в своем репозитории GitHub. Затем, переименовать его, присвоив имя Hugo-RFm-bs5-cover. После этого - клонировать проект в рабочую директорию: `./atom-sites/`

Исходники примера "Cover" - в директории `exampleSite/examples_bs5-cover`. Здесь же находится и файл `cover.html`. Полный путь к нему: `/home/w/vdev/atom-sites/_RFi-cover/exampleSite/examples_bs5-cover/cover.html`. Это полный действующий автономный пример "Cover" (использует интернет-ресурсы, необходимо интернет-подключение!).

Исходный код файла содержит комментарии, которые помогут выделить фрагменты, для шаблонов директории `layouts`:

1.  default/baseof.html
2.  partials/head.html
3.  partials/header.html
4.  partials/footer.html
5.  index.html

### Первый этап

На первом этапе нужно:

1.  файл `default/baseof.html` (теги `<html>`, `<body>`, `<div id="content">`) привести соответствие с файлом `cover.html`

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

2.  В файлы директории `layouts`:

-   \_default/baseof.html
-   partials/head.html
-   partials/header.html
-   partials/footer.html
-   index.html

поместить (в режиме "как есть" - copy/paste) содержимое соответствующих фрагментов файла `cover.html` (см. комментарии в файле `cover.html`)

Следует обратить внимание, что файл `layouts/index.html` по умолчанию, является шаблоном главной страницы (homepage) создаваемого сайта. Его содержимое должно начинаться с определения: `{{ define "main" }}` (закрывается: `{{ end }}`).

> _Важно:_
> _Отсутствие определения `define "main"` может исказить отображение главной страницы в браузере._

В завершении нужно командой `hugo server` собрать сайт и посмотреть его в браузере.

Цель - получить такой же внешний вид главной страницы, как на образце.

По выполнении заданий первого этапа следует провести тщательное тестирование. Затем нужно "закоммитить" каждое изменение (stage, commit to muster) и "залить" в удаленный репозиторий GitHub (Push).

### Второй этап

На этом этапе требуется привести в соответствие с рекомендациями разработчиков Hugo следующие шаблоны:

-   layouts/\_default/baseof.html
-   layouts/index.html
-   layouts/\_default/list.html
-   layouts/\_default/single.html

#### Шаблон `\_default/baseof.html`

Разработчики Hugo рекомендуют при разработке шаблона `\_default/baseof.html` пользоваться следующим примером:

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

#### Шаблон homepage - `layouts/index.html`

Особенности его разработки шаблона главной страницы (homepage) layouts/index.html изложены на странице [Homepage Template](https://gohugo.io/templates/homepage/). Там же приведен пример

Особенности его разработки

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

### Третий этап

На втором этапе:

1.  подключить `sidebar` и автоматизировать его (теги),
2.  автоматизировать `navbar` (автоматическое формирование -по таксономии),
3.  создать необходимые Gulp задачи, и очистить устаревшие и сформировать актуальные "активы" проекта:
    -   assets/bootstrap/scss
    -   assets/css/cover.css
    -   assets/css/dark-mode.css
    -   assets/css/refreshing.css
    -   assets/js/bootstrap.bundle.min.js
    -   assets/js/dark-mode-switch.js
    -   static/js/bootstrap.bundle.min.js.map
4.  автоматизировать формирование метаданных в элементе [`<head>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/head),
5.  создать подключить автономные:
    -   layouts/partials/scripts.html
    -   layouts/partials/stylesheets.html
    -   layouts/partials/favicons.html
    -   подключить автономные `stylesheets` и `scripts`.
6.  разработать `config.yaml`
7.  автоматизировать [footer](https://developer.mozilla.org/ru/docs/Web/HTML/Element/footer)
8.  подключить dark-mode switcher
