---
date: 2020-07-29T07:24:21+03:00
Lastmod: 2021-06-22T13:09:21+03:00
title: Подсветка синтаксиса
subtitle: "- в примерах исходного кода"
description: Подсветка синтаксиса в Hugo отличается скоростью, простой настройкой и большим набором обрабатываемых языков. По умолчанию подключена красивая и многим полюбившаяся темная тема «monokai»
summary: "Исходный код в ваших примерах - безупречен"
summaryImage: /images/highligth.png
draft: false
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: "Hugo Authors, wBuresh"
categories: ["Управление контентом"]
tags: [Hugo, Сode]
# categories: [content-management]
# tags: [hugo, templates, taxonomy]
toc: true
---

По материалам сайта Hugo [Syntax Highlighting](https://gohugo.io/content-management/syntax-highlighting/#list-of-chroma-highlighting-languages)

<i>Документация hugo</i>.

Для всех, кто пишет о своих или чьих-либо разработках с открытым исходным кодом, важно чтобы текст содержал не только скриншоты, но фрагменты исходного кода с простыми и понятными комментариями. Сейчас легко найти подходящие средства, позволяющие представить исходный код, с красивой подсветкой синтаксиса. Например весьма популярна среди специалистов [highlight.js](https://github.com/highlightjs/highlight.js), написанная на JavaScript. Она надежно работает и просто устанавливается. К стати, ее успешно применяют разработчики великолепных тем для Hugo: [**Hugo ReFresh**](https://themes.gohugo.io/hugo-refresh/), разработчик - ([Roberto Jordaney](https://rjordaney.is/)), [Docs](https://getdoks.org/), разработчик [Henk Verlinde](https://henkverlinde.com/) и многие другие  


Однако, Hugo поставляется с очень лаконичной, быстрой и легко настраиваемой подсветкой синтаксиса от [Chroma](https://github.com/alecthomas/chroma). **Chroma**, как и **Hugo**, написана на **Go**, активно развивается и совершенствуется.

По умолчанию, подсветка имеет следующую конфигурацию:

{{< highlight yaml "linenos=true,hl_lines=4 11,linenostart=27" >}}

# Highlighting Language - yaml
markup:
highlight:
codeFences: true
guessSyntax: false
hl_Lines: ""
lineNoStart: 1
lineNos: false
lineNumbersInTable: true
noClasses: true
style: monokai
tabWidth: 4
{{< /highlight >}}

То есть, включать в свои статьи примеры исходных кодов с подсветкой синтаксиса различных языков программирования, разметки, или просто структурированного текста пользователи могут сразу после установки **Hugo** с соответствующей темой.

Как видно из приведенного фрагмента параметров конфигурации, по умолчанию, предложена очень красивая и весьма популярная тема **monokai**. Это определено параметром `style:`, в нашем примере - строка 37 (с выделением).

Важно помнить, что для полной реализации возможностей и преимуществ Hugo Syntax Highlighting необходимо применять встроенный Hugo шорткод - `❴❴< highlight >❵❵`. Однако не лишне уделить должное внимание и базовым возможностям **Markdown**.

> Примечание:
>
> Для демонстрации примеров был взят, пожалуй, самый трудный для демонстрации язык `go-html-template`. Чтобы все получилось, пришлось фигурные скобки заменить символами unicode &#10100; и &#10101;. Если этого не сделать, то код просто сработает и показать пример не удастся, так как **Hugo** реагирует на содержимое {{ _внутри фигурных скобок_ }} . Вопреки ожиданиям, даже [шорткод](https://gohugo.io/content-management/shortcodes/) **highlight** не всегда помогает.

<!-- You can call out code or a command within a sentence with single backticks. The text within the backticks will not be formatted.

```markdown
Use `git status` to list all new or modified files that haven't yet been committed.
```
 -->


## Подсветка синтаксиса. Базовый Markdown

Некоторые пользователи могут ограничиться применением базовых возможностей Markdown. В настройках Hugo параметр `codeFences: true` включен по умолчанию (в нашем примере - строка 30 тоже выделена). Все просто. Достаточно одной табуляции или отступа в строках на четыре пробела и можно показать код или форматированный текст. Однако подсветки синтаксиса не будет. Чтобы она появилась нужно заключить код в три обратные кавычки (backquote, backtick) - &#96;&#96;&#96; и указать язык, синтаксис которого требуется подсветить. Это наглядно показано на простых примерах.

Язык в примере кода не указан

```
&#96;&#96;&#96;
❴
  "firstName": "Hugo",
  "lastName": "Chroma",
  "alias": "Highlight"
❵
&#96;&#96;&#96;
```

Код выводится корректно, но без подсветки синтаксиса.

```
{
  "firstName": "Hugo",
  "lastName": "Chroma",
  "alias": "Highlight"
}

 <!-- Линтер обычно выдает предупреждение: «MD040/fenced-code-language: Fenced code blocks should have a language specifiedmarkdownlintMD040» -->

```

При указании языка, в нашем примере - JSON:

```json
&#96;&#96;&#96;json
❴
  "firstName": "Hugo",
  "lastName": "Chroma",
  "alias": "Highlight"
❵
&#96;&#96;&#96;
```

Визуализированный вывод с подсветкой синтаксиса (по умолчанию - тема **monokai**) выглядит так:

```json
{
  "firstName": "Hugo",
  "lastName": "Chroma",
  "alias": "Highlight"
}
```

## Встроенный Hugo шорткод - `❴❴< highlight >❵❵`. Практика применения

Подсветка кода в Hugo работает это довольно просто. **Chroma** берет исходный код или другой структурированный текст и преобразует его в подсвечиваемый синтаксис HTML.

{{< highlight bash >}}
highlight INPUT LANG OPTIONS
{{< /highlight >}}

Применяя подсветку синтаксиса важно помнить, что:

1. [Встроенный шорткод](https://gohugo.io/content-management/shortcodes/) `❴❴< highlight >❵❵` обязательно должен быть закрыт - `❴❴< /highlight >❵❵`
2. Для правильной подсветки, необходимо явно указать демонстрируемый язык (или его alias - псевдоним).
3. Если содержимое не требует подсветки нужно указать **plaintext** (либо один из псевдонимов: _no-highlight, plain, text или txt_).

Кроме того, нелишне обратить внимание, что **highlight** не применяется для подсветки `JavaScript` на стороне клиента.

См. [краткий список]() часто цитируемых языков.

См. также [полный список](https://gohugo.io/content-management/syntax-highlighting/#list-of-chroma-highlighting-languages) языков (около двухсот), подсветку кода которых поддерживает [Chroma](https://github.com/alecthomas/chroma).

Итак, применяется шорткод довольно просто. Как это делается наглядно показано на следующем примере:

{{< highlight html >}}
<picture>

<source srcset="..." type="image/svg+xml">
<img src="..." class="img-fluid img-thumbnail" alt="...">
</picture>
{{< /highlight >}}

## Практика применения встроенного шорткода `❴❴< highlight >❵❵` на примерах

Преимущества применения встроенного шорткода `❴❴< highlight >❵❵` хорошо видны даже на первом нашем примере, посвященном [конфигурации подсветки Hugo по умолчанию](). Речь идет о возможности использовать параметры, позволяющие выводить подсвеченный код не только с учетом особенностей синтаксиса языка, но и с нумерацией строк, что облегчает комментирование демонстрируемого кода. Кроме того, для повышения наглядности некоторые строки и/или диапазоны строк можно подсветить. Это помогает быстро найти нужное, особенно при чтении больших фрагментов кода. А еще можно установить номер с которого будет начинаться нумерация строк в примере. Это очень нужно при демонстрации и комментировании фрагментов реальных исходных кодов.

### Параметры

Итак, шорткод `❴❴< highlight >❵❵` может применяться с параметрами, позволяющими:

1. Вывести номера строк - параметр **`linenos`**. Допустимые значения:
   - **`true`** и **`false`** - управление выводом нумерации строк;
   - **`table`** - форматирование блоков кода для копирования и вставки кода;
   - **`inline`** - для форматирования небольших, как правило, однострочных фрагментов кода.
1. Указать начальный номер отсчета - параметр **`linenostart=19`**. Отсчет строк начнется с указанного номера (в примере - строка 19).
1. Определить строки или диапазоны смежных строк для выделения **`hl_lines`**.

<!-- ## Highlight Shortcode -->

### Пример 1. `❴❴< highlight go-html-template >❵❵` - указан язык `go-html-template`

{{< highlight go-html-template >}}

<figure {{ with .Get "class" }}class="{{.}}"{{ end }}>
    {{ with .Get "link"}}<a href="{{.}}">{{ end }}
        <img src="{{ .Get "src" }}" {{ if or (.Get "alt") (.Get "caption") }}alt="{{ with .Get "alt"}}{{.}}{{else}}{{ .Get "caption" }}{{ end }}"{{ end }} />
    {{ if .Get "link"}}</a>{{ end }}
    {{ if or (or (.Get "title") (.Get "caption")) (.Get "attr")}}
    <figcaption>{{ if isset .Params "title" }}
        <h4>{{ .Get "title" }}</h4>{{ end }}
        {{ if or (.Get "caption") (.Get "attr")}}<p>
        {{ .Get "caption" }}
        {{ with .Get "attrlink"}}<a href="{{.}}"> {{ end }}
            {{ .Get "attr" }}
        {{ if .Get "attrlink"}}</a> {{ end }}
        </p> {{ end }}
    </figcaption>
    {{ end }}
</figure>
<!-- image -->
{{< / highlight >}}

Как видно, при правильном выборе и указании языка, корректно подсвечивается синтаксис языка разметки **html** и языка программирования **Go**.

### Пример 2. Подсветка кода с выводом нумерации строк

**Шорткод `❴❴< highlight go-html-template >❵❵` - с параметром `"linenos=true"`**

{{< highlight go-html-template "linenos=true" >}}

<figure {{ with .Get "class" }}class="{{.}}"{{ end }}>
    {{ with .Get "link"}}<a href="{{.}}">{{ end }}
        <img src="{{ .Get "src" }}" {{ if or (.Get "alt") (.Get "caption") }}alt="{{ with .Get "alt"}}{{.}}{{else}}{{ .Get "caption" }}{{ end }}"{{ end }} />
    {{ if .Get "link"}}</a>{{ end }}
    {{ if or (or (.Get "title") (.Get "caption")) (.Get "attr")}}
    <figcaption>{{ if isset .Params "title" }}
        <h4>{{ .Get "title" }}</h4>{{ end }}
        {{ if or (.Get "caption") (.Get "attr")}}<p>
        {{ .Get "caption" }}
        {{ with .Get "attrlink"}}<a href="{{.}}"> {{ end }}
            {{ .Get "attr" }}
        {{ if .Get "attrlink"}}</a> {{ end }}
        </p> {{ end }}
    </figcaption>
    {{ end }}
</figure>
{{< / highlight >}}

Наряду с подсветкой синтаксиса выведена нумерация строк.

<!-- ## Пример 3. Подсветка кода с выводом нумерации и выделением строк и диапазонов -->

## Configure Syntax Highlighter

Shortcode - `❴❴< highlight go-html-template >❵❵`; options - `"linenos=table,hl_lines=3 7 10-12,linenostart=10"`

{{< highlight go-html-template "linenos=table,hl_lines=3 7 10-12,linenostart=10" >}}

<figure {{ with .Get "class" }}class="{{.}}"{{ end }}>
    {{ with .Get "link"}}<a href="{{.}}">{{ end }}
        <img src="{{ .Get "src" }}" {{ if or (.Get "alt") (.Get "caption") }}alt="{{ with .Get "alt"}}{{.}}{{else}}{{ .Get "caption" }}{{ end }}"{{ end }} />
    {{ if .Get "link"}}</a>{{ end }}
    {{ if or (or (.Get "title") (.Get "caption")) (.Get "attr")}}
    <figcaption>{{ if isset .Params "title" }}
        <h4>{{ .Get "title" }}</h4>{{ end }}
        {{ if or (.Get "caption") (.Get "attr")}}<p>
        {{ .Get "caption" }}
        {{ with .Get "attrlink"}}<a href="{{.}}"> {{ end }}
            {{ .Get "attr" }}
        {{ if .Get "attrlink"}}</a> {{ end }}
        </p> {{ end }}
    </figcaption>
    {{ end }}
</figure>
{{< / highlight >}}

Наряду с подсветкой синтаксиса выведена нумерация строк. Начало нумерации - со строки 10. Строки 3 и 7, а также диапазон строк 10-12 - выделены, что позволяет обратить особое внимание при их описании.

> Примечание:
>
> Следует обратить внимание, что только [Goldmark](https://gohugo.io/getting-started/configuration-markup/#goldmark) поддерживает передаваемые атрибуты, такие как `hl_lines` и пр. Также важно, помнить что между параметрами при их перечислении (через запятую) пробелы НЕДОПУСТИМЫ!.

Для просмотра стилей, подготовлены эти галереи:

- [Short snippets](https://xyproto.github.io/splash/docs/all.html)
- [Long snippets](https://xyproto.github.io/splash/docs/longer/all.html)

## Простая и умная подсветка синтаксиса

Начиная с версии v0.60.0, в Hugo есть возможность подсветки кода упрощенным методом, без применения шорткода, но с добавлением, уже известных нам параметров: `{linenos=table,hl_lines=[1,"4-5"],linenostart=8}`. Подробнее См. [Highlighting in Code Fences](https://gohugo.io/content-management/syntax-highlighting/#highlighting-in-code-fences).


### Пример

После указания [синтаксиса языка]({{< ref "#ChroList" >}}), достаточно поместить

 Вот как это выглядит:

```html {linenos=table,hl_lines=[1,"4-5"],linenostart=2}
<!-- As a link -->
<nav class="navbar navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
  </div>
</nav>

<!-- As a heading -->
<nav class="navbar navbar-light bg-light">
  <div class="container-fluid">
    <span class="navbar-brand mb-0 h1">Navbar</span>
  </div>
</nav>
```

## Генерация стилей подсветки синтаксиса (css)

Generate Syntax Highlighter CSS

По умолчанию _Hugo-Refreshing_ подключена красивая и очень популярная темная тема подсветки синтаксиса «monokai». Для любителей светлых тонов подгружена и добавлена в файл refreshing.scss строка `// @import 'syntax-monokailight';` (предварительно закомментирована!) для импорта стилей светлой темы monokailight. Кроме того, в конфигурационном файле `config.yaml` темы **ReFreshing** - включен параметр `pygmentsUseClasses: true`.

{{< highlight scss "linenos=true,linenostart=5">}}
// SCSS - themes/hugo-refreshing/assets/style-rfg/refreshing.scss

@import 'syntax-monokai';
// @import 'syntax-monokailight';
{{< /highlight >}}

По желанию, пользователь может легко переключиться на на светлую тему подсветки синтаксиса. Для этого достаточно снять комментарий - `//` в строке 6 и закомментировать строку 5. После они должны иметь следующий вид:

{{< highlight scss "linenos=true,linenostart=5">}}
// SCSS - themes/hugo-refreshing/assets/style-rfg/refreshing.scss

// @import 'syntax-monokai';
@import 'syntax-monokailight';
{{< /highlight >}}

Помимо этого, пользователь имеет возможность выбрать любую другую подсветку:
abap; algol; algol_nu; api; arduino; autumn; borland; bw; colorful; dracula; emacs; friendly; fruity; github; igor; lovelace; manni; monokai; monokailight; murphy; native; paraiso-dark; paraiso-light; pastie; perldoc; pygments; rainbow_dash; rrt; solarized-dark; solarized-dark256; solarized-light; swapoff; tango; trac; vim; vs; xcode.

Для этого необходимо сформировать таблицу выбранного стиля. Для этого предусмотрена специальная команда Hugo:

{{< highlight bash >}}
hugo gen chromastyles --style=monokai > syntax.css
{{< /highlight >}}

Запустите `hugo gen chromastyles -h` для получения дополнительных опций. См. галерею доступных стилей [https://xyproto.github.io/splash/docs/](https://xyproto.github.io/splash/docs/).

При этом следует убедится, что в файле конфигурации config.yaml (config.toml и др.) есть параметр `pygmentsUseClasses: true`

## goldmark-highlighting

См. GitHub [goldmark-highlighting](https://github.com/yuin/goldmark-highlighting)

goldmark-highlighting это расширение для [goldmark](http://github.com/yuin/goldmark) - парсера языка Markdown, написанного на Go. goldmark-highlighting добавляет подсветку синтаксиса в выделенных (fenced) блоках кода. Как уже отмечалось,

Для подсветки синтаксиса goldmark-highlighting использует [chroma](https://github.com/alecthomas/chroma). A Markdown parser written in Go. Easy to extend, standards-compliant, well-structured.

## Список зыков, подсветка синтаксиса которых поддерживается {#ChroList}

List of Chroma Highlighting Languages

See [the full list of Chroma lexers and their aliases](https://gohugo.io/content-management/syntax-highlighting/#list-of-chroma-highlighting-languages) (which is the identifier used in the highlight template func or when doing highlighting in code fences):

|   № | Популярные         | Алиасы                                                                      |   № | Языки программирования | Алиасы                               |
| --: | ------------------ | --------------------------------------------------------------------------- | --: | ---------------------- | ------------------------------------ |
|     | _Без подсветки_    |                                                                             |     | _Часто цитируемые_     |
|  1. | **plaintext**      | no-highlight, plain, text, txt                                              | 13. | **Go**                 | go, golang                           |
|     | _Командная строка_ |                                                                             | 14. | **Go HTML Template**   | go-html-template                     |
|  2. | **Bash**           | bash, bashrc, ebui1ld, eclass, exheres-0, exlib, ksh, sh, shell, zsh, zshrc | 15. | **Go Text Template**   | go-text-template                     |
|     | _Стили_            |                                                                             | 16. | **Kotlin**             | kotlin, kt                           |
|  3. | **CSS**            | css                                                                         | 17. | **JavaScript**         | javascript, js, jsm                  |
|  4. | **SCSS**           | scss                                                                        | 18. | **Java**               | java                                 |
|  4. | **Sass**           | sass                                                                        | 19. | **PHP**                | inc, php, php3, php4, php5, php[345] |
|     | _Разметка_         |                                                                             | 20. | **Python**             | py, python, pyw, sage, sc, tac       |
|  6. | **HTML**           | htm, html, xhtml,xslt                                                       | 21. | **Python 3**           | py3, python3                         |
|  7. | **markdown**       | markdown, md, mkd                                                           | 22. | **react**              | jsx, react                           |
|  8. | **XML**            | rss, svg, wsdl, wsf, xml, xsd, xsl, xslt                                    | 23. | **vue**                | vue, vuejs                           |
|     | _Настройки_        |                                                                             | 24. | **C**                  | c, h, idc                            |
|  9. | **YAML**           | yaml, yml                                                                   | 25. | **CoffeeScript**       | coffee, coffee-script, coffeescript  |
| 10. | **TOML**           | toml                                                                        | 26. | **TypeScript**         | ts, tsx, typescript                  |
| 11. | **JSON**           | json                                                                        |     |                        |                                      |
| 12. | **INI**            | cfg, dosini, gitconfig, inf, ini                                            |     |                        |                                      |

<!-- [Configure Markup](https://gohugo.io/getting-started/configuration-markup/#configure-markup)
highlight:
    codeFences: true
    guessSyntax: false
    hl_Lines: ""
    lineNoStart: 1
    lineNos: false
    lineNumbersInTable: true
    noClasses: true
    style: monokai
    tabWidth: 4
  tableOfContents:
    endLevel: 3
    ordered: false
    startLevel: 2 -->

<!--

 -->
