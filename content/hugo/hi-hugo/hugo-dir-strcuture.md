---
title: "Структура директорий Hugo"
date: 2019-10-30T08:06:44+03:00
Lastmod: 2020-08-03T16:20:26+03:00
draft: false
categories:
  - "Hugo"
  - "frontend"
  - "example"
tags:
- "example"
- "styles"
- "hugo"
---

<!-- TOC -->

- [Директории Hugo](#hugoDir)
- [archetypes - архитипы (шаблоны)](#archetypes)
- [assets - директория ресурсов](#assets)
- [Hugo Pipes](#hugoPipes)
  - [Директория активов](#assetDirectory)
  - [Ивлечение из файла - в ресурс](#fileToResource)
  - [Публикация assets](#assetPublishing)
  - [Go Pipes](#go-pipes)
  - [Method aliases (псевдонимы)](#method-aliases-%D0%BF%D1%81%D0%B5%D0%B2%D0%B4%D0%BE%D0%BD%D0%B8%D0%BC%D1%8B)
  - [SASS / SCSS](#sass--scss)
  - [Options](#options)
    - [targetPath [string]](#targetpath-string)
    - [outputStyle [string]](#outputstyle-string)
    - [precision [int]](#precision-int)
    - [enableSourceMap [bool]](#enablesourcemap-bool)
    - [includePaths [string slice]](#includepaths-string-slice)
  - [Asset minification](#asset-minification)
  - [Asset bundling](#asset-bundling)
  - [Создание (добавление) контента](#%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BA%D0%BE%D0%BD%D1%82%D0%B5%D0%BD%D1%82%D0%B0)
- [Links and Cross References](#links-and-cross-references)
- [Anchors](#anchors)

<!-- /TOC -->

Новый сайт [Hugo](https://gohugo.io) генерируется командой (в терминале) `$ hugo new site newSiteName`. В результате ее выполнения выдается сообщение:

{{< highlight bash "linenos=table,hl_lines=2 11" >}}
w@deb-del:~$ hugo new site hugo-gen-site
Congratulations! Your new Hugo site is created in /home/w/hugo-gen-site.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
w@deb-del:~$
{{< /highlight >}}

Помимо поздравления о создании нового сайта и указания пути к его директории, сообщается о возможности дальнейших действиях, которые может выполнить пользователь. Во-первых, предлагается скачать и установить тему. На сайте  [Hugo](https://themes.gohugo.io/) создан специальный раздел, где можно получить не только информацию о теме, но и посмотреть любую из них в действии. Во-вторых, есть возможность приступить сразу к созданию контента при помощи команды `<SECTIONNAME>/<FILENAME>.<FORMAT>`. В-третьих, сообщается, что командой `hugo server` можно сразу запустить сайт. Однако, запускать его пока рановато. Прежде рассмотрим что создал Hugo.

## Директория сайта

По умолчанию директория сайта *newSiteName* имеет следующую структуру:

{{< highlight txt "linenos=true" >}}
newSiteName
       ├── /archetypes
       |         └── default.md
       ├── /content
       ├── /data
       ├── /layouts
       ├── /static
       ├── /themes
       └── /config.toml
{{< /highlight >}}

Просмотр содержимого директории вызывает сомнения, что создан сайт. Всего 6 совершенно пустых директорий и один конфигурационный файл `config.toml`. Правда, еще один файл `default.md` можно найти в директории `archetypes`. Он пригодится при создании контента. Все правильно. Без контента сайта быть не может. Но Hugo может запустить сайт в таком виде. И вот что получится:

{{< codeHTML >}}
<div class="row row-cols-1 row-cols-md-3 g-4">
    <div class="col">
        <div class="card">
           <a href="/images/hugo/hugo20200803-193443-new-site.png" target="_blank">
             <img src="/images/hugo/hugo20200803-193443-new-site.png" class="card-img-top" alt="...">
           </a>
           <div class="card-body">
             <p class="card-text">Терминал: hugo server</p>
           </div>
        </div>
    </div>
    <div class="col">
        <div class="card">
        <a href="/images/hugo/hugo20200803-193458-new-site.png" target="_blank">
            <img src="/images/hugo/hugo20200803-193458-new-site.png" class="card-img-top" alt="...">
        </a>
        <div class="card-body">
             <p class="card-text">Команда выполнена</p>
           </div>
        </div>
    </div>
    <div class="col">
        <div class="card">
        <a href="/images/hugo/hugo20200803-193619-new-site.png" target="_blank">
            <img src="/images/hugo/hugo20200803-193619-new-site.png" class="card-img-top" alt="...">
        </a>
        <div class="card-body">
             <p class="card-text">http://localhost:1313</p>
           </div>
        </div>
    </div>
</div>
{{< /codeHTML >}}



## Установка темы для Hugo

Как уже говорилось, перечень тем находится на сайте Hugo, в разделе [Themes](https://themes.gohugo.io/). Так как выбор - дело не легкое, то лучше скачать несколько тем, чтобы глубже изучить и сравнить их особенности. Следует отметить, что лучше скачать несколько тем и поработать с каждой из них некоторое время. Благо для подключения темы требуется лишь указать ее название в конфигурационном файле.

[Hugo ReFresh](https://themes.gohugo.io/hugo-refresh/)

[Порядок установки темы ReFresh](/hugo/themes/refresh/rj_readme)


## Создание собственной темы.


{{< highlight txt "linenos=true" >}}
newThemeName
       ├── /archetypes
       ├── /layouts
       ├── /static
       ├── /LICENSE // The MIT License (MIT)
       └── /theme.toml
{{< /highlight >}}


Таким образом, можно разработать свою тему и выложить ее на . как это сделать рассматривается в разделе [Add Your Hugo Theme to the Showcase](https://gohugo.io/contribute/themes/) документации.



## О добавлении своей темы в репозиторий

Подробно о добавлении своей темы в репозиторий [GitHub hugoThemes](https://github.com/gohugoio/hugoThemes) говорится в  [инструкции](https://github.com/gohugoio/hugoThemes#adding-a-theme-to-the-list). Интересно, что прежде предлагается протестировать свою тему с специально разработанным содержимым директории *content* на [Hugo Basic Example repository](https://github.com/gohugoio/hugoBasicExample). Это то, что надо!

Там же инструкция по тестингу. Установил сюда: `/home/w/vdev/vGitHub/hugoBasicExample`. Подключил тему - все работает! Ура, тема разработана! Осталась доводка. А это, пожалуй, самая ответственная часть дела.

Кроме того, Hugo поддерживает расширенную поддержку тем с помощью Theme Components. Это очень интересная возможность. [Подробнее...](https://gohugo.io/hugo-modules/theme-components)

## archetypes - архитипы (шаблоны)

[archetypes](https://gohugo.io/content-management/archetypes/)

Архетипы - это шаблоны, используемые при создании нового контента.

Новые файлы содержимого в Hugo, создаются командой `hugo new`
По умолчанию `hugo new` создаст новые файлы содержимого, как минимум:
- заголовком (выведенным из имени файла)
- с датой создания, в допустимом формате
- и атрибутом `draft: true`.

Это экономит время и обеспечивает согласованность сайтов, использующих различные типы контента.

Кроме того, есть возможность создавать свои собственные (пользовательские) архетипы с предварительно настроенными полями, например, `draft: false`.


Кроме того, можно сразу создать свою тему командой


## assets -  директория ресурсов

[assets - директория ресурсов](#assets)

**assets** - директория ресурсов создается при необходимости. По умолчанию её нет.
В **assets** хранятся все файлы, подлежащие обработке [Hugo Pipes](https://gohugo.io/hugo-pipes/introduction/).

При этом, в общедоступной директории будут опубликованы только файлы, для которых используются `.Permalink` или `.RelPermalink`,

From file to resource

## Hugo Pipes

Hugo Pipes - это набор функций Hugo для обработки активов.


### Директория активов

>Файлы активов должны храниться в директориях ресурсов -  по умолчанию - `/assets` (его можно изменить с помощью ключа `assetDir` файла конфигурации).


### Извлечение из файла - в ресурс

Чтобы обработать актив с помощью [Hugo Pipes](https://gohugo.io/hugo-pipes/introduction/), он должен быть извлечен как ресурс с использованием `resources.Get`, который принимает один аргумент: путь к файлу относительно директории ресурса.

``` bash
{{ $style := resources.Get "sass/main.scss" }}
```
См. материалы

[hugo-refresh-integration.md](#css-fontsSetup)


>Таким образом, все пользовательские SCSS достаточно положить в директорию `/assets`


### Публикация assets

Assets будут опубликованы (для` /public`) только в том случае, если используются `.Permalink` или `.RelPermalink.`

### Go Pipes

Для улучшения читабельности примеры документации Hugo Pipes написаны с использованием Go Pipes:

``` bash
{{ $style := resources.Get "sass/main.scss" | resources.ToCSS | resources.Minify | resources.Fingerprint }}
<link rel="stylesheet" href="{{ $style.Permalink }}">
```

См. также...

[Минификация активов (assets)](#assetsМin)



### Method aliases (псевдонимы)

Each Hugo Pipes resources transformation method uses a camelCased alias (toCSS for resources.ToCSS). Non-transformation methods deprived of such aliases are resources.Get, resources.FromString, resources.ExecuteAsTemplate and resources.Concat.

The example above can therefore also be written as follows:


Каждый метод преобразования ресурсов **Hugo Pipes** использует псевдоним **camelCased** (toCSS for resources.ToCSS). Методы без преобразования, лишенные таких псевдонимов, представляют собой `resources.Get`, `resources.FromString`, `resources.ExecuteAsTemplate` и `resources.Concat`.

Поэтому приведенный выше пример также можно записать следующим образом:

``` bash
{{ $style := resources.Get "sass/main.scss" | toCSS | minify | fingerprint }}
<link rel="stylesheet" href="{{ $style.Permalink }}">
```
### SASS / SCSS

Hugo Pipes allows the processing of SASS and SCSS files.

Any SASS or SCSS file can be transformed into a CSS file using resources.ToCSS which takes two arguments, the resource object and a map of options listed below.

``` bash
{{ $sass := resources.Get "sass/main.scss" }}
{{ $style := $sass | resources.ToCSS }}
```

### Options

#### targetPath [string]
    If not set, the resource’s target path will be the asset file original path with its extension replaced by .css.

#### outputStyle [string]
    Default is nested. Other available output styles are expanded, compact and compressed.

#### precision [int]
    Precision of floating point math.

#### enableSourceMap [bool]
    When enabled, a source map will be generated.

#### includePaths [string slice]

    Additional SCSS/SASS include paths. Paths must be relative to the project directory.

``` bash
{{ $options := (dict "targetPath" "style.css" "outputStyle" "compressed" "enableSourceMap" true "includePaths" (slice "node_modules/myscss")) }}
{{ $style := resources.Get "sass/main.scss" | resources.ToCSS $options }}
```

>Setting outputStyle to compressed will handle SASS/SCSS files minification better than the more generic resources.Minify.


## Минификация активов (assets)" "assetsМin"

Hugo Pipes allows the minification of any CSS, JS, JSON, HTML, SVG or XML resource.

Any resource of the aforementioned types can be minifed using resources.Minify which takes for argument the resource object.

``` bash
{{ $css := resources.Get "css/main.css" }}
{{ $style := $css | resources.Minify }}
```

### Asset bundling

Hugo Pipes can bundle any number of assets together.

Asset files of the same MIME type can be bundled into one resource using resources.Concat which takes two arguments, a target path and a slice of resource objects.

``` bash
{{ $plugins := resources.Get "js/plugins.js" }}
{{ $global := resources.Get "js/global.js" }}
{{ $js := slice $plugins $global | resources.Concat "js/bundle.js" }}
```

## config

Hugo ships with a large number of configuration directives. The config directory is where those directives are stored as JSON, YAML, or TOML files. Every root setting object can stand as its own file and structured by environments. Projects with minimal settings and no need for environment awareness can use a single config.toml file at its root.

Many sites may need little to no configuration, but Hugo ships with a large number of configuration directives for more granular directions on how you want Hugo to build your website. Note: config directory is not created by default.

## content

В этой директории живет всё наполнение сайта (content). каждую директорию верхнего уровня Hugo считает **разделом**.

All content for your website will live inside this directory. Each _top-level_ folder in Hugo is considered a content section. For example, if your site has three main sections — `blog`, `articles`, and `tutorials` — you will have three directories at `content/blog`, `content/articles`, and `content/tutorials`. Hugo uses sections to assign default content types.



Страницы:
- главная - открывается при запуске (по умолчанию)
- страницы разделов - поддиректории **content**
    Статьи - "обычные страницы" это содержимое вышеуказанных директорий.

data
    This directory is used to store configuration files that can be used by Hugo when generating your website. You can write these files in YAML, JSON, or TOML format. In addition to the files you add to this folder, you can also create data templates that pull from dynamic content.

layouts
    Stores templates in the form of `.html` files that specify how views of your content will be rendered into a static website. Templates include list pages, your homepage, taxonomy templates, partials, single page templates, and more.

static
    Stores all the static content: images, CSS, JavaScript, etc. When Hugo builds your site, all assets inside your static directory are copied over as-is. A good example of using the static folder is for verifying site ownership on Google Search Console, where you want Hugo to copy over a complete HTML file without modifying its content.


static - Хранит весь статический контент: изображения, CSS, JavaScript и т. Д. Когда Hugo создает ваш сайт, все ресурсы в вашем статическом директорияе копируются как есть. Хороший пример использования статической папки - подтверждение права собственности на сайт в Google Search Console, где вы хотите, чтобы Hugo скопировал полный HTML-файл без изменения его содержимого.

### Создание (добавление) контента

Для создания статьи предназначена команда `Hugo`, c указанием пути к файлу и его имени. **Hugo** хранит весь контент в директории `/content`, поэтому путь к файлу должен вести только в эту директорию.

В директории `/content/articles` будет создан файл `my-first-article.md` с таким содержимым:

``` md
---
title: "My First Post"
date: 2020-02-16T08:47:11+01:00
draft: true
---
```

Все, что находится между `---`, является метаданными для статьи, **Hugo** считает это «вопросом первостепенной важности». Как уже отчечалось, формат по умолчанию - **.toml**, доступно: **.json** или **.yaml**.
``` bash
hugo new articles/my-first-article.md
```

См. [Информацию о toml](https://github.com/toml-lang/toml)

>Как что-то плохое. json/yaml/xml - вот это вот плохое, особенно yaml, и томл может их заменить везде, где конфиг надо править ручками. И это будет прекрасно.
>[*В чем суть TOML? - linux.org.ru*](https://www.linux.org.ru/forum/general/11368615)
