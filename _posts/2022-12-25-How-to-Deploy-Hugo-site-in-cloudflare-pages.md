---
author: Piragenth
title: "How to Deploy a Hugo Site on Cloudflare Pages"
date: 2022-12-25T07:15:52+05:30
suggestion: false
---


![](https://linuxtutorialforbeginners.com/assets/Pictures/hugo-cloudflare-pages.png)

# Introduction to the Cloudflare site

Cloudflare Pages is a static page hosting service offered by Cloudflare. It is designed to make it easier for developers to host and manage their static websites, including those created with the Hugo static website generator.

One of the benefits of using Cloudflare sites is that they integrate seamlessly with Cloudflare's global content delivery network (CDN), meaning your site will be served quickly and securely to users around the world. It also has a number of other features, such as automatic management of SSL certificates and support for custom domains.

In this tutorial, we'll walk through the process of deploying a Hugo site to Cloudflare Pages. We will cover the following topics:

- Setting up a Cloudflare account and creating a Cloudflare Pages website
- Setting up a Git repository for your Hugo site
- Creating and deploying your Hugo site to Cloudflare Pages

## Setting up a Cloudflare account and creating a Cloudflare Pages website

![](https://linuxtutorialforbeginners.com/assets/Pictures/cloudflare-home.png)

The first step in deploying your Hugo site to Cloudflare Pages is to set up a Cloudflare account and create a Cloudflare Pages site. How to do it:

1. Go to [https://www.cloudflare.com/](https://www.cloudflare.com/) and click the "Sign Up" button on the top right corner of the page.

2. Fill out the registration form and enter your email address and password. Then click the "Create Account" button.

3. Check your email for a verification email from Cloudflare and click the link provided to verify your email address.

4. Once your email address is verified, log in to your Cloudflare account and click on the "Sites" tab in the top menu.

5. Click the "Create New Site" button.

6. Enter your website name and select a subdomain. The subdomain will be used as your site's URL, so choose something descriptive and easy to remember. For example, if you choose "mysite" as your subdomain, your website will be accessible at "mysite.pages.dev".

7. Click the "Create Site" button to create your Cloudflare Pages site.

![](https://linuxtutorialforbeginners.com/assets/Pictures/cloudflare-pages.png)

## Setting up a Git repository for your Hugo site

The next step is to set up a Git repository for your Hugo site. Git is a version control system that allows you to track changes to your code and collaborate with other developers.

1. If you don't already have a Git repository for your Hugo site, create a new repository on GitHub or another Git hosting service.

2. Initialize the Git repository on your local machine by running the following commands in the root directory of your Hugo site:

``` bang
git init
git add.
git commit -m "Initial commit"
```


3. Add the remote repository as remote to your local repository by running the following command, replacing "origin" with the URL of your remote repository:

``` bash
git remote add origin <repository-url>
```


## Creating and deploying your Hugo site to Cloudflare Pages

Now that you have a Cloudflare Pages site and a Git repository, you're ready to build and deploy your Hugo site.

1. Create your Hugo site by running the following command in the root directory of your Hugo site:

``` bash
hugo
```

With Cloudflare Pages and your Git repository setup, you're ready to build and deploy your Hugo site.

1. Create your Hugo site by running the following command in the root directory of your Hugo site:

``` bash
git add public
git commit -m "Create site"
```



3. Push the changes to the remote repository by running the following command:

``` bash
git push origin master
```


4. Return to the Cloudflare Pages dashboard and click the "Connect Git Provider" button.

5. Select the Git provider you are using (eg GitHub) and follow the instructions to authorize Cloudflare to access your repository.

6. Once your storage is connected, select it from the drop-down menu and click the "Connect" button.

7. In the "Branch to Deploy" field, enter the name of the branch you want to deploy (e.g. "main").

8. Click the "Deploy" button to deploy your website.

It may take a few minutes for your site to load and be available at the URL you entered earlier (eg "mysite.pages.dev").

## Conclusion

In this tutorial, we walked through the process of deploying Hugo to Cloudflare Pages. We have covered the following steps:

- Setting up a Cloudflare account and creating a Cloudflare Pages website
- Setting up a Git repository for your Hugo site
- Creating and deploying your Hugo site to Cloudflare Pages

With these steps, you should now be able to easily deploy your Hugo site to Cloudflare sites and take advantage of the fast and secure hosting provided by Cloudflare's global CDN.

I hope you found this tutorial helpful! If you have any questions or need further assistance, please do not hesitate to contact us.