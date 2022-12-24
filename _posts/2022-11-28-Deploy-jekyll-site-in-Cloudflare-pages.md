---
title: "Deploy Jekyll Site in Cloudflare Pages"
date: 2022-11-28T14:56:35+05:30
draft: false
categories:
- Linux
- website
tags:
- jekyll website
- cloudflare pages
---
![jekyll in-Cloudflare page](https://blog.cloudflare.com/content/images/2020/12/Cloudflare-Pages.png)
#  Prerequisite

* Cloudflare free account
* Free GitHub account (optional)
* Jekyll installed on your pc

## Installing jekyll

to create a jekyll site you need to install jekyll first in your pc locally.

```bash
sudo apt install ruby-full build-essential zlib1g-dev
```

Avoid installing RubyGems packages (called gems) as the root user. Instead, set up a gem installation directory for your user account. The following commands will add environment variables to your `~/.bashrc` file to configure the gem installation path:

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Finally, install Jekyll and Bundler:

```bash
gem install jekyll bundler
```

That’s it! You’re ready to start using Jekyll.

For Other distros: [Jekyll](https://jekyllrb.com/docs/installation/)

### create new jekyll site

to create a jekyll site:

```bash 
jekyll new {jekyll-site-name}
```

OR 

**Fork from github theme repo** 

#### Pick up a theme

* [jamstackthemes.dev](https://jamstackthemes.dev)
* [jekyllthemes.org](https://jekllthemes.org)
* [jekyllthemes.io](https://jekyllthemes.io)
* [jekyll-themes.com](https://jekyll-themes.com)

# Deploy jekyll site in cloudflare pages

In order proceed you need to have cloudflare Free account.

After you create cloudflare account follow the steps

![](https://linuxtutorialforbeginners.com/assets/Pictures/cloudflare-home.png)
* click create project 
![](https://linuxtutorialforbeginners.com/assets/Pictures/cloudflare-pages.png)
* Connect Github account 
* Select Forked GitHub repo
* Select The Frameset as Jekyll
![](https://linuxtutorialforbeginners.com/assets/Pictures/cloudflare-jekyll-framset.png)

Click Deploy and the site will be ready 
you can add your custom domain
