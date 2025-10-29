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
- It's **static**, so it's fast and secure.  
- Easy to **host on GitHub Pages or Cloudflare Pages**.  

## Choosing a Theme

I found a theme I really liked: [hugo-blog-awesome](https://github.com/hugo-sid/hugo-blog-awesome). It's modern, lightweight, and fits my style.

## Setting Up the Site

I followed the steps in the theme's repository.

1. **Create a new Hugo site**:

```bash
hugo new site blog
````

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

## Next Steps

With Hugo set up, the next step is simple: **start making notes and writing posts**!
