---
title: Guplpfile.js
# subtitle: continuer of the title in a two words
date: 2021-05-26T06:30:51+03:00
Lastmod: 2021-05-26T06:30:51+03:00
draft: false
# description: "- дополнение к заголовку (подзаголовок)"
# summary: краткое изложение - зачем читать сие
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
toc: true
categories:
  - "webDev"
tags:
  - Gulp
toc: true
---

## Текущий guplpfile.js

Текущий

{{< highlight js >}}

var gulp = require('gulp');
var del = require('del');
var favicons = require('gulp-favicons');
var image = require('gulp-image');
var size = require('gulp-size');

var path = {
  styles: {
    src: "/src/sass/vera/**/*.sass",
    // Compiled files will end up in whichever folder it's found in (partials are not compiled)
    dest: "src/styles"
  },
  build: {
    html: '_app/',
    js: '_app/js/',
    css: '_app/css/',
    img: '_app/img/',
    fonts: '_app/fonts/'
  },
  public: {
    html: 'public/',
    js: 'public/js/',
    css: 'public/css/',
    img: 'public/img/',
    fonts: 'public/fonts/'
  },
  node_modules: {
    bootstrap: 'node_modules/bootstrap/',
    bootswatch: 'node_modules/bootswatch/',
    jquery: 'node_modules/jquery/dist/',
    popper: 'node_modules/popper.js/dist/'
  }
};

