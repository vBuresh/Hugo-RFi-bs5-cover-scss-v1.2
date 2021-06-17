---
title: Atom vs VScode
subtitle: '- орфография в Atom'
date: 2020-01-16T11:54:49+03:00
Lastmod: 2021-06-15T11:29:01+03:00
summary: 'Управление содержимым - важнейшая задача на всех этапах создания, развития и поддержки сайта'
draft: false
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [веб-разработка]
tags: [Atom, VScode]
---

# Atom - VSCodium (VScode)

Visual Studio Code

В прощенное воскресенье, послал мне Господь [VSCodium]({{< ref "vscodium" >}})

## Снова зуд

В очередной раз появилось желание получше присмотреться, а, возможно и перейти на VScode. Причин и поводов достаточно. Поразмыслим о достоинствах VScode:

1. Многочисленное сообщество;
1. Очень много функций работает из коробки;
1. Масса активно поддерживаемых плагинов;
1. Хорошая проверялка орфографии (Spell Checker);

> вторник, 15 июня 2021 г., 13:48 - отличная [проверка синтаксиса и в Атоме]({{< ref "/spell-check" >}}). нужно только уметь ее настраивать.

Минусы

- нет такой мягкости, как у Atom;
- Придется переписывать сниппеты;

Плагины для Hugo:

Рекомендованные Hugo [Editor Plug-ins for Hugo](https://gohugo.io/tools/editors/#visual-studio-code)

- Hugofy. Hugofy is a plugin for Visual Studio Code to “make life easier” when developing with Hugo. The source code can be found here.
- Hugo Helper. Hugo Helper is a plugin for Visual Studio Code that has some useful commands for Hugo. The source code can be found here.
- Hugo Language and Syntax Support. Hugo Language and Syntax Support is a Visual Studio Code plugin for Hugo syntax highlighting and snippets. The source code can be found here.

Добавлено:

- [VSCode Front Matter Helpers](https://marketplace.visualstudio.com/items?itemName=eliostruyf.vscode-front-matter)
- Better TOML

{{< highlight javascript >}}
{
"key": "alt+meta+d",
"command": "editor.action.duplicateSelection"
}
{{< /highlight >}}

## И снова зовет VScode

Не прошло и пол-года... Какой там пол-года! Уже через месяц снова зачесалось. Ох и достал же бестолковый "Атомный" Spell Check.

Начинаю и очередную миграцию с Atom на VScode. Как бы не пятую. Причины те же. А главное:

1. В Atom безобразно работает Spell Check. Все время активного применения Атом я ждал и верил. Как видно - напрасно.
1. Все-таки есть некоторая "тормознутось", хотя разработчики Atom работают над проблемой серьезно. Но, похоже, есть что-то непреодолимое.
1. Плагин CSL заточен только на VScode.


А VScode имеет массу функций - "из коробки" и очень продвинутые плагины. На таком фоне Atom кажется утехой кошерных фанатиков (сектантов), каким был я. Однако достали.

Были жалобы на количество "присматриваемых" файлов. «Unable to watch for file changes in this large workspace. [Please follow the instructions link to resolve this issue](https://code.visualstudio.com/docs/setup/linux#_visual-studio-code-is-unable-to-watch-for-file-changes-in-this-large-workspace-error-enospc)».

Чтобы узнать количество можно командой `cat /proc/sys/fs/inotify/max_user_watches`. Оказалось около 65k. Потребовалось увеличить количество (пока до 224288). Для этого рекомендовалось в конце файла `/etc/sysctl.conf` добавить строку `fs.inotify.max_user_watches=524288`, где 524288 - максимальное количество. Затем потребовалось загрузить изменения командой:

{{< highlight terminal >}}
sudo sysctl -p
fs.inotify.max_user_watches = 224288)
{{< /highlight >}}

Пока VScode радует. Однако такое у меня уже было. Ностальгия обостряется на третий день. Именно столько мне удавалось продержаться на VScode в прошлые попытки миграции. Однако продержался

### Сниппеты

Заметным камнем преткновения для миграции были сниппеты (англ. snippet — фрагмент, отрывок) — фрагменты исходного кода или текста, пригодного для повторного использования. Они очень облегчают и ускоряют работу. Поэтому для Атома я их наделал немало. Придется мигрировать.

В руки - официальная документация VS Code - страница по созданию сниппетов. Там много хорошего. В частности:

- [Официальная документация VS Code](https://code.visualstudio.com/docs)
- [Создание собственных сниппетов](https://code.visualstudio.com/docs/editor/userdefinedsnippets?wt.mc_id=devto-blog-chnoring)

Есть и еще материалы на просторах интернета, например:

- [Сниппеты в VS Code](https://dev-gang.ru/article/fragmenty-koda-vs-of3zdc2f54/)
- [VS Code - Публикуем свое (сниппет) расширение](https://dev-gang.ru/article/vs-code-opublikuite-svoe-snippet-rasshirenie-fh6iqx47qn/)

## Плюсы VS Code

Удобная навигация.

## VSCodium

Однако не все так просто. Ведь M$ - гнилая контора. И вот явился **VSCodium** - VSCode without MS branding/telemetry/licensing. Take a look at this project: [https://github.com/VSCodium/vscodium](https://github.com/VSCodium/vscodium)
