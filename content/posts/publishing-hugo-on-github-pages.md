---
title: "Publishing Hugo on Github Pages"
date: 2021-04-13T22:40:27+02:00
draft: false
---

## Own scripts, Wordpress, Jekyll... Hugo!

I had this idea of having my own blog for many years. I always wanted to write about programming - something I do everyday for many years now.

My first attempt was to create a blog using PHP/HTML/CSS/JS from scratch. But I quickly realised this is a lot of work. I wanted my blog to be responsive and easy to maintain. 

My second attempt was installing Wordpress on some basic hosting platform with custom domain. It was better as I didn't have to spend much time on writing the code and there is huge range of free and responsive themes. Disadvantage is that you have to pay for domain and hosting. Also I don't really like Wordpress (after spending too much time working with it) and when you start installing plugins it gets tricky to make everything working with your theme of choice so you still end up with a lot of manual work.

So another try was Jekyll. First static site generator (SSG) I ever used. It is great to work with, clean docs, plenty of themes and exactly what I needed as I could use GitHub Pages to host my blog for free (I don't mind github.io subdomain).
The only problem with Jekyll I had was - it is written in Ruby and I don't really have any experience with Ruby ecosystem. So I gave up when I had to setup my Ruby environment and encountered some gem related issues.

Finally I stumbled upon Hugo. When I read it is written in Go, I already knew it is going to be pleasant to use (in Go you usually get a single binary and don't need any extra dependencies in your system). And it indeed was super easy to install and start with. Let's have a look!

## Quick setup

You download a binary from https://github.com/gohugoio/hugo/releases. In my case it was hugo_0.82.0_Linux-64bit.tar.gz as I use Ubuntu on 64 bit processor. Once you extracted hugo binary, you can place it in ~/.local/bin/hugo so it can be executed from any place in your terminal.

You can also confirm if it works by calling version command:

	$ hugo version  
	hugo v0.82.0-9D960784 linux/amd64 BuildDate=2021-03-21T17:28:04Z VendorInfo=gohugoio

## Create a blog

Creating a blog is super simple as it takes only few commands to run. No dependencies needed at all (comparing to Jekyll).
The command below will create a new folder named "yourname.github.io" with a default project structure inside:

    $ hugo new site yourname.github.io

Before we move next, it is important to update some configuration and set a theme. In our case we will go with ananke theme which is suggested by Hugo docs as a basic default. Preferred way to add a theme is to use git submodule. It will make it easier to keep the theme up to date. To fetch ananke theme go inside yourname.github.io directory and run command below:

    $ git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke

Now, open config.toml file in your favourite text editor and update values with your preference. You need to manually add theme and publishDir. Publish directory is set to "public" by default, but we are going to change it to "docs" so we can use it later on Github Pages. We will cover it in next paragraph.
My config.toml looks like this:

    baseURL = "https://barell.github.io/"
    languageCode = "en-gb"
    title = "barell's notes"
    theme = "ananke"
    publishDir = "docs"

Next step is to create very first blog post, in the end this is all about blogging! You can run command below to generate new md file with some prepared meta data:

    $ hugo new posts/my-first-post.md

Markdown (md) files are created within content directory. If you are not familiar with markdown syntax, don't worry, there are a lot of great docs online.
Once you edited my-first-post.md file in a text editor and added some content, you can view your blog on your computer before publishing. Simply run command below to start a local server:

    $ hugo server -D

Your blog should be accessible on http://localhost:1313/.
At this point you actually generated a static site already which sits in docs directory we set in config.toml file. If you don't want to start a server and only build the site, run command below:

    $ hugo -D

## Publish on Github Pages

We now have our blog generated on our computer but now it is time to publish it online. I'm going to show how to do it on Github Pages.
I assume that you already have Github account with a created empty repository called "yourname.github.io". 

In your blog directory initialize git and push it to your Github:

    $ git init
    $ git remote add origin git@github.com:yourname/yourname.github.io.git
    $ git add . 
    $ git commit -m "Publish blog"
    $ git push -u origin master

On Github itself, you also need to go to repository settings and scroll down to Pages section. Then select master branch and "/docs" directory as source.

Once this is saved, you should see your blog online shortly on https://yourname.github.io/. In my case it was few minutes.

That's it. As you can see the whole process is smooth and painless. As a happy Hugo user I will certainly recommend it to everyone!