---
title: 'Spell Check'
subtitle: '- орфография в Atom'
date: 2020-03-04T10:43:01+03:00
Lastmod: 2021-06-22T11:29:01+03:00
description: 'В текстовом редакторе Atom проверку орфографии по умолчанию обеспечивает плагин Spell Check. Он входит в состав ядра Atom. Найденные при проверке неизвестные слова отмечаются подчеркиванием. Ошибку легко исправить или заменить всё слово, выбрав правильный вариант из предложенного списка. Также можно добавить в словарь новое известное слово. Кроме того, пользователи могут подключать словари разных языков и редактировать список проверяемых языков.'
summary: Проверка орфографии в текстовом редакторе Atom.
draft: false
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [веб-разработка]
tags: ['Atom', 'проверка орфографии', 'письмо']
# categories: ['web development']
# tags: ['Atom', spell-check]
toc: true
---

Для проверки орфографии в текстовом редакторе Atom предусмотрены следующие пакеты:

-   [spell-check](#spellCheck)
-   [linter-spell](#linterSpell)

Эти пакеты заметно отличаются, и имеют свои достоинства и недостатки. При этом они не могут «жить вместе. Каждый требует отключения своего «альтернативного собрата», если он был ранее подключен.

## spell-check {#spellCheck}

Пакет входит в ядро Atom. На 13 июня 2021 года имеет почти полмиллиона установок: 401 237.

На странице GitHub [Spell Check package](https://github.com/atom/spell-check) разработчики скромно заявляют, что пакет:

spell-check
: Highlights misspelled words and shows possible corrections.

spell-check
: Выделяет слова с ошибками и показывает возможные исправления

### Применение

При включенной проверке, слова с ошибкой выделяются красной линией. Чтобы вызвать список слов, предлагаемых вместо ошибочного нужно подвести курсор к отмеченному слову воспользоваться комбинацией клавиш:

- в **Mac**                 : `cmd-shift-:`
- в **Windows** и **Linux** : `ctrl-shift-:`

### Языки для проверки

Все просто. Однако сложности могут встретиться при подключении словарей для двух языков. Например русского и английского. Для этого в настройках следует указать: `en-US, ru-RU`. [Подробнее...](https://github.com/atom/spell-check#changing-the-dictionary)

### Проверка установленных словарей

Для **hunspell**

Получить список установленных словарей можно в терминале, командой: `/usr/bin/hunspell -D`.

Получим результат (Debian-11, пятница, 11 июня 2021 г., 11:51):

{{< highlight bash>}}
w@deb-del:~$ /usr/bin/hunspell -D
SEARCH PATH:
.::/usr/share/hunspell:/usr/share/myspell:/usr/share/myspell/dicts:/Library/Spelling:/home/w/.openoffice.org/3/user/wordbook:/home/w/.openoffice.org2/user/wordbook:/home/w/.openoffice.org2.0/user/wordbook:/home/w/Library/Spelling:/opt/openoffice.org/basis3.0/share/dict/ooo:/usr/lib/openoffice.org/basis3.0/share/dict/ooo:/opt/openoffice.org2.4/share/dict/ooo:/usr/lib/openoffice.org2.4/share/dict/ooo:/opt/openoffice.org2.3/share/dict/ooo:/usr/lib/openoffice.org2.3/share/dict/ooo:/opt/openoffice.org2.2/share/dict/ooo:/usr/lib/openoffice.org2.2/share/dict/ooo:/opt/openoffice.org2.1/share/dict/ooo:/usr/lib/openoffice.org2.1/share/dict/ooo:/opt/openoffice.org2.0/share/dict/ooo:/usr/lib/openoffice.org2.0/share/dict/ooo
AVAILABLE DICTIONARIES (path is not mandatory for -d option):
/usr/share/hunspell/en_US
/usr/share/hunspell/ru_RU
/usr/share/hunspell/ru_petr1708
/usr/share/hunspell/cu
{{< /highlight >}}

Если в списке нужных словарей не окажется, их можно установить, следуя рекомендациям разработчиков [Подробнее...](https://github.com/atom/spell-check#missing-languages)

Если все подключено правильно, следует еще раз обратить внимание на настройки:
`ctrl-,` » Packages » Core Packages » Spell Check » Settins » **Grammars**

{{< figure src="/images/spell-check-settings.png" width="100%" >}}

Приступая к работе, важно убедиться, что язык, на котором будет написан документ, есть в списке проверяемых.

В [руководстве явно указано](https://github.com/atom/spell-check), что по умолчанию проверка орфографии включена только для:

| Files               | Scopes                         |
| :-------------------|:-------------------------------|
| Plain Text          | text.plain                    |
| GitHub Markdown     | source.gfm                     |
| Git Commit Message  | text.git-commit                |
| AsciiDoc            | source.asciidoc                |
| reStructuredText    | source.rst, text.restructuredtext |


То есть, "машинным" языком  определено:

``` bash
source.asciidoc, source.gfm, text.git-commit,
text.plain, text.plain.null-grammar,
source.rst, text.restructuredtext
```

См. также [Writing in Atom/Spell Checking](https://flight-manual.atom.io/using-atom/sections/writing-in-atom/#spell-checking)

Если в работе применяются другие языки, например HTML, Markdown (не GFM) и пр., то их нужно добавить в настройках (поле **Grammars**).

## Имя языковой зоны

Определение имени языковой зоны (language's scope)
Finding a Language's Scope Name

[Finding a Language's Scope Name](https://flight-manual.atom.io/using-atom/sections/basic-customization/#finding-a-languages-scope-name)

overrides, you'll need to know the scope name for the language. We've already done this for finding a scope for writing a snippet in Snippet Format, but we can quickly cover it again.

The scope name is shown in the settings view for each language. Click on "Packages" in the navigation on the left, search for the language of your choice, select it, and you should see the scope name under the language name heading:

![the language name heading](https://flight-manual.atom.io/using-atom/images/python-grammar.png)

Кроме того "языковая зона" (the scope name for the language), - определяется командой: `Editor: Log Cursor Scope`, выполняемой в консоли: `Ctrl + Shift + P`. По мере ввода команды, выводится список, соответствующий введенной части команды. При появлении -`Editor: Log Cursor Scope` и выборе этой позиции, - будет выведено уведомление со списком используемых типов документа.

{{< note >}}
<p>В списке отражены только те типы документов, которые соответствуют "области действия курсора", а не всему документу. При этом учитываются кавычки и их тип (двойные или одиночные), а также, комментарии и пр.</p>
{{< /note >}}

HTML

{{< figure src="/images/logcursorscope_html.png" width="100%" caption="HTML: курсор в теге `<p>`" class="text-muted" >}}

При смене области действия курсора, например, при перемещении его в закомментированный фрагмент `<!-- вот | так -->`

{{< figure src="/images/logcursorscope_html-comment.png" width="100%" caption="HTML: курсор в `<!-- комментарии -->`" class="text-muted" >}}

Таким образом, чтобы орфография проверялась во всем HTML документе, включая закомментированные фрагменты, нужно в поле **Grammar** добавить следующее:

```
text.html.basic,

source.html,
comment.block.html,
```

GFM

Это язык включен в ядро Atom "как родной". См. настройки пакета: Packages  »  Language Gfm.

{{< figure src="/images/logcursorscope_gfm.png" width="100%" caption="GFM: курсор - в абзаце документа GitHub Markdown" >}}

Однако, если установить курсор в область `front-matter`, то определится следующее:

{{< figure src="/images/logcursorscope_gfm-front.png" width="100%" caption="GFM: курсор - в зоне `front-matter` GitHub Markdown" >}}

На рисунке видно, что в документе MD `front-matter` - на языке YAML, причем текст в области курсора - в одинарных кавычках `string.quoted.single.yaml`.

Если кавычки заменить на двойные, то строка сообщения будет такой: `string.quoted.double.yaml`. А если из совсем убрать, - то последняя строка изменится: `string.unquoted.yaml`. или

Таким образом, чтобы орфография проверялась во всем GFM документе, включая зону `front-matter` (с любыми кавычками и без них), нужно в поле **Grammar** добавить следующее (через запятую):

```
front-matter.yaml.gfm,
string.unquoted.yaml,
string.quoted.single.yaml,
string.quoted.double.yaml,
```

YAML - формат конфигурационных файлов. Расширенная версия распространенного формата JSON.

[YAML Ain’t Markup Language (YAML™) Version 1.2](https://yaml.org/spec/1.2/spec.html)

См. также: fat32elena [Yaml vs. Json — что круче?](https://habr.com/ru/company/rambler_and_co/blog/525498/) 17.11.2020

{{< figure src="/images/logcursorscope_yaml.png" width="100%" caption="YAML: курсор - в файле конфигурации config.yaml." >}}

Для проверки орфографии в файлах конфигурации YAML, в том числе в директориях i18n и data, нужно подключить только `source.yaml`, так как для проверки `front-matter` уже рекомендовалось подключить `string.unquoted.yaml, string.quoted.single.yaml, string.quoted.double.yaml,`

Таким образом, имеем по умолчанию:

```
source.asciidoc, source.gfm, text.git-commit, text.plain, text.plain.null-grammar, source.rst, text.restructuredtext
```

Общий список к добавлению (по `Log Cursor Scope`)

```
text.md, source.yaml, front-matter.yaml.gfm,
string.unquoted.yaml, string.quoted.single.yaml,
string.quoted.double.yaml,
```

надо добавить:

```
text.html.basic, source.yaml, text.html.hugo, text.xml.svg,
```

В итоге имеем:

```
text.html.basic, source.yaml, text.html.hugo, text.xml.svg, source.asciidoc, source.gfm, text.git-commit, text.plain, text.plain.null-grammar, source.rst, text.restructuredtext
```
и еще:

`css, css.erb, sass, sass.erb, source.js, source.json`

Потому что

| Пакет Atom    | Языковая зона  | List         |
| :------------ | :------------- |:------------:|
| language-gfm  | source.gfm     | core default |
| language-git  | text.git-commit| core default |
| language-text | text.plain     | core default |
| language-html | text.html.basic| core add     |
| language-yaml | source.yaml    | core add     |
| language-hugo | text.html.hugo | repo add     |
| language-svg  | text.xml.svg   | repo add     |

<!-- text.xml.svg -->

<!--

HUGO
{{< figure src="/images/LogCursorScope_HUGO.png" width="100%" caption="Scopes at Cursor - HUGO" >}}

``` bash
text.html.hugo,
punctuation.section.embedded.end.gotemplate,
```

- Markdown

```
text.md
fenced.code.md
source.embedded.shell
```

```
text.md, code.raw.markup.md,

```
- SVG

``` bash
text.xml.svg

``` -->



### Плагины

Заслушивает упоминания плагин **spell-check-urls**, который разработал опытный программист и активный участник сообщества Атом [Dylan R. E. Moonfire (dmoonfire)](https://github.com/dmoonfire).

This is a small spell-check plugin that marks various URLS as correct so they don't show up as spelling errors.

To use, just add the package in Atom and it will automatically hook up to spell-check.

There is no configuration.

### Предложения

Сейчас все хранится в одном файле общих настроек Atom `config.cson` /spell-check (linter-spell - там же). Нужно

### сделать пользовательский словарь

#### Где сейчас отражаются

{{< figure src="/images/spell-checkKnownWords.png"  width="100%" class="text-muted h4" caption="Известные слова" alt="spell-check" >}}

#### Где хранятся

{{< figure src="/images/spell-check-config_cson.png" class="text-muted h4" caption="Известные слова" alt="spell-check" >}}

Предложение сделать файл .spellcheckusersdic


Related to #365, spell-check's "Add to known words" option will save all these words, regardless of the current locale, somewhere — and the user has access to this flat list in spell-check's settings. But if you work with multiple languages, it would be far better (and in sync with hunspell practices) to add each exception to the personal dictionary for the given language.

Is this something that could be achieved? I would be most grateful for any pointers.

### ©b^ Предложение - spell-check Known Words config.cson

Так в настройках spell-check Known Words:



{{< figure src="/images/spell-checkKnownWords.png" width="100%" caption="Рис. 4. настройка spell-check / Known Words">}}

## linter-spell {#linterSpell}

Этот пакет разработан командой AtomLinter. Него около 100 000 установок: 91 480 (на 11 июня 2021).

Исходники пакета размещены на GitHub - [linter-spell](https://github.com/AtomLinter/linter-spell) в подзаголовочном тексте, отмечается, что пакет:

linter-spell
: Multilingual grammar-specific spell checking using Ispell-interface such as Aspell or Hunspell.

linter-spell
: Многоязычная грамматическая проверка орфографии с использованием интерфейса Ispell, такого как Aspell или Hunspell

### Особенности linter-spell

В отличии от **spell-check**, проверку орфографии **linter-spell** выполняет при сохранении документа с обнаруженными ошибками. Слова с ошибками и неизвестные слова помечаются  линтером подчеркиванием желтыми линиями. Орфографические ошибки можно исправить или добавить в личный словарь, либо в словарь языка с помощью базового пакета [intentions](https://atom.io/packages/intentions). Вызов - комбинацией клавиш:

-   в OSX              : ctrl + enter
-   в Linux и Windows  : alt + enter

Grammar and Dictionary Providers

Spell checking plain text, Markdown, or AsciiDoc documents is included in the package. To spell check other document types use a linter-spell-grammar provider. To use additional dictionaries use linter-spell-dictionary provider. Current providers are listed in the table below (D=Dictionary, G=Grammar, D/G=Dictionary/Grammar).

### Грамматика и словари

Проверка орфографии в виде обычного текста (plain text), документов Markdown или AsciiDoc включена в пакет по умолчанию. Для проверки орфографии других форматов применяются словари других поставщиков. Все они перечислены в таблице с указанием назначения, пакета и зависимостей, а также гиперссылок на ресурсы каждого разработчика. [Подробнее...](https://github.com/AtomLinter/linter-spell#grammar-and-dictionary-providers)

Кроме того, приведены подробные примеры создания новых [словарей](https://github.com/AtomLinter/linter-spell#create-new-dictionary-providers) и новых [грамматик](https://github.com/AtomLinter/linter-spell#creating-new-grammar-providers)

Таким образом, Атом обеспечивает пользователей достаточно надежными инструментами проверки орфографии, которые очень хорошо дополняют друг друга, несмотря на отсутствие возможности совместной работы. Но для этого есть возможность быстрого отключения и включения установленных пакетов.

Связанный с # 365, опция проверки орфографии «Добавить к известным словам» сохранит все эти слова, независимо от текущей локали, где-то - и у пользователя есть доступ к этому плоскому списку в настройках проверки орфографии. Но если вы работаете с несколькими языками, было бы намного лучше (и синхронно с практикой hunspell) добавлять каждое исключение в личный словарь для данного языка.

[На вопрос соотечественника](https://github.com/AtomLinter/linter-spell/issues/81) ответил так:

It works well on my Debian 11 with  settings like this:

{{< figure src="/images/linter-spell-settins.png" caption="" attr="" attrlink="" >}}

For more information on connecting dictionaries on Arch Linux, see [atom / spellcheck README.md ] (https://github.com/atom/spell-check#arch-linux). The setting is similar to the linter-spell.
