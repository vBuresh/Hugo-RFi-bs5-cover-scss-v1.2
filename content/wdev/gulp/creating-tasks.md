---
title: Gulp-задачи
# subtitle: continuer of the title in a two words
date: 2021-05-24T11:34:39+03:00
Lastmod: 2021-05-24T11:34:39+03:00
draft: false
# description: "- дополнение к заголовку (подзаголовок)"
# summary: краткое изложение - зачем читать сие
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories:
  - "webDev"
tags:
  - Gulp
---

    **Источники:**

- [Creating Tasks](https://gulpjs.com/docs/en/getting-started/creating-tasks)
- [Репозиторий gulp на Github](https://github.com/wearefractal/gulp).
- [NPM](https://www.npmjs.com/search?q=keywords:gulpplugin)
- Википедия: [Gulp](https://ru.wikipedia.org/wiki/Gulp)
- [Gulp — как глоток свежего воздуха после Grunt](https://        frontender.info/no-need-to-grunt-take-a-gulp-of-fresh-air/)

В среде веб-разработчиков **Gulp** (англ. «глоток» [/gʌlp/, /галп/]) известен как таск-менеджер. Да просто «задачник» по-нашему. Являясь вполне удачным ответвлением от проекта **Grunt** «задачник» Gulp сохранил все лучшие возможности своего предшественника, связанные с автоматизацией рутинных процессов таких как минификация, тестирование, объединение и(или) переименование файлов, удаления директорий и(или) их содержимого и пр.). Кроме того, в Gulp усовершенствована система сборки. То есть, помимо запуска задач, можно: копировать файлы, компилировать и развёртывать проект в новом окружении и т.д..

Gulp написан на языке программирования **JavaScript**. Все задачи «готовятся к запуску» в файле `gulpfile.js` (галп-файл). Они пишутся кодом JavaScript (а не в стиле конфигурационного файла, как в **Grunt**). Важно подчеркнуть, что разработчикам удалось реализовать ряд интересных и востребованных решений соотвeтствующих требованиям концепции потоковой передачи данных. [Подробнее о концепции...](https://github.com/substack/stream-handbook)

Прежде чем приступть к рассмотрению Gulp-задач, следует поговорить о плагинах, предназначенных для расширения функциональности. При этом важно понять, что ключевая мысль Gulp в том, что каждый плагин должен выполнять _только одно_ простое действие. А Gulp всего лишь соединяет и организует эти действия в задачи. Интересно отметить, что на момент написания этой статьи [в менеджере пакетов NPM](https://www.npmjs.com/search?q=keywords:gulpplugin), входящем в состав Node.js, доступно **4102** плагина для Gulp.

Итак, взаимодействия между компонентами программы реализуется через оператор `.pipe()`, выполняя по одной задаче за раз. При этом исходные файлы не затрагиваются, до конца процедуры, что обеспечивает свободную комбинацию плагинов в любой последовательности и количестве.

Их запуск осуществляется в терминале (командной строке)..



Each gulp task is an asynchronous JavaScript function - a function that accepts an error-first callback or returns a stream, promise, event emitter, child process, or observable (more on that later). Due to some platform limitations, synchronous tasks aren't supported, though there is a pretty nifty alternative.
Each gulp task is an asynchronous JavaScript function - a function that accepts an error-first callback or returns a stream, promise, event emitter, child process, or observable (more on that later). Due to some platform limitations, synchronous tasks aren't supported, though there is a pretty nifty alternative.



## Exporting

Типы задач:

-   **Public** tasks are exported from your gulpfile, which allows them to be run by the `gulp` command.
    - задачи экспортируются из вашего gulpfile, что позволяет запускать их с помощью команды `gulp`.
-   **Private** tasks are made to be used internally, usually used as part of `series()` or `parallel()` composition.
    - задачи предназначены для внутреннего использования, обычно как часть композиции `series()` или `parallel()`.

A private task looks and acts like any other task, but an end-user can't ever execute it independently. To register a task publicly, export it from your gulpfile.

Частная задача выглядит и действует как любая другая задача, но конечный пользователь никогда не сможет выполнить ее независимо. Чтобы публично зарегистрировать задачу, экспортируйте ее из своего файла `gulpfile`.

```js
const { series } = require('gulp');

// The `clean` function is not exported so it can be considered a private task.
// It can still be used within the `series()` composition.
function clean(cb) {
  // body omitted
  cb();
}

// The `build` function is exported so it is public and can be run with the `gulp` command.
// It can also be used within the `series()` composition.
function build(cb) {
  // body omitted
  cb();
}

exports.build = build;
exports.default = series(clean, build);
```
