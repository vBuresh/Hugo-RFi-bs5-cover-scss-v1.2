---
title: "Шорткоды и команды Hugo"
date: 2019-10-29T16:06:37+03:00
draft: true
---

## Deploy Your Website

See: [Deploy Your Website](https://gohugo.io/getting-started/usage/#deploy-your-website)

After running **hugo** server for local web development, you need to do a final **hugo** run without the server part of the command to rebuild your site. You may then deploy your site by copying the `public/` directory to your production web server.

Since Hugo generates a static website, your site can be hosted anywhere using any web server. See Hosting and Deployment for methods for hosting and automating deployments contributed by the Hugo community.

Running **hugo** does not remove generated files before building. This means that you should delete your `public/` directory (or the publish directory you specified via flag or configuration file) before running the **hugo** command. If you do not remove these files, you run the risk of the wrong files (e.g., drafts or future posts) being left in the generated site.
Dev vs Deploy Destinations

Hugo does not remove generated files before building. An easy workaround is to use different directories for development and production.

To start a server that builds draft content (helpful for editing), you can specify a different destination; e.g., a dev/ directory:

```bash
hugo server -wDs ~/Code/hugo/docs -d dev
```

When the content is ready for publishing, use the default public/ dir:

```bash
hugo -s ~/Code/hugo/docs
```

This prevents draft content from accidentally becoming available.

```bash
hugo new cite
```

To create a new website in Hugo, you can use the following command:

```bash
hugo new site hugo-RFi-bs5cover --format yaml
```
