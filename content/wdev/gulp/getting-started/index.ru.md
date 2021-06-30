---
date: 2021-06-29T10:37:52+03:00
Lastmod: 2021-06-29T10:37:52+03:00
title: Getting Started
subtitle: Getting Started
description: Gulp is a toolkit that helps you automate painful or time-consuming tasks in your development workflow.
summary: three-line summary of the article.
draft: false
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [Веб-разработка]
# categories: ['Web development']
tags: [Gulp]
toc: true
---


- Автоматизация - помогает автоматизировать рутинные или трудоемкие задачи в процессе разработки.
- Независимость от платформы - Gulp легко встраивается во все основные IDE. Его используют с PHP, .NET, Node.js, Java и другими платформами.
- Сильная экосистема - используйте модули npm, чтобы делать все, что захотите + более 3000 тщательно отобранных плагинов для потокового преобразования файлов.
- Простой - Gulp легок и прост в освоении и использовании благодаря минимальной площади API.

<!--
- Automation - gulp is a toolkit that helps you automate painful or time-consuming tasks in your development workflow.
- Platform-agnostic - Integrations are built into all major IDEs and people are using gulp with PHP, .NET, Node.js, Java, and other platforms.
- Strong Ecosystem - Use npm modules to do anything you want + over 3000 curated plugins for streaming file transformations.
- Simple - By providing only a minimal API surface, gulp is easy to learn and simple to use.
-->


## Быстрый старт - Руководство
<!-- ## Check out the Getting Started guide -->

1. [quick-start](https://gulpjs.com/docs/en/getting-started/quick-start)
2. [javascript-and-gulpfiles](https://gulpjs.com/docs/en/getting-started/javascript-and-gulpfiles)
3. [creating-tasks](https://gulpjs.com/docs/en/getting-started/creating-tasks)
4. [async-completion](https://gulpjs.com/docs/en/getting-started/async-completion)
5. [working-with-files](https://gulpjs.com/docs/en/getting-started/working-with-files)
6. [explaining-globs](https://gulpjs.com/docs/en/getting-started/explaining-globs)
7. [using-plugins](https://gulpjs.com/docs/en/getting-started/using-plugins)
8. [watching-files](https://gulpjs.com/docs/en/getting-started/watching-files)

## Sample gulpfile.js

``` js {linenos=table,hl_lines=[10,"27-31"],linenostart=1}
var gulp = require('gulp');
var less = require('gulp-less');
var babel = require('gulp-babel');
var concat = require('gulp-concat');
var uglify = require('gulp-uglify');
var rename = require('gulp-rename');
var cleanCSS = require('gulp-clean-css');
var del = require('del');

var paths = {
  styles: {
    src: 'src/styles/**/*.less',
    dest: 'assets/styles/'
  },
  scripts: {
    src: 'src/scripts/**/*.js',
    dest: 'assets/scripts/'
  }
};

/* Not all tasks need to use streams,
 * a gulpfile is just another node program
 * and you can use all packages available on
 * npm, but it must return either a Promise,
 * a Stream or take a callback and call it */

function clean() {
  // You can use multiple globbing patterns as you would with `gulp.src`,
  // for example if you are using del 2.0 or above, return its promise
  return del([ 'assets' ]);
}

/*
 * Define our tasks using plain functions
 */
function styles() {
  return gulp.src(paths.styles.src)
    .pipe(less())
    .pipe(cleanCSS())
    // pass in options to the stream
    .pipe(rename({
      basename: 'main',
      suffix: '.min'
    }))
    .pipe(gulp.dest(paths.styles.dest));
}

function scripts() {
  return gulp.src(paths.scripts.src, { sourcemaps: true })
    .pipe(babel())
    .pipe(uglify())
    .pipe(concat('main.min.js'))
    .pipe(gulp.dest(paths.scripts.dest));
}

function watch() {
  gulp.watch(paths.scripts.src, scripts);
  gulp.watch(paths.styles.src, styles);
}

/*
 * Specify if tasks run in series or parallel using `gulp.series` and `gulp.parallel`
 */
var build = gulp.series(clean, gulp.parallel(styles, scripts));

/*
 * You can use CommonJS `exports` module notation to declare tasks
 */
exports.clean = clean;
exports.styles = styles;
exports.scripts = scripts;
exports.watch = watch;
exports.build = build;
/*
 * Define default task that can be called by just running `gulp` from cli
 */
exports.default = build;
```
