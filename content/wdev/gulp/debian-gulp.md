---
title: Gulp для Debian
date: 2021-05-22T13:42:03+03:00
draft: false
description: "исходный код в ваших примерах - безупречен"
summary:  "Великолепные возможности Hugo удачно дополняются задачами Gulp в части подготовки и включения в проект стилей (SASS, SCSS, CSS), JS и изображений, а также их своевременного обновления"
summaryImage: /images/highligth.png
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories:
- webDev
tags:
  - Debian
  - Hugo
  - Gulp
---

## gulp из репозитории Debian

В репозитории Debian можно найти пакет gulp и ряд расширений, в том числе:

### Плагин gulp-newer

Плагин **[gulp-newer](https://github.com/tschaub/gulp-newer)** - for passing through only those source files that are newer than corresponding destination files | для прохождения только тех исходных файлов, которые новее, чем соответствующие файлы назначения.

Разработчик плагина Tim Schaub (спасибо ему) работу плагина показывает на примере **Using `newer` with 1:1 source:dest mappings**

> The default task in the example below sets up a watch that minifies images on changes. Piping the source files to `newer` before `imagemin` ensures that only those images that have changed are minified. The `newer` plugin is configured with the directory path for minified images.

В приведенном ниже примере задача - минимизировать измененные изображения. Передача исходных файлов в `newer` перед`imagemin` гарантирует, что минимизируются только те изображения, которые были изменены. Плагин `newer` настроен с указанием пути к директории для минимизированных изображений.

```js
var gulp = require('gulp');
var newer = require('gulp-newer');
var imagemin = require('gulp-imagemin');

var imgSrc = 'src/img/**';
var imgDest = 'build/img';

// Minify any new images
gulp.task('images', function() {

  // Add the newer pipe to pass through newer images only
  return gulp.src(imgSrc)
      .pipe(newer(imgDest))
      .pipe(imagemin())
      .pipe(gulp.dest(imgDest));

});

gulp.task('default', function() {
  gulp.watch(imgSrc, ['images']);
});
```

Кроме того, Tim Schaub приводит ещё пример: **Using newer with many:1 source:dest mappings**

> Plugins like gulp-concat take many source files and generate a single destination file. In this case, the newer stream will pass through all source files if any one of them is newer than the destination file. The newer plugin is configured with the destination file path.

Плагины, такие как `gulp-concat`, берут множество исходных файлов и генерируют один файл назначения. В этом случае отбираются толко исходные файлы, которые новее файлов назначения. В `newer` указан путь к файлу назначения.

```js
var gulp = require('gulp');
var newer = require('gulp-newer');
var concat = require('gulp-concat');

// Concatenate all if any are newer
gulp.task('concat', function() {

  // Add the newer pipe to pass through all sources if any are newer
  return gulp.src('lib/*.js')
      .pipe(newer('dist/all.js'))
      .pipe(concat('all.js'))
      .pipe(gulp.dest('dist'));

});
```

### Плагин gulp-rename

Плагин **[gulp-rename](https://github.com/hparra/gulp-rename)** - plugin to rename files easily

```js
var rename = require("gulp-rename");

// rename to a fixed value
gulp.src("./src/main/text/hello.txt")
  .pipe(rename("main/text/ciao/goodbye.md"))
  .pipe(gulp.dest("./dist")); // ./dist/main/text/ciao/goodbye.md

// rename via mutating function
gulp.src("./src/**/hello.txt")
  .pipe(rename(function (path) {
    // Updates the object in-place
    path.dirname += "/ciao";
    path.basename += "-goodbye";
    path.extname = ".md";
  }))
  .pipe(gulp.dest("./dist")); // ./dist/main/text/ciao/hello-goodbye.md

// rename via a map function
gulp.src("./src/**/hello.txt")
  .pipe(rename(function (path) {
    // Returns a completely new object, make sure you return all keys needed!
    return {
      dirname: path.dirname + "/ciao",
      basename: path.basename + "-goodbye",
      extname: ".md"
    };
  }))
  .pipe(gulp.dest("./dist")); // ./dist/main/text/ciao/hello-goodbye.md

// rename via a fixed object
gulp.src("./src/main/text/hello.txt", { base: process.cwd() })
  .pipe(rename({
    dirname: "main/text/ciao",
    basename: "aloha",
    prefix: "bonjour-",
    suffix: "-hola",
    extname: ".md"
  }))
  .pipe(gulp.dest("./dist")); // ./dist/main/text/ciao/bonjour-aloha-hola.md
```

Есть еще несколько `Gulp` пакетов в репозитории Debian, но пока они не требуются.
