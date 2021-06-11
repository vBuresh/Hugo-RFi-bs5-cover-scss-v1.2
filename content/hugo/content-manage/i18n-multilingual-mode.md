---
title: i18n многоязычный режим Hugo
date: 2019-11-05T15:26:32.000Z
draft: false
---

<!-- TOC -->

 - [i18n многоязычный режим Hugo](#i18n-%D0%BC%D0%BD%D0%BE%D0%B3%D0%BE%D1%8F%D0%B7%D1%8B%D1%87%D0%BD%D1%8B%D0%B9-%D1%80%D0%B5%D0%B6%D0%B8%D0%BC-hugo)

  - [i18n](#i18n)

<!-- /TOC -->

 Для увеличени посещаемости, а главное - для лучшего понимания информации посетителями сайта в Hugo есть возможность многоязычного представления контента, а также локализациий строк.

# Настройка многоязычного проета

Как настроить многоязычный проект Hugo и перевести контент подробно рссмотрено в документации.

- [Multilingual Mode](https://gohugo.io/content-management/multilingual)
- [Hugo Multilingual Part 1: Content translation](https://regisphilibert.com/blog/2018/08/hugo-multilingual-part-1-managing-content-translation/)
- [i18n](https://gohugo.io/functions/i18n/#readout)

# Конфигурирование языков

При осуществлении многоязычного проекта прежде всего нужно объявить Hugo о поддерживаемых языках. Например, в проекте три языка:

- Английский en
- Русский ru
- Старославянский cu

В конфигурационный файл Hugo необходмо добавить следующие параметры:

```yaml
# config.yaml
languages:
  en:
    languageName:  English
    weight:        1
  ru:
    languageName:  Russian
    weight:        2
  cu:
    languageName:  OldChurchSlavonic
    weight:        3
```

Теперь наши языки будут доступны с использованием `.Site.Languages` и отсортированы по весу `Weight` (чем ниже - первый). Язык по умолчанию - следует первым.

Любой пользовательский параметр будет применяться при вызове `.Site.Params` или `.Param` вместо параметра сайта по умолчанию. Поэтому никогда не придется следить за тем, какой параметр вызывать!

```yaml
# config.yaml
params:
  # description: Everything you need to know about the three languages.
  description: Основной язык сайта русский - Russian. Для поддержки текстов на ЦСЯ - OldChurchSlavonic. Для статей, документов и других оргигинальных материалов - English
  twitter_handle: 3Languages

languages:
  ru:
    languageName:  Russian
    weight:        1
  cu:
    languageName:  OldChurchSlavonic
    weight:        2
    description: Tous ce que vous avez toujours voulu savoir sur les trois langues.
    twitter_handle: 3Languages_france
  en:
    languageName:  English
    weight:        3
    description: Todo lo que necesitas saber sobre los tres idiomas.
    twitter_handle: 3Languages_espana
```

```go
<meta name="description" content="{{ .Param "description" }}">
<meta name="twitter:site" content="{{ .Param "twitter_handle" }}">
```

## Перевод страниц сайта

Для управления контентом на соответствующем языке Hugo предлагает два разных способа.

1. "По имени файла" - подразумевает включение языкового кода в файл содержимого следующим образом: `/content/about.fr.md`
2. "По языковой директории" - предплагает создание файла внутри определенной языковой директории: `/content/french/about.md`

### Управление переводами по имени файла

**Страница about.md и ее переводы.**

```
content
       ├── about.md
       ├── about.es.md
       └── about.fr.md
```

Hugo назначит французский язык для about.fr.md, а испанский - для about.es.md. Это понятно. А что же с about.md? Языковый код, будет присвоен в соответствии с параметором _default language_.

При отсутствии параметра `DefaultContentLanguage` в конфигурационном файле, язык по умолчанию всегда English. Например, если нужно, чтобы Hugo назначил Russian для about.md, мы следует сделать русский язык по умолчанию, добавив следующую строку:

```yaml
# config.yaml
  DefaultContentLanguage: ru
```

То есть, каждый из способов обеспечивает две вещи:

Каждой странице назначается язык. Каждая страница связана с соответствующими переводами.

```
# config.yaml
 DefaultContentLanguage: es
```

```yaml
languages:
  en:
    languageName: English
    weight: 1
    contentDir: content/english
  fr:
       languageName: Français
       weight: 2
       contentDir: content/french
  es:
    languageName: Spanish
    weight: 3
    contentDir: content/spanish
```

### Управление переводами по языковой директории

It is also possible to assign a different content directory to each of your languages. In order to use this system we would have to include a `contentDir` parameter to our languages configuration.

Для этого можно выделить соответствующие директории контента для каждого языка. Чтобы использовать эту систему, нам нужно включить параметр `contentDir` в конфигурацию языков.

```yaml
languages:
  en:
    : English
    weight: 1
    contentDir: content/english
  fr:
    languageName: Français
    weight: 2
    contentDir: content/french
  es:
    languageName: Spanish
    weight: 3
    contentDir: content/spanish
```

Параметр принимает относительный (либо абсолютный) путь к директориям проекта. Использование абсолютного пути означает, что директории содержимого не обязательно должны находиться внутри данного проекта, они могут находиться где угодно на вашем компьютере.

Директория **content** должна иметь следующую структуру:

      content
      ├── english
      │   └── about.md
      ├── french
      │   └── about.md
      └── spanish
          └── about.md

Теперь Hugo назначит язык каждой странице about, в зависимости от директории хранения контента.

Linking our pages 🔗

Translation linking is important.

We usually want to advertise the available translations of a page to our users be it in the form of a language switch menu or some SEO meta tags.

We’ve seen how Hugo assign a language to a particular page, but how will it be able to link pages as translations of each other?

For both systems, Hugo will look at the filename and its location relative to its content directory. So depending on your translation management system, we can check those linkings:


### Линковка страниц сайа 🔗

**Ссылка на перевод важна.**

Обычно мы хотим рекламировать доступные переводы страницы для наших пользователей, будь то в форме меню переключения языка или некоторых мета-тегов SEO.

Мы видели, как Хьюго назначает язык определенной странице, но как он сможет связывать страницы как переводы друг друга?

Для обеих систем Хьюго будет смотреть на имя файла и его местоположение относительно своего каталога содержимого. Поэтому в зависимости от вашей системы управления переводами мы можем проверить эти ссылки:


By Filename

```
1                          | 2                           | 3
-------------------------- | --------------------------- | --
`content/about.md`         | `content/about.fr.md`       | ✅
`content/about.fr.md`      | `content/about.es.md`       | ✅
`content/about/index.md`   | `content/about/index.fr.md` | ✅
`content/about.md`         | `content/a-propos.fr.md`    | 🚫
`content/company/about.md` | `content/about.fr.md`       | 🚫
```

By Directory

```
1                                  | 2                               | 3
---------------------------------- | ------------------------------- | --
`content/english/about.md`         | `content/french/about.md`       | ✅
`content/english/about/index.md`   | `content/french/about/index.md` | ✅
`content/english/about.md`         | `content/french/a-propos.md`    | 🚫
`content/english/company/about.md` | `content/english/about.md`      | 🚫
```


Note that you can force a linking even if default linking factors don’t match.
All you’d have to do is add to your pages a translationKey Front Matter param which share the same value.

Следует обратить внимание, что можно принудительно прилинковать, даже если параметры линковки по умолчанию не совпадают.
Все, что вам нужно сделать, это добавить на соответствующие страницы параметр `translationKey` с  одинаковым значением в параметрах Front Matter param, в начале страниц контента

``` md
<!-- From all three pages: about.md, a-propos.fr.md, acerda.es.md -->
---
translationKey: about
---
```

Теперь, даже если имена не совпадают, Hugo с легко свяжет эти страницы.

### Использование связанных переводов в шаблоне.

Чтобы использовать ссылку в шаблоне, нужно помнить, что Hugo хранит связанные переводы в двух переменных страницы:

- `.Translations` - связанные страницы.
- `.AllTranslations` - связанные страницы, включая текущую.

The collections are sorted by language Weight as defined in our configuration file.

So in order to build our alternate meta tags, we would just add this in our <head>:

``` go
  {{ if .IsTranslated }}
  	{{ range .Translations }}
  	<link rel="alternate" hreflang="{{ .Language.Lang }}" href="{{ .Permalink }}" title="{{ .Language.LanguageName }}">
  	{{ end }}
  {{ end }}
```



# i18n многоязычный режим Hugo

[Multilingual Mode](https://gohugo.io/content-management/multilingual)

## i18n

[i18n](https://gohugo.io/functions/i18n/#readout)

Translates a piece of content based on your i18n configuration files.

Syntax

> i18n KEY

> T KEY

This translates a piece of content based on your `i18n/en-US.yaml` (and similar) files. You can use the go-i18n tools to manage your translations. The translations can exist in both the theme and at the root of your repository.

``` go
  {{ i18n "translation_id" }}
```

> T is an alias to i18n. E.g. 2{ T "translation_id" }2.

## Menus

You can define your menus for each language independently. Creating multilingual menus works just like creating regular menus, except they’re defined in language-specific blocks in the configuration file:
Вы можете определить свои меню для каждого языка независимо. Создание многоязычных меню работает так же, как создание обычных меню, за исключением того, что они определены в языковых блоках в файле конфигурации:


content/warea
``` yaml
defaultContentLanguage = "en"

[languages.en]
weight = 0
languageName = "English"

[[languages.en.menu.main]]
url    = "/"
name   = "Home"
weight = 0


[languages.de]
weight = 10
languageName = "Deutsch"

[[languages.de.menu.main]]
url    = "/"
name   = "Startseite"
weight = 0
```
The rendering of the main navigation works as usual. .Site.Menus will just contain the menu in the current language. Note that absLangURL below will link to the correct locale of your website. Without it, menu entries in all languages would link to the English version, since it’s the default content language that resides in the root directory.
Рендеринг основной навигации работает как обычно. `.Site.Menus` будет просто содержать меню на текущем языке. Обратите внимание, что `absLangURL` ниже будет ссылаться на правильную локализацию вашего сайта. Без этого пункты меню на всех языках будут ссылаться на английскую версию, поскольку это язык контента по умолчанию, который находится в корневом каталоге.

```go
<ul>
    {{- $currentPage := . -}}
    {{ range .Site.Menus.main -}}
    <li class="{{ if $currentPage.IsMenuCurrent "main" . }}active{{ end }}">
        <a href="{{ .URL | absLangURL }}">{{ .Name }}</a>
    </li>
    {{- end }}
</ul>
```
