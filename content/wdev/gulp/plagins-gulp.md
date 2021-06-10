---
title: "Gulp плагины"
date: 2021-05-22T13:46:58+03:00
Lastmod: 2021-05-26T12:17:21+03
draft: false
description: каждый плагин выполняет одно простое действие
summary: Gulp соединяет и организует действия каждого плагина в задачи
# summaryImage: /images/highligth.png
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
toc: true
categories:
- webDev
tags:
  - Gulp
---

## Gulp плагины для текуших задач

Что уже установлено

-   "gulp": "^4.0.1",
-   "gulp-favicons": "^3.0.0",
-   "gulp-image": "^4.0.0",
-   "gulp-size": "^3.0.0",
-   "gulp-svgstore": "^7.0.1"

`Gulp`

### gulp-favicons

Favicon (сокр. от английского FAVorite ICON — «значок для избранного») — значок веб-сайта или веб-страницы. Это иконка, чаще всего с логотипом компании либо с изображением первых букв названия сайта.

[gulp-favicons](https://github.com/rejas/gulp-favicons)

#### Пример задачи gulp-favicons

```js
var favicons = require('gulp-favicons');

gulp
  .src('./favicon.png')
  .pipe(
    favicons({
      appName: 'My App',
      appShortName: 'App',
      appDescription: 'This is my application',
      developerName: 'Hayden Bleasel',
      developerURL: 'http://haydenbleasel.com/',
      background: '#020307',
      path: 'favicons/',
      url: 'http://haydenbleasel.com/',
      display: 'standalone',
      orientation: 'portrait',
      scope: '/',
      start_url: '/?homescreen=1',
      version: 1.0,
      logging: false,
      html: 'index.html',
      pipeHTML: true,
      replace: true,
    })
  )
  .pipe(gulp.dest('./dest'));
```

#### Результат выполнения задачи gulp-favicons

В результате **Gulp** создал нам 64 файла

| 1                                       | 2                                       | 3                                       |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| android-chrome-36x36.png                | android-chrome-48x48.png                | android-chrome-72x72.png                |
| android-chrome-96x96.png                | android-chrome-144x144.png              | android-chrome-192x192.png              |
| android-chrome-256x256.png              | android-chrome-384x384.png              | android-chrome-512x512.png              |
| apple-touch-icon.png                    | apple-touch-icon-57x57.png              | apple-touch-icon-60x60.png              |
| apple-touch-icon-72x72.png              | apple-touch-icon-76x76.png              | apple-touch-icon-114x114.png            |
| apple-touch-icon-120x120.png            | apple-touch-icon-144x144.png            | apple-touch-icon-152x152.png            |
| apple-touch-icon-167x167.png            | apple-touch-icon-180x180.png            | apple-touch-icon-1024x1024.png          |
| apple-touch-icon-precomposed.png        | apple-touch-startup-image-640x1136.png  | apple-touch-startup-image-750x1334.png  |
| apple-touch-startup-image-828x1792.png  | apple-touch-startup-image-1125x2436.png | apple-touch-startup-image-1136x640.png  |
| apple-touch-startup-image-1242x2208.png | apple-touch-startup-image-1242x2688.png | apple-touch-startup-image-1334x750.png  |
| apple-touch-startup-image-1536x2048.png | apple-touch-startup-image-1620x2160.png | apple-touch-startup-image-1668x2224.png |
| apple-touch-startup-image-1668x2388.png | apple-touch-startup-image-1792x828.png  | apple-touch-startup-image-2048x1536.png |
| apple-touch-startup-image-2048x2732.png | apple-touch-startup-image-2160x1620.png | apple-touch-startup-image-2208x1242.png |
| apple-touch-startup-image-2224x1668.png | apple-touch-startup-image-2388x1668.png | apple-touch-startup-image-2436x1125.png |
| apple-touch-startup-image-2688x1242.png | apple-touch-startup-image-2732x2048.png | browserconfig.xml                       |
| coast-228x228.png                       | favicon.ico                             | favicon-16x16.png                       |
| favicon-32x32.png                       | favicon-48x48.png                       | firefox_app_60x60.png                   |
| firefox_app_128x128.png                 | firefox_app_512x512.png                 | index.html                              |
| manifest.json                           | manifest.webapp                         | mstile-70x70.png                        |
| mstile-144x144.png                      | mstile-150x150.png                      | mstile-310x150.png                      |
| mstile-310x310.png                      | yandex-browser-50x50.png                | yandex-browser-manifest.json            |

| favicon-rfi.svg

Похоже, список исчерпывающий. Конечно, не все файлы потребуются, но выбрать есть из чего. Да, вручную такое выполнить непросто.

Интересен файл index.html.

```html
<link rel="shortcut icon" href="favicons/favicon.ico">
<link rel="icon" type="image/png" sizes="16x16" href="favicons/favicon-16x16.png">
<link rel="icon" type="image/png" sizes="32x32" href="favicons/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="48x48" href="favicons/favicon-48x48.png">
<link rel="manifest" href="favicons/manifest.json">
<meta name="mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#fff">
<meta name="application-name" content="ReFreshing">
<link rel="apple-touch-icon" sizes="57x57" href="favicons/apple-touch-icon-57x57.png">
<link rel="apple-touch-icon" sizes="60x60" href="favicons/apple-touch-icon-60x60.png">
<link rel="apple-touch-icon" sizes="72x72" href="favicons/apple-touch-icon-72x72.png">
<link rel="apple-touch-icon" sizes="76x76" href="favicons/apple-touch-icon-76x76.png">
<link rel="apple-touch-icon" sizes="114x114" href="favicons/apple-touch-icon-114x114.png">
<link rel="apple-touch-icon" sizes="120x120" href="favicons/apple-touch-icon-120x120.png">
<link rel="apple-touch-icon" sizes="144x144" href="favicons/apple-touch-icon-144x144.png">
<link rel="apple-touch-icon" sizes="152x152" href="favicons/apple-touch-icon-152x152.png">
<link rel="apple-touch-icon" sizes="167x167" href="favicons/apple-touch-icon-167x167.png">
<link rel="apple-touch-icon" sizes="180x180" href="favicons/apple-touch-icon-180x180.png">
<link rel="apple-touch-icon" sizes="1024x1024" href="favicons/apple-touch-icon-1024x1024.png">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="ReFreshing">
<link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)"    href="favicons/apple-touch-startup-image-640x1136.png">
<link rel="apple-touch-startup-image" media="(device-width: 375px) and (device-height: 667px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)"    href="favicons/apple-touch-startup-image-750x1334.png">
<link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)"    href="favicons/apple-touch-startup-image-828x1792.png">
<link rel="apple-touch-startup-image" media="(device-width: 375px) and (device-height: 812px) and (-webkit-device-pixel-ratio: 3) and (orientation: portrait)"    href="favicons/apple-touch-startup-image-1125x2436.png">
<link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 736px) and (-webkit-device-pixel-ratio: 3) and (orientation: portrait)"    href="favicons/apple-touch-startup-image-1242x2208.png">
<link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 3) and (orientation: portrait)"    href="favicons/apple-touch-startup-image-1242x2688.png">
<link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)"   href="favicons/apple-touch-startup-image-1536x2048.png">
<link rel="apple-touch-startup-image" media="(device-width: 834px) and (device-height: 1112px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)"   href="favicons/apple-touch-startup-image-1668x2224.png">
<link rel="apple-touch-startup-image" media="(device-width: 834px) and (device-height: 1194px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)"   href="favicons/apple-touch-startup-image-1668x2388.png">
<link rel="apple-touch-startup-image" media="(device-width: 1024px) and (device-height: 1366px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)"  href="favicons/apple-touch-startup-image-2048x2732.png">
<link rel="apple-touch-startup-image" media="(device-width: 810px) and (device-height: 1080px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)"  href="favicons/apple-touch-startup-image-1620x2160.png">
<link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)"   href="favicons/apple-touch-startup-image-1136x640.png">
<link rel="apple-touch-startup-image" media="(device-width: 375px) and (device-height: 667px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)"   href="favicons/apple-touch-startup-image-1334x750.png">
<link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)"   href="favicons/apple-touch-startup-image-1792x828.png">
<link rel="apple-touch-startup-image" media="(device-width: 375px) and (device-height: 812px) and (-webkit-device-pixel-ratio: 3) and (orientation: landscape)"   href="favicons/apple-touch-startup-image-2436x1125.png">
<link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 736px) and (-webkit-device-pixel-ratio: 3) and (orientation: landscape)"   href="favicons/apple-touch-startup-image-2208x1242.png">
<link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 3) and (orientation: landscape)"   href="favicons/apple-touch-startup-image-2688x1242.png">
<link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)"  href="favicons/apple-touch-startup-image-2048x1536.png">
<link rel="apple-touch-startup-image" media="(device-width: 834px) and (device-height: 1112px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)"  href="favicons/apple-touch-startup-image-2224x1668.png">
<link rel="apple-touch-startup-image" media="(device-width: 834px) and (device-height: 1194px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)"  href="favicons/apple-touch-startup-image-2388x1668.png">
<link rel="apple-touch-startup-image" media="(device-width: 1024px) and (device-height: 1366px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="favicons/apple-touch-startup-image-2732x2048.png">
<link rel="apple-touch-startup-image" media="(device-width: 810px) and (device-height: 1080px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)"  href="favicons/apple-touch-startup-image-2160x1620.png">
<link rel="icon" type="image/png" sizes="228x228" href="favicons/coast-228x228.png">
<meta name="msapplication-TileColor" content="#0a1922">
<meta name="msapplication-TileImage" content="favicons/mstile-144x144.png">
<meta name="msapplication-config" content="favicons/browserconfig.xml">
<link rel="yandex-tableau-widget" href="favicons/yandex-browser-manifest.json">
```

Как видно, в нем все метатеги и подключения для всех сгенерированных файлов.

### gulp-image

Optimize `PNG, JPEG, GIF, SVG` images with gulp task. См. [gulp-image](https://github.com/1000ch/gulp-image)

#### Usage

Example of `gulpfile.js`.

```js
const gulp = require('gulp');
const image = require('gulp-image');

gulp.task('image', function () {
  gulp.src('./fixtures/*')
    .pipe(image())
    .pipe(gulp.dest('./dest'));
});

gulp.task('default', ['image']);
```

You can pass an object to `image()` as argument such as following:

```js
gulp.task('image', () => {
  gulp.src('./fixtures/*')
    .pipe(image({
      pngquant: true,
      optipng: false,
      zopflipng: true,
      jpegRecompress: false,
      mozjpeg: true,
      gifsicle: true,
      svgo: true,
      concurrent: 10,
      quiet: true // defaults to false
    }))
    .pipe(gulp.dest('./dest'));
});
```

Set `false` for optimizers which you don't want to apply. And you can set `concurrent` option to limit the max concurrency in execution. You can also set `quiet` to avoid logging out results for every image processed.

You can configure parameters applied to each optimizers such as following:

```js
gulp.task('image', () => {
  gulp.src('./fixtures/*')
    .pipe(image({
      optipng: ['-i 1', '-strip all', '-fix', '-o7', '-force'],
      pngquant: ['--speed=1', '--force', 256],
      zopflipng: ['-y', '--lossy_8bit', '--lossy_transparent'],
      jpegRecompress: ['--strip', '--quality', 'medium', '--min', 40, '--max', 80],
      mozjpeg: ['-optimize', '-progressive'],
      gifsicle: ['--optimize'],
      svgo: ['--enable', 'cleanupIDs', '--disable', 'convertColors']
    }))
    .pipe(gulp.dest('./dest'));
});
```

### gulp-size

`npm install --save-dev gulp-size`

`.pipe(size())`

```js
const gulp = require('gulp');
const size = require('gulp-size');

exports.default = () => (
	gulp.src('fixture.js')
		.pipe(size())
		.pipe(gulp.dest('dist'))
);
```

### gulp-markdown-pdf

[gulp-markdown-pdf](https://github.com/sindresorhus/gulp-markdown-pdf#gulp-markdown-pdf)

#### Установка

`$ npm install --save-dev gulp-markdown-pdf`

#### Применение

```js
const gulp = require('gulp');
const markdownPdf = require('gulp-markdown-pdf');

exports.default = () => (
	gulp.src('intro.md')
		.pipe(markdownPdf())
		.pipe(gulp.dest('dist'))
);
```
