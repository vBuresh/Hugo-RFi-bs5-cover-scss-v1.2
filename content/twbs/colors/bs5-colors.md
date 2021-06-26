---
title: Colors
date: 2020-07-21T12:41:45+03:00
Lastmod: 2021-06-13T10:31:45+03:00
draft: false
# summary:
summaryImage: images/colors.png
categories: ['веб-разработка']
tags: ['bootstrap', 'шрифт и цвет']
---

[colors](https://getbootstrap.com/docs/5.0/customize/color/#all-colors)

{{< highlight YAML>}}
:root {
  --bs-blue: #0d6efd;
  --bs-indigo: #6610f2;
  --bs-purple: #6f42c1;
  --bs-pink: #d63384;
  --bs-red: #dc3545;
  --bs-orange: #fd7e14;
  --bs-yellow: #ffc107;
  --bs-green: #28a745;
  --bs-teal: #20c997;
  --bs-cyan: #17a2b8;
  --bs-white: #fff;
  --bs-gray: #6c757d;
  --bs-gray-dark: #343a40;
  --bs-primary: #0d6efd;
  --bs-secondary: #6c757d;
  --bs-success: #28a745;
  --bs-info: #17a2b8;
  --bs-warning: #ffc107;
  --bs-danger: #dc3545;
  --bs-light: #f8f9fa;
  --bs-dark: #343a40;
  --bs-font-sans-serif: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  --bs-font-monospace: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
  --bs-gradient: linear-gradient(180deg, rgba(255, 255, 255, 0.15), rgba(255, 255, 255, 0));
}
{{< /highlight >}}

## Color

Colorize text with color utilities. If you want to colorize links, you can use the helper classes which have `:hover` and `:focus` states.


{{< highlight go-html-template >}}
{{< colored-links.inline >}}
{{- range (index $.Site.Data "theme-colors") }}
<a href="#" class="link-{{ .name }}">{{ .name | title }} link</a>
{{- end -}}
{{< /colored-links.inline >}}
{{< /highlight >}}

Пример

{{< highlight go-html-template >}}
{{< colors.inline >}}
{{- range (index $.Site.Data "theme-colors") }}
<p class="text-{{ .name }}{{ if or (eq .name "light") (eq .name "warning") (eq .name "info") }} bg-dark{{ end }}">.text-{{ .name }}</p>
{{- end -}}
{{< /colors.inline >}}
<p class="text-body">.text-body</p>
<p class="text-muted">.text-muted</p>
<p class="text-white bg-dark">.text-white</p>
<p class="text-black-50">.text-black-50</p>
<p class="text-white-50 bg-dark">.text-white-50</p>
{{< /highlight >}}

## Background color

Similar to the contextual text color classes, easily set the background of an element to any contextual class. Background utilities **do not set `color`**, so in some cases you'll want to use `.text-*` utilities.

{{< highlight go-html-template >}}
{{< colors.inline >}}
{{- range (index $.Site.Data "theme-colors") }}
<div class="p-3 mb-2 bg-{{ .name }} {{ if or (eq .name "light") (eq .name "warning") }}text-dark{{ else if (eq .name "info") }}text-body{{ else }}text-white{{ end }}">.bg-{{ .name }}</div>
{{- end -}}
{{< /colors.inline >}}
<div class="p-3 mb-2 bg-white text-dark">.bg-white</div>
<div class="p-3 mb-2 bg-transparent text-dark">.bg-transparent</div>
{{< /highlight >}}

## Background gradient

By adding a `.bg-gradient` class, a linear gradient is added as background image to the backgrounds. This gradient starts with a semi-transparent white which fades out to the bottom.

Do you need a gradient in your custom CSS? Just add `background-image: var(--bs-gradient);`.

{{< highlight  go-html-template >}}
{{< colors.inline >}}
{{- range (index $.Site.Data "theme-colors") }}
<div class="p-3 mb-2 bg-{{ .name }} bg-gradient {{ if or (eq .name "light") (eq .name "warning") }}text-dark{{ else }}text-white{{ end }}">.bg-{{ .name }}.bg-gradient</div>
{{- end -}}
{{< /colors.inline >}}
{{< /highlight >}}
