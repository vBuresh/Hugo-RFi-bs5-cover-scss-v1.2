---
title: Конфигурация сайта
subtitle: '- пользовательские определения'
date: 2021-06-16T09:33:32+03:00
Lastmod: 2021-06-16T09:33:32+03:00
draft: false
description: Hugo имеет гибкую и многоуровневую систему конфигурации - пользовательских параметров, установок и определений по которым генерируется сайт.
summary: Пользовательские установки и определения по которым Hugo генерирует сайт
author:
  # given_name: Vladimir
  # family_name: Buresh
  display_name: ['Hugo Authors', 'wBuresh']
categories: [configuration]
tags: [hugo, настройки]
# categories: [content-management]
# tags: [hugo, templates, taxonomy]
toc: true
---

В IT сообществе термин «конфигурация» обычно понимается как совокупность установок и настроек ПО, задаваемая пользователем, а термин «конфигурация»  —  как процесс изменения этих настроек в соответствии с нуждами пользователя. Для целей Hugo «конфигурация» - это пользовательские установки и настройки, в соответствии с которыми генерируется сайт.

Конфигурация в Hugo отличается простотой  и гибкостью. Кроме того, настройки в Hugo многоуровневые:

- глобальные - файл: config.toml либо config.yaml либо config.json
- для определенных типов контента (группы документов) - Configuration Directory
- для конкретного документа - Front Matter

В руководстве Hugo конфигурации посвящена отдельная, довольно большая страница -  [конфигурация Hugo  (Configure Hugo)](https://gohugo.io/getting-started/configuration/) с подробными разъяснениями и примерами. Вот ее содержание^

1. [Конфигурационный файл (Configuration File)](https://gohugo.io/getting-started/configuration/#configuration-file)
1. [Configuration Directory](https://gohugo.io/getting-started/configuration/#configuration-directory)
1. [Все конфигурационные установки (All Configuration Settings)](https://gohugo.io/getting-started/configuration/#all-configuration-settings)
1. [Конфигурация сборки (Configure Build)](https://gohugo.io/getting-started/configuration/#configure-build)
1. [Конфигурация сервера (Configure Server)](https://gohugo.io/getting-started/configuration/#configure-server)
1. [Configure Title Case](https://gohugo.io/getting-started/configuration/#configure-title-case)
1. [Configuration Environment Variables](https://gohugo.io/getting-started/configuration/#configuration-environment-variables)
1. [Configuration Lookup Order](https://gohugo.io/getting-started/configuration/#configuration-lookup-order)
1. [Example Configuration](https://gohugo.io/getting-started/configuration/#example-configuration)
1. [Configure with Environment Variables](https://gohugo.io/getting-started/configuration/#configure-with-environment-variables)
1. [Ignore Content and Data Files when Rendering](https://gohugo.io/getting-started/configuration/#ignore-content-and-data-files-when-rendering)
1. [Конфигурация «шапки» (Configure Front Matter)](https://gohugo.io/getting-started/configuration/#configure-front-matter)
1. [Configure Dates](https://gohugo.io/getting-started/configuration/#configure-dates)
1. [Configure Additional Output Formats](https://gohugo.io/getting-started/configuration/#configure-additional-output-formats)
1. [Configure Minify](https://gohugo.io/getting-started/configuration/#configure-minify)
1. [Configure File Caches](https://gohugo.io/getting-started/configuration/#configure-file-caches)
1. [The keywords explained](https://gohugo.io/getting-started/configuration/#the-keywords-explained)
1. [Configuration Format Specs](https://gohugo.io/getting-started/configuration/#configuration-format-specs)
