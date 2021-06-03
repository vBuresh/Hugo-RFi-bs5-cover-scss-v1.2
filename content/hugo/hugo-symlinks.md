---
title: Symlinks
# subtitle: continuer of the title in a two words
date: 2020-09-01T14:16:29+03:00
Lastmod: 2020-09-01T14:16:29+03:00
draft: false
# description: "- дополнение к заголовку (подзаголовок)"
# summary: краткое изложение - зачем читать сие
# summaryImage: images/
author:
  given_name: Vladimir
  family_name: Buresh
  display_name: wBuresh
categories:
  - Hugo
tags:
- webDev
---

[Symbolic Links suddenly stopped](https://discourse.gohugo.io/t/symbolic-links-suddenly-stopped-from-version-v0-56-0/19878/2) (from version v0.56.0)

{{< bQuote >}}
<h4>Notes</h4>
<ul>
<li>We have removed the “auto theme namespacing” of params from theme configuration. This was an undocumented and hidden feature that wasn’t useful in practice.
<ul>
<li>We have revised and improved the symlinks support in Hugo: In earlier versions, symlinks were only fully supported for the content folders. With the introduction of the new very flexible file mounts, with content support even for what we have traditionally named “themes”, we needed a more precise definition of symlink support in Hugo:</li>
<li>Symlinks are not supported outside of the main project ((the project you run hugo or hugo server from).</li>
<li>In the main project static mounts, only symlinks to files are supported.</li>
<li>In all other mounts in the main project, both file and directory symlinks are allowed.</li>
</ul>
</li>
</ul>

<footer class="blockquote-footer text-right font-italic pt-3">
Bjørn Erik Pedersen: See
<a href="https://gohugo.io/news/0.56.0-relnotes#notes">Hugo 0.56.0, Notes</a>
</footer>
{{< /bQuote >}}

The short version:

{{< bQuote >}}
<ul>
<li>The overall symlink support is much improved.</li>
<li>But it’s more restrictive for themes (for security and … practial reason; symlinks are hard to reason about, and even harder when you reason about some other person’s symlinks)</li>
<li>You now have a powerful mounts feature that can do most of what the old symlinks hacks can do.</li>
</ul>
<footer class="blockquote-footer text-right font-italic pt-3 mb-0">
Bjørn Erik Pedersen
<a href="https://discourse.gohugo.io/t/symbolic-links-suddenly-stopped-from-version-v0-56-0/19878/2">The short version</a>
</footer>
{{< /bQuote >}}
