---
subtitle: попытка сравнения
date: 2020-03-02T10:58:50+03:00
Lastmod: 2021-06-15T13:38:40+33:00
title: Atom или VSCodium
description: Общее у этих двух замечательных редакторов
summary: three-line summary of the article.
draft: false
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [веб-разработка]
tags: ['Atom', 'VSCodium']
---

To install it follow this guide:

[https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo](https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo)

[Debian Wiki - Подробнее](https://wiki.debian.org/VisualStudioCode)

Что сказать? Установил **VSCodium** и полегчало. Кажется, что это именно то, на что можно потратить время. [Делаем страничку «VSCodium»]({{< ref "vscodium" >}})

How to install for Debian/Ubuntu/Linux Mint

If software-properties-common is available, you can use apt-add and apt-add-repository to add the new repository and its key.

{{< highlight bash >}}
wget -qO - https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg | sudo apt-key add -
sudo apt-add-repository 'deb https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/repos/debs/ vscodium main'
sudo apt update
sudo apt install codium
{{< /highlight >}}

## Кастомизация

Это следует делать не спеша, ибо потом не разберешься что ломает.

### Атом тема и раскладка

1. Atom's iconic [One Dark theme](https://github.com/Binaryify/OneDark-Pro) for Visual Studio Code (id - zhuangtongfa.material-theme)
2. [Atom Keymap for VS Code](https://github.com/Microsoft/vscode-atom-keybindings)

Предлагаемая подсветка синтаксиса всех html, js, sass, md пока полностью меня устраивает.
Правда для md и Hugo пришлось подгружать плагины:

### Общесистемные плагины

1. Spelling Checker for Visual Studio Code
2. Rainbow Brackets for Visual Studio Code
3. Auto Rename Tag
4. Prettier Formatter for Visual Studio Code
5. Todo Tree

### Для церковнославянской типографики

1. Church Slavonic Markdown
2. VSCode Church Slavonic keyboard

Все подгружено и ожидает. Подробнее на странице

### Плагины для Hugo

1. Better TOML is vs code extension to support TOML file
2. Syntax highlighting and snippets for Hugo websites (id - budparr.language-hugo-vscode)
3. Hugo Snippets (id - fivethree.vscode-hugo-snippets)
4. Hugo language - Syntax highlighting and snippets for Hugo websites.
5. Hugo Shortcode Syntax Highlighting (id - kaellarkin.hugo-shortcode-syntax)

### Плагины для Markdown

[Markdown All in One](https://github.com/yzhang-gh/vscode-markdown)

Это очень богатый плагин

### Плагины для SVG
