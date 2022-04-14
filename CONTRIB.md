# Contribution Guidelines

This document is meant to be used as a guide for anyone interested in contributing to T-Mobile Opensource Website. We are always interested and are on the lookout for folks who are open and willing to write technical articles.

## Prerequisites

- hugo CLI
- git CLI
- Text Editor (Visual Studio Code, NotePad++, etc.)

## Add a Blog Post

Blog posts are stored in the `/content/blog/posts` directory in this repo.

Create a new file like `/content/blog/posts/my-cool-new-post.md`

The syntax is basic markdown, but you will need to add some Hugo specific metadata at the top of the file, similar to this:

```markdown
---
title: "My Cool Blog Post: Some Amazing Title!"
date: 2020-05-01T01:00:00-04:00
draft: false
tags: ["oss", "t-mobile", "cool", "stuff"]
categories: ["resources"]
author: "FirstName LastName"
---
```

You can set the `draft` field to `true` while you're working on it locally....[preview with drafts enabled](#generate-static-site-assets-with-drafts-enabled), and then toggle it to `false` when you're ready to publish.

### Add an Image for a Blog Post

To add an image to your blog post, you just need to use normal markdown syntax.

If you're adding an image that's not already on the web somewhere, you'll need to add the image (standard jpeg/png formats should work) in the `/themes/tmo-oss-theme/static/blog` directory. It's usually good to create a new directory corresponding to your blog post (ie. `/themes/tmo-oss-theme/static/blog/my-cool-blog-post`) and add your images there for better identification/organization.

One your file has been added, you can use markdown syntax like this:

```markdown
![my-cool-image](/blog/my-cool-blog-post/my-cool-image.png)
```

## Add a Project

If you're open sourcing a project, add a project definition to have it included on the site.

Add a project specific file to the `/data/projects` directory similar to `/data/projects/my-cool-project.yml`

The contents should look similar to this:

```
name: MagTape
full_name: tmobile/magtape
description: Kubernetes Policy as Code
url: https://github.com/tmobile/magtape
img: "foo.png"
language: "Python"
css: ""
order: 21

```

Order is sort of manual, but we try to base it on number of github stars. So when you first add your project, assuming no or low Github Stars, just find the current largest order index, +1, and use that. Over time if your project gains momentum and gets popular, we can reorder it.

## Preview Site Locally

### Install Hugo

Follow instructions on [http://gohugo.io]([http://gohugo.io) to install Hugo

### Generate Static Site Assets

```shell
$ hugo --cleanDestinationDir --config ./config-public.toml
```

#### Generate Static Site Assets with Drafts Enabled

```shell
$ hugo --buildDrafts --cleanDestinationDir --config ./config-public.toml
```

### Serve the Site Locally

```shell
hugo server
```

## Publishing the Site

The site is hosted via Github Pages and is served from the `/public` directory on the `main` branch of this repo.

The CI for this repo will generate the `/public` directory fresh on each run, you should NOT commit this directory when you add content.

PR's merged to `main` will be reflected on the public site upon merge.

Future tooling will hopefully provide previews for code in open PR's, but for now, preview locally.
