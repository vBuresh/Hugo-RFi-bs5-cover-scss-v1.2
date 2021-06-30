---
date: 2019-11-08T18:20:14+03:00
Lastmod: 2021-06-30T:06:42:01+03:00
title: Виртуальные хосты Apache на Debian
subtitle: subtitle of the published article
description: short description of the article
summary: three-line summary of the article.
draft: false
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories: [Веб-разработка]
# categories: ['Web development']
tags: [Debian, Настройки, Хостинг]
toc: true
---

## Apache Virtual Hosts on Debian

>[Веб-сервер **Apache**](https://ru.wikipedia.org/wiki/Apache_HTTP_Server) – кроссплатформенный [свободный](https://ru.wikipedia.org/wiki/%D0%A1%D0%B2%D0%BE%D0%B1%D0%BE%D0%B4%D0%BD%D0%BE%D0%B5_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%BD%D0%BE%D0%B5_%D0%BE%D0%B1%D0%B5%D1%81%D0%BF%D0%B5%D1%87%D0%B5%D0%BD%D0%B8%D0%B5) [веб-сервер](https://ru.wikipedia.org/wiki/%D0%92%D0%B5%D0%B1-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80). Более половины всех серверов по всему миру используют [**Apache**](https://ru.wikipedia.org/wiki/Apache_HTTP_Server).

## Достоинства

- Быстродействие, надёжность, безопасность
- Гибкость конфигурации
  - основа - текстовые конфигурационные файлы на собственном языке с блоками директив.
  - Три уровня конфигурации
    1. сервера ([httpd.conf](https://ru.wikipedia.org/wiki/Httpd.conf)).
    2. виртуального хоста (httpd.conf c версии 2.2, extra/httpd-vhosts.conf).
    3. каталога ([.htaccess](https://ru.wikipedia.org/wiki/.htaccess)).

- Возможность подключения внешних модулей _(более 500)_ для предоставления данных, использовать СУБД для аутентификации пользователей, модифицировать сообщения об ошибках и т.д.
- Встроенный механизм виртуальных [хостов](https://ru.wikipedia.org/wiki/%D0%A5%D0%BE%D1%81%D1%82), позволяющий обслуживать на одном [IP-адресе](https://ru.wikipedia.org/wiki/IP-%D0%B0%D0%B4%D1%80%D0%B5%D1%81) множество [сайтов](https://ru.wikipedia.org/wiki/%D0%A1%D0%B0%D0%B9%D1%82) ([доменных имён](https://ru.wikipedia.org/wiki/%D0%94%D0%BE%D0%BC%D0%B5%D0%BD%D0%BD%D0%BE%D0%B5_%D0%B8%D0%BC%D1%8F)) с собственным содержимым, а также настройками ядра и модулей, ограничениями доступами ко всему сайту или отдельным файлам.

## **Установка**

ssh root@server_ip
: Подключение к серверу по SSH

dpkg -l apache2
: Проверка, не установлен ли  Apache ранее

sudo apt update<br>apt-get install apache2
: Установка Apache. Возможно: apache2-doc libapache2-mod-php

systemctl enable apache2
: Включить Apache для запуска автоматически после перезапуска сервера

systemctl status apache2
: Проверка состояния службы Apache

Команда: `systemctl status apache2`

``` bash {linenos=true}
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset>
     Active: active (running) since Wed 2021-06-30 06:23:39 MSK; 26min ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 597 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCC>
   Main PID: 678 (apache2)
      Tasks: 56 (limit: 19008)
     Memory: 26.7M
        CPU: 168ms
     CGroup: /system.slice/apache2.service
             ├─678 /usr/sbin/apache2 -k start
             ├─679 /usr/sbin/apache2 -k start
             ├─680 /usr/sbin/apache2 -k start
             └─681 /usr/sbin/apache2 -k start
```

## Виртуальные хосты

Виртуальные хосты **Apache** -- это комплект директив конфигурации, которые обеспечивают размещение неограниченного количества веб-сайтов, используя один веб-сервер **Apache**. То есть, если на сервере есть несколько сайтов, то для корректного отображения всех сайтов необходима настройка (конфигурирование) **Apache**.

### Типы виртуальных постов

Веб-сервером **Apache** поддерживаются два типа виртуальных хостов -- на основе **имен** (_name-based virtual hosts_) и на основе **IP** (_IP-based virtual hosts_).

Виртуальные хосты на основе имен
: Применяются при размещении несколько веб-сайтов на одном сервере
Виртуальный хост на основе IP
: Позволяет иметь только один веб-сайт на одном IP-адресе

Однако, локальный сервер имеет только один IP: **127.0.0.1**, поэтому вариант с привязкой к IP подходит далеко не всегда. В связи с этим, наиболее распространенным является использование виртуальных хостов на базе имен, привязанных к одному IP-адресу. Таким образом, можно хранить множество сайтов на одном IP.

### webroot - каталоги сайтов

В качестве примера будет создано два сайта:

<!-- wp:list -->

- rfm-bsblog.ru
- rfm-bscover.ru

Для хранения компонентов этих сайтов необходимо создать корневые директории. Обычно их размещают в директории `**/var/www/**`

Это легко сделать при помощи команд:

``` bash
sudo mkdir -p /var/www/rfm-bsblog.ru/public_html
sudo mkdir -p /var/www/rfm-bscover.ru/public_html
```

Важно обратить внимание, что в каждой директории **сайты** будет создана поддиректория **public_html**, для размещения файлов. Это придаст хостингу необходимую гибкость.


#### Стартовые страницы

Затем в поддиректория **public_html** каждого сайта, командой **`nano index.html`**, нужно создать тестовые стартовые (индексные) страницы **`index.html`** следующего содержания:


``` html
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Новый сайт</title>
  </head>
  <body>
    <h1>Привет!</h1>
    <p>Это новый сайт rfm-bsblog.ru / rfm-bscover.ru <!-- соответственно --></p>
  </body>
</html>
```

Затем **веб-серверу Apache** необходимо предоставить требуемый доступ к этим файлам (дать соответствующие разрешения), а также установить пользователя и группу.

Важно обратить внимание , что поддиректории в `/var/www/` созданы с помощью **sudo**, поэтому принадлежат пользователю **root**. Чтобы обычные пользователи могли редактировать файлы в этих директориях, нужно дать им такие права:

``` bash
sudo chown -R $USER:$USER /var/www/rfm-bsblog.ru/public_html
sudo chown -R $USER:$USER /var/www/rfm-bscover.ru/public_html
```

После этого переменная $USER примет имя текущего пользователя и он получит права на поддиректории public_html, в которых будет храниться контент.

Кроме того, нужно не забыть предоставить пользователям право на чтение директории сайта и всех его поддиректорий (чтобы страницы отображались правильно). Для следует выполнить команду:

``` bash
sudo chmod -R 755 /var/www
```

Создание структуры директорий завершено.

#### Файлы виртуальных хостов

Теперь следует создать файлы виртуальных хостов (с расширением **`.conf`**). Они задают настройки отдельных сайтов и помогают Apache корректно отвечать на запросы.

Стандартный файл хоста с именем **000-default.conf**, который можно использовать в качестве шаблона, поставляется с Apache и размещается в директории _`/etc/apache2/sites-available/`_. Его нужно скопировать его, чтобы создать виртуальный хост для каждого доменного имени: **rfm-bsblog.ru** и **rfm-bscover.ru**.

``` bash
# для rfm-bsblog.ru
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/rfm-bsblog.ru.conf
# для rfm-bscover.ru.conf
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/rfm-bscover.ru.conf
```

Затем следует открыть и отредактировать файлы:

``` bash
# для rfm-bsblog.ru
sudo nano /etc/apache2/sites-available/rfm-bsblog.ru.conf
# для rfm-bscover.ru
sudo nano /etc/apache2/sites-available/rfm-bscover.ru.conf
```

По умолчанию файл **.conf** обычно имеет следующее содержание:

``` bash
<VirtualHost *:80>
# виртуальный хост прослушивает порт 80:
  ServerAdmin webmaster@localhost
# указывает адрес адрес электронной почты администратора, включаемый сервером в любые сообщения об ошибках (без возвращения клиенту). Атрибут необязательной, можно вообще удалить строку.
  DocumentRoot /var/www/html
# определяет место, где должен искать Apache при обработке запроса для домена, определенного в ServerName или ServerAlias
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Нужно отредактировать конфигурацию по умолчанию, заменив соответствующие значения собственными.

``` bash
<VirtualHost *:80>

ServerAdmin admin@rfm-bsblog.ru
ServerName rfm-bsblog.ru
ServerAlias www.rfm-bsblog.ru
DocumentRoot /var/www/rfm-bsblog.ru/public_html

ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

## Настройка локальных хостов (опционально)

Если у вас нет доменного имени, и вместо настоящего вы использовали условный домен, вы можете протестировать настройки, временно отредактировав файл hosts на локальном компьютере. Он будет перехватывать запросы на настроенные ранее домены и направлять их на VPS (то есть, выполнять работу DNS). Но этот метод работает только на локальной машине и подходит только для тестирования.

**Примечание**: Убедитесь, что вы перешли на локальную машину. Для выполнения данного раздела нужны учётные данные администратора.

Отредактируйте файл hosts с привилегиями администратора.

``` bash
sudo nano /etc/hosts
```

В этом файле нужно указать IP-адрес сервера, а затем доменное имя, которое будет использоваться для доступа к серверу.

К примеру, если IP-адрес сервера -- `**111.111.111.111**`, в конец файла хоста нужно внести следующие строки:



``` bash
127.0.0.1   localhost
...
111.111.111.111 rfm-bsblog.ru
111.111.111.111 rfm-bscover.ru
```

Теперь все запросы к rfm-bsblog.ru и rfm-bscover.ru будут отправлены на локальный компьютер, а оттуда -- на IP-адрес сервера.

Сохраните и закройте файл.

## Результаты

Чтобы протестировать настройку виртуальных хостов, просто откройте домен в веб-браузере: `**rfm-bsblog.ru**`

сообщение:

`Success! The` **rfm-bsblog.ru**`virtual host is working!`

**Примечание**: Результат, появившийся на экране, зависит от содержания созданного html файла.

Точно так же нужно проверить и второй сайт: **`rfm-bscover.ru`**

Если оба сайта работают, значит, виртуальные хосты настроены правильно.

**Примечание**: Если файл hosts на локальном компьютере был изменён, после тестирования удалите внесённые в него строки, чтобы не засорять файл ненужными записями.

---

<!--
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 64:00:6a:72:4d:9a brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.38/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s31f6
       valid_lft 19594sec preferred_lft 19594sec
    inet6 fe80::6600:6aff:fe72:4d9a/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```
-->

Выполните следующую команду для создания файла конфигурации виртуального хоста для нашего первого домена **domain1.ru** :

shell

``` bash
# для сайта rfm-bsblog.ru
nano /etc/apache2/sites-available/rfm-bsblog.ru.conf
# для сайта rfm-bscover.ru
nano /etc/apache2/sites-available/rfm-bscover.ru.conf
```

 <!-- wp:heading {"level":3} -->

### Файлы конфигурации Аpache

Файл конфигурации для rfm-bsblog.ru с подстрочными комментариями.

``` bash
<VirtualHost *:80>
# виртуальный хост прослушивает порт 80:

ServerAdmin admin@rfm-bsblog.ru
# указывается адрес адрес электронной почты администратора, включаемый сервером в любые сообщения об ошибках (без возвращения клиенту). Атрибут необязательной, можно вообще удалить строку.
ServerName rfm-bsblog.ru
# имя домена
ServerAlias www.rfm-bsblog.ru
# дополнительные имена, которые должны совпадать, как если бы они являлись исходными именами доменов
DocumentRoot /var/www/html/rfm-bsblog.ru
# определяет место, где должен искать Apache при обработке запроса для домена, определенного в ServerName или ServerAlias

ErrorLog ${APACHE_LOG_DIR}/rfm-bsblog.ru_error.log
CustomLog ${APACHE_LOG_DIR}/rfm-bsblog.ru_access.log combined
# В этих строках указано местоположение файлов журнала

</VirtualHost>
```

Файл конфигурации для rfm-bscover.ru выглядит так:



``` bash
<VirtualHost *:80>

ServerAdmin admin@rfm-bscover.ru
ServerName rfm-bscover.ru
ServerAlias www.rfm-bscover.ru
DocumentRoot /var/www/html/rfm-bscover.ru

ErrorLog ${APACHE_LOG_DIR}/rfm-bscover.ru_error.log
CustomLog ${APACHE_LOG_DIR}/rfm-bscover.ru_access.log combined

</VirtualHost>
```

#### Включение виртуальных хостов

Включить виртуальные хосты можно одним из двух способов:

shell

##### 1. Командами:



``` bash
a2ensite rfm-bsblog.ru.conf
a2ensite rfm-bscover.ru.conf

# выдается сообщение: bash: a2ensite: команда не найдена
```

Такие ситуации встречались см. форум Debian: [a2ensite не найден](https://debianforum.ru/index.php?topic=15117.0) (11.08.2019). Применяем второй способ, так как, по мнению специалистов "_переменные окружения могут быть разными и для одного пользователя. Достаточно запомнить, что абсолютные пути всегда верны и тогда "проблемы" как бы и не существует._"

##### 2. Созданием символических ссылок

При этом способе символическая ссылка создается для каждого виртуального хоста в директории: **`/etc/apache2/sites-enabled`**

``` bash
ln -s /etc/apache2/sites-available/rfm-bsblog.ru.conf /etc/apache2/sites-enabled/
ln -s /etc/apache2/sites-available/rfm-bscover.ru.conf /etc/apache2/sites-enabled/
```

Сделано вторым способом. После включения виртуальных хостов (одним из двух возможных способов) необходимо перезапустить **веб-сервер Apache**:

```
systemctl restart apache2
```

Если всё правильно, браузер успешно откроет сайты.

<!--
Однако этого не получилось.

Если в поисковой строке набирать имена сайтов, которые нужны:

<!-- wp:list -->

- vblog.com
- rfm-bsblog.ru
- rfm-bscover.ru

Firefox выдает сообщение:

**This site can't be reached**<br>
**vblog.com**'s server IP address could not be found.DNS_PROBE_FINISHED_NXDOMAIN

Приэтом ip адрес 127.0.0.1 и [localhost](http://localhost/) открывают сайт rfm-bsblog.ru.

### Решение зреет

-->









 <div class="pt-3 border-top border-bottom mb-3">
  <h2 class="h4">В тему:</h2>
  <ol>
  <li>"<a href="https://ru.wikipedia.org/wiki/Apache_HTTP_Server" target="_blank" rel="noopener noreferrer">Apache HTTP Server</a>" - <em>Материал из Википедии — свободной энциклопедии</em>.</li>
  <li><a href="https://andreyex.ru/operacionnaya-sistema-debian/kak-nastroit-virtualnye-hosty-apache-na-debian-9/" target="_blank" rel="noopener noreferrer">Как настроить виртуальные хосты Apache на Debian 9</a> (andreyex.ru, ред.2018-07-10)</li>
  <li><a href="https://losst.ru/nastrojka-virtualnyh-hostov-apache">Настройка виртуальных хостов Apache</a> (losst.ru, диванный аналитик 05.10.2017)</li>
  <li><a href="https://habr.com/ru/sandbox/3533/" target="_blank" rel="noopener noreferrer">Настройка виртуальных хостов на Apache для начинающих</a> (Habr, диванный аналитик 07.07.2009)</li>
</ol>
</div>

-->
