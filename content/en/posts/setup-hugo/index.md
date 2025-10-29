Here’s an updated version of your blog post with the GitHub Pages deployment steps included:

---

+++
date    = '2025-10-29T14:08:41+01:00'
draft   = false
title   = 'Setting Up My Hugo Blog'
author  = "Mike Tuntelder"
toc     = false
+++

I recently decided to start a blog and chose **Hugo** as my platform. Here's how I got it up and running.

---

![Banner](hugo.png)

## Why Hugo?

After some research, I liked Hugo for a few reasons:

* It's **static**, so it's fast and secure.
* Easy to **host on GitHub Pages or Cloudflare Pages**.

## Choosing a Theme

I found a theme I really liked: [hugo-blog-awesome](https://github.com/hugo-sid/hugo-blog-awesome). It's modern, lightweight, and fits my style.

## Setting Up the Site

I followed the steps in the theme's repository.

1. **Create a new Hugo site**:

```bash
hugo new site blog
```

2. **Add the theme as a Git submodule**:

```bash
cd blog
git clone https://github.com/hugo-sid/hugo-blog-awesome.git themes/hugo-blog-awesome
```

3. **Configure the site to use the theme**:

```bash
Copy-Item .\themes\hugo-blog-awesome\exampleSite\hugo.toml hugo.toml
```

And edit where needed.

## Cleaning Up

I cleaned up the directories to get a clean starting structure:

```
blog\
    archetypes
    assets
    content
        en
            pages
            posts
    public
    resources
    themes
    hugo.toml
```

## Deploying to GitHub Pages

To make my blog live, I used **GitHub Pages**:

1. **Create a GitHub Actions workflow**:
   I added `blog\.github\workflows\hugo.yaml` to automatically build the site on every push:

```yaml
name: Hugo Build and Deploy
on:
  push:
    branches:
      - main
jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: '0.116.0'
      - name: Build
        run: hugo --minify
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

2. **Configure GitHub Pages**:

   * Go to **Settings → Pages**.
   * Set a **custom domain** and enable **enforce HTTPS**.

3. **Update DNS**:
   In my domain’s DNS settings, I added these A records pointing to GitHub Pages:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
4. **Running the action manually**:

    Go to Actions, "Deploy Hugo site to Pages", select run workflow and click the green run workflow button.
    
## Next Steps...

With Hugo set up and deployed, the next step is simple: **start making notes and writing posts**!

