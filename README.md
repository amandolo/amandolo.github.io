# Andrea Mandolo - Introduction Site
[![build](https://github.com/amandolo/amandolo.github.io/actions/workflows/build.yml/badge.svg?branch=main)](https://github.com/amandolo/amandolo.github.io/actions/workflows/main.yml) [![pages-build-deployment](https://github.com/amandolo/amandolo.github.io/actions/workflows/pages/pages-build-deployment/badge.svg?branch=public)](https://github.com/amandolo/amandolo.github.io/actions/workflows/pages/pages-build-deployment)


This repository contains my introduction in GoHugo and my resume in the format [jsonresume](https://jsonresume.org/).

The site is hosted on GitHub Pages at <a href="https://andrea.mandolo.net/" target="_blank" />https://andrea.mandolo.net/ </a>

# Introduction site

## Generate files

All resume files are inside the `site` folder.
Use the following build command to create all static assets for the site.  

```
make generate
```

## Develop with live rendering

Use the following command to create a container serving the site at `http://localhost:1313`.

```
make dev
```

# Resume

## Generate files

All resume files are inside the `resume` folder.
Use the following build command to create `build/resume.pdf` and `build/resume.html`. Some themes do not go well with pdf exporting, as
it is done with chromium headless browser. Openning a local server and pressing `Print` in Chrome generally works better.

```
make generate
```

## Develop with live rendering

Use the following command to create a container serving the resume with the specified theme at `http://localhost:4000`.
This page can be printed or save as a PDF.

```
make dev
```

## General observations
1. Only themes in the specific format are installed, that is `jsonresume-theme-*`
2. Some themes fail to generate the server or the pdf (shrug)
3. Some themes are old and contain different json keyworks like `website` instead of `url`, few of them actually do everything right


## Themes

You can find other available themes at https://jsonresume.org/themes/
To change theme you have to edit variable THEME in the `Makefile`.