// это примитив задачи
gulp.task('upss', function(done) {
  console.log('Отлично! Это рабочий пример');
  done();
});
// Генерация favicons
////////////////////////////////
gulp.task('favicons', function(done) {
  gulp
    .src('./wMedia/rawFAVicons/favicon-rfi.png')
    .pipe(
      favicons({
        appName: 'ReFreshing',
        appShortName: 'RFi',
        appDescription: 'ReFreshing - Hugo Theme',
        developerName: 'wBuresh',
        developerURL: 'https://cybmir.ru/',
        background: '#0a1922',
        path: 'favicons/',
        url: 'https://cybmir.ru/',
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
    .pipe(size())
    .pipe(gulp.dest('./wMedia/favicons/'));
  // copy favicons to the project - /static
  gulp.src([
      //'./wMedia/favicons-safari-pinned-tab/safari-pinned-tab.svg', // w!-негенерируется
      './wMedia/favicons/android-chrome-192x192.png',
      './wMedia/favicons/android-chrome-512x512.png',
      './wMedia/favicons/apple-touch-icon.png',
      './wMedia/favicons/favicon.ico',
      './wMedia/favicons/favicon-16x16.png',
      './wMedia/favicons/favicon-32x32.png',
      './wMedia/favicons/manifest.json'
    ])
    .pipe(size())
    .pipe(gulp.dest('./@_^RFi/static/assets/img/favicons'));
  done();
});

// images optimaiser
////////////////////////////////

gulp.task('image', function(done) {
  gulp.src('./wMedia/rawIMG/*')
    .pipe(image())
    .pipe(gulp.dest('./wMedia/img_opti/images-min'));
  done();
  // console.log('Изображния оптимизируются и  передаются в проект Hugo-Refreshing');
});

// gulp.task('default', ['image']);

// Deleting uotdated bs5 files
/////////////////////////////////////
gulp.task('bsdel', function() {
  return del([
    '.^@^_RFi/assets/bootstrap/scss/**/*',
    '^@^_RFi/assets/js/bootstrap.bundle.min.js',
    '^@^_RFi/static/js/bootstrap.bundle.min.js.map'
  ]);
});

// copy bs5 scss, js to the project
////////////////////////////////

gulp.task('bsup', function(done) {
  // copy BS styles
  gulp.src([
      './bootstrap/scss/**/*',
    ])
    .pipe(gulp.dest('./^@^_RFi/assets/bootstrap/scss/'));
  // copy BS scripts
  gulp.src([
      './bootstrap/dist/js/bootstrap.bundle.min.js',
    ])
    .pipe(gulp.dest('./^@^_RFi/assets/js/'));
  // copy BS .min.js.map to static
  gulp.src([
      './bootstrap/dist/js/bootstrap.bundle.min.js.map',
    ])
    .pipe(gulp.dest('./^@^_RFi/static/js'));
  done();
  console.log('Стили и скрипты bs5 скопированы в рабочие директории');
});

// function clean(cb) {
//   del(['./dist/']);
//   cb();
// }
//
// exports.default = series(clean, parallel(process1, process2));

// copy other resources to the project
////////////////////////////////

gulp.task('cssjs', function(done) {
  // copy styles
  gulp.src([
      './bootstrap/scss',
    ])
    .pipe(gulp.dest('^@^_RFi/assets/bootstrap'));
  // copy BS scripts
  gulp.src([
      './bootstrap/dist/js/bootstrap.bundle.min.js',
      './dark-mode-switch/dark-mode-switch.min.js'
    ])
    .pipe(gulp.dest('./@_^RFi/assets/js/'));
  // copy BS .min.js.map to static
  gulp.src([
      './bootstrap/dist/js/bootstrap.bundle.min.js.map',
    ])
    .pipe(gulp.dest('./@_^RFi/static/js'));
  done();
  console.log('Стили и скрипты скопированы в рабочие директории');
});
{{< / highlight >}}


## Gulp 4 sample gulpfile.js

by Jérôme Coupé GitHub Gist

{{< highlight js "linenos=true" >}}
"use strict";

// Load plugins
const autoprefixer = require("autoprefixer");
const browsersync = require("browser-sync").create();
const cp = require("child_process");
const cssnano = require("cssnano");
const del = require("del");
const eslint = require("gulp-eslint");
const gulp = require("gulp");
const imagemin = require("gulp-imagemin");
const newer = require("gulp-newer");
const plumber = require("gulp-plumber");
const postcss = require("gulp-postcss");
const rename = require("gulp-rename");
const sass = require("gulp-sass");
const webpack = require("webpack");
const webpackconfig = require("./webpack.config.js");
const webpackstream = require("webpack-stream");

// BrowserSync
function browserSync(done) {
  browsersync.init({
    server: {
      baseDir: "./_site/"
    },
    port: 3000
  });
  done();
}

// BrowserSync Reload
function browserSyncReload(done) {
  browsersync.reload();
  done();
}

// Clean assets
function clean() {
  return del(["./_site/assets/"]);
}

// Optimize Images
function images() {
  return gulp
    .src("./assets/img/**/*")
    .pipe(newer("./_site/assets/img"))
    .pipe(
      imagemin([
        imagemin.gifsicle({ interlaced: true }),
        imagemin.jpegtran({ progressive: true }),
        imagemin.optipng({ optimizationLevel: 5 }),
        imagemin.svgo({
          plugins: [
            {
              removeViewBox: false,
              collapseGroups: true
            }
          ]
        })
      ])
    )
    .pipe(gulp.dest("./_site/assets/img"));
}

// CSS task
function css() {
  return gulp
    .src("./assets/scss/**/*.scss")
    .pipe(plumber())
    .pipe(sass({ outputStyle: "expanded" }))
    .pipe(gulp.dest("./_site/assets/css/"))
    .pipe(rename({ suffix: ".min" }))
    .pipe(postcss([autoprefixer(), cssnano()]))
    .pipe(gulp.dest("./_site/assets/css/"))
    .pipe(browsersync.stream());
}

// Lint scripts
function scriptsLint() {
  return gulp
    .src(["./assets/js/**/*", "./gulpfile.js"])
    .pipe(plumber())
    .pipe(eslint())
    .pipe(eslint.format())
    .pipe(eslint.failAfterError());
}

// Transpile, concatenate and minify scripts
function scripts() {
  return (
    gulp
      .src(["./assets/js/**/*"])
      .pipe(plumber())
      .pipe(webpackstream(webpackconfig, webpack))
      // folder only, filename is specified in webpack config
      .pipe(gulp.dest("./_site/assets/js/"))
      .pipe(browsersync.stream())
  );
}

// Jekyll
function jekyll() {
  return cp.spawn("bundle", ["exec", "jekyll", "build"], { stdio: "inherit" });
}

// Watch files
function watchFiles() {
  gulp.watch("./assets/scss/**/*", css);
  gulp.watch("./assets/js/**/*", gulp.series(scriptsLint, scripts));
  gulp.watch(
    [
      "./_includes/**/*",
      "./_layouts/**/*",
      "./_pages/**/*",
      "./_posts/**/*",
      "./_projects/**/*"
    ],
    gulp.series(jekyll, browserSyncReload)
  );
  gulp.watch("./assets/img/**/*", images);
}

// define complex tasks
const js = gulp.series(scriptsLint, scripts);
const build = gulp.series(clean, gulp.parallel(css, images, jekyll, js));
const watch = gulp.parallel(watchFiles, browserSync);

// export tasks
exports.images = images;
exports.css = css;
exports.js = js;
exports.jekyll = jekyll;
exports.clean = clean;
exports.build = build;
exports.watch = watch;
exports.default = build;
{{< /highlight >}}
