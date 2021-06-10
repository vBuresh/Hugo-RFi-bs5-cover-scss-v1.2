---
title: Hugo’s Built-in Shortcodes
date: "2020-07-06T13:10:04+03:00"
draft: false
categories:
  - webDev
tags:
categories: [content-management]
tags: [hugo, shortcodes]
toc: true
---

Hugo ships with a set of predefined shortcodes that represent very common usage. These shortcodes are provided for author convenience and to keep your markdown content clean.
figure

figure is an extension of the image syntax in markdown, which does not provide a shorthand for the more semantic HTML5 `<figure>` element.

The figure shortcode can use the following named parameters:

src
    URL of the image to be displayed.
link
    If the image needs to be hyperlinked, URL of the destination.
target
    Optional target attribute for the URL if link parameter is set.
rel
    Optional rel attribute for the URL if link parameter is set.
alt
    Alternate text for the image if the image cannot be displayed.
title
    Image title.
caption
    Image caption. Markdown within the value of caption will be rendered.
class
    class attribute of the HTML figure tag.
height
    height attribute of the image.
width
    width attribute of the image.
attr
    Image attribution text. Markdown within the value of attr will be rendered.
attrlink
    If the attribution text needs to be hyperlinked, URL of the destination.

Example figure Input
figure-input-example.md

{{< figure src="/images/screenshot-o-b.png" title="Steve Francia" >}}

Example figure Output
figure-output-example.html

{{< highlight html>}}
<figure>
  <img src="/images/rfi-homepage.png"  />
  <figcaption>
      <h4>Steve Francia</h4>
  </figcaption>
</figure>
{{< /highlight >}}
