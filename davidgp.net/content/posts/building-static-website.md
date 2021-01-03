---
title: "Building Static Website"
date: 2021-01-02T18:10:04+01:00
draft: false
categories:
- Hugo
tags:
- Hugo
- Cloudflare
- Github Actions
- Google Cloud
- Web
- Hosting
---

Until now I was building all my personal websites using [Wordpress][1] and personally hosting everything on my own web server. For some months now, I wanted something simplier to maintain. So I have decided to switch to [Hugo][2], a static website generator. This posts starts a series of articles how I have setup everything to automate the whole process.

<!--more-->

## Tools

My idea of setting everything up is based in the following article: "[Tobias Schwarz - Static Website with Hugo, Cloudflare and Automated Builds using Google Cloud][3]", but with some differences, mainly using [Github Actions][4] instead of Google Cloud tools and [Terraform][5] to automate all infrastructure aspects.

The complete list of tools:
* [Github for code repository][6].
* [Terraform][5] to automate the infrastructure deployment.
* [Google Cloud Storage][7] to store the website pages.
* [Github actions][4] for automatically publish new updates to the blog.
* [Cloudflare][8] for SSL and CDN.

Consider that of the previous tools, depending on the usage [Github Actions][4] you maybe need to pay for it. [Cloudflare][8] was selected since they offer a free plan for personal webpages like this one. For the object storage, in this case [Gloogle Cloud Storage][7], you will need to pay for it, how much? It will depend on the size of your website and the traffic to it (although the usage of [Cloudflare as CDN][8] should mitigate part of the costs).

## Steps

### Create the repository

You will need a [Github][9] account. Once registered you will need to create a repository, you can follow [these instructions][10] if necessary.

### Create the Hugo website

Not an expert in [Hugo][2], I just know the basic to build this site without too much aspirations to become an expert. I just wanted something simple and this works. The steps detailed now are basically the ones explained in the [Hugo Quick Start Guide][11]. As a side note, I'm creating this as a subfolder in my repository, other folders will contain the rest of the code explained here, that maybe it is not the best idea.

Inside the new repository I just executed:

```sh
hugo new site davidgp.net
```

Installed the [PaperMod Hugo Theme][12]:

```sh
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/hugo-PaperMod
git submodule update --init --recursive
```

I just adapted the [config file in their installation guide to my needs][13].

Note: Maybe right now I have switched to a different theme or heavily modified this one from the defualt configuration. If you are curious, everything is publicly available in my own [repository for this webpage][6].


[1]: https://wordpress.org
[2]: https://gohugo.io
[3]: https://www.tobias-schwarz.com/en/posts/8/
[4]: https://github.com/features/actions
[5]: https://www.terraform.io/
[6]: https://github.com/davidgp1701/davidgp.net
[7]: https://cloud.google.com/storage
[8]: https://www.cloudflare.com/plans/
[9]: https://github.com/
[10]: https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/create-a-repo
[11]: https://gohugo.io/getting-started/quick-start/
[12]: https://github.com/adityatelange/hugo-PaperMod
[13]: https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/
