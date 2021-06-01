# Тема ReFreshing-bs5-cover для Hugo

На сайте Bootstrap даются [примеры сайтов](https://getbootstrap.com/docs/5.0/examples/), разработанных командой Bootstrap. Они предназначены для оказания помощи пользователям быстро начать свой проект - от использования частей фреймворка до настраиваемых компонентов `partials` и `layouts`, на основе любого образца.

## Шаблон "Cover"

> Quickly get a project started with any of our examples ranging from using parts of the framework to custom components and layouts.

Среди примеров по-своему интересен одностраничный шаблон **Cover**, предлагаемый для создания простых и красивых домашних страниц.

> A one-page template for building simple and beautiful home pages

Он отличается, прежде всего, простотой и лаконичностью (без аскетизма), компактностью, гармоничностью и прочими достоинствами.

## Практика применения шаблона в Hugo

Исходники проекта [размещены на GitHub](https://github.com/vBuresh/Hugo-RFi-bs5-cover). Нужно "форкнуть" проект и найти его в своем репозитории GitHub. Затем, переименовать его, присвоив имя Hugo-RFm-bs5-cover. После этого - клонировать проект в рабочую директорию: `./atom-sites/`

Исходники примера "Cover" - в директории `exampleSite/examples_bs5-cover`. Здесь же находится и файл `cover.html`. Полный путь к нему: `/home/w/vdev/atom-sites/_RFi-cover/exampleSite/examples_bs5-cover/cover.html`. Это полный действующий автономный пример "Cover" (использует интернет-ресурсы, необходимо интернет-подключение!).

Исходный код файла содержит комментарии, которые помогут выделить фрагменты, для помещения в директорию `layouts`:

1.  layouts/default/baseof.html
2.  layouts/partials/head.html
3.  layouts/partials/header.html
4.  layouts/partials/footer.html
5.  layouts/index.html
6.  layouts/default/single.html

### первый этап

На первом этапе: - содержимое выбранных фрагментов файла `cover.html` поместить в соответствующие файлы директории `layouts` (в режиме "как есть"):

1.  default/baseof.html (2/5, 4/51)
2.  partials/head.html
3.  partials/header.html
4.  partials/footer.html
5.  layouts/index.html
6.  default/single.html

После этого провести сборку командой `hugo server`.

Цель - получить такой же внешний вид главной страницы, как на образце.

По выполнении заданий первого этапа следует провести тщательное тестирование. Затем нужно "закоммитить" каждое изменение (stage, commit to muster) и "залить" в удаленный репозиторий GitHub (Push).

### второй этап

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
