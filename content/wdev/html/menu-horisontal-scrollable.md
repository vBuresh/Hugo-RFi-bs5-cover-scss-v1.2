---
title: "Горизонтальное прокручиваемое меню"
date: 2019-11-03T11:07:30+03:00
draft: false
---

## Как сделать - горизонтальное прокручиваемое меню

[How To Create a Horizontal Scrollable Menu](https://www.w3schools.com/howto/howto_css_menu_horizontal_scroll.asp)

### html
``` html
<div class="scrollmenu">
 <a href="#home">Home</a>
 <a href="#news">News</a>
 <a href="#contact">Contact</a>
 <a href="#about">About</a>
 ...
</div>

<div class="scrollmenu">
 <a href="#home">Home</a>
 <a href="#news">News</a>
 <a href="#contact">Contact</a>
 <a href="#about">About</a>
 ...
</div>


```

``` css
div.scrollmenu {
  background-color: #333;
  overflow: auto;
  white-space: nowrap;
}

div.scrollmenu a {
  display: inline-block;
  color: white;
  text-align: center;
  padding: 14px;
  text-decoration: none;
}

div.scrollmenu a:hover {
  background-color: #777;
}

```
Страница

``` html
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
div.scrollmenu {
    background-color: #333;
    overflow: auto;
    white-space: nowrap;
}

div.scrollmenu a {
    display: inline-block;
    color: white;
    text-align: center;
    padding: 14px;
    text-decoration: none;
}

div.scrollmenu a:hover {
    background-color: #777;
}
</style>
</head>
<body>

<div class="scrollmenu">
  <a href="#home">Home</a>
  <a href="#about">About</a>
  <a href="#blog">Blog</a>
  <a href="#tools">Tools</a>
  <a href="#base">Base</a>
  <a href="#custom">Custom</a>
  <a href="#more">More</a>
  <a href="#logo">Logo</a>
  <a href="#friends">Friends</a>
  <a href="#partners">Partners</a>
  <a href="#people">People</a>
  <a href="#work">Work</a>
</div>

<h2>Horizontal Scrollable Menu</h2>
<p>Resize the browser window to see the effect.</p>

</body>
</html>
```
