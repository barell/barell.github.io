---
title: "Installing Hugo"
date: 2021-04-13T22:40:27+02:00
draft: true
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

You can also confirm it works by calling version command:

	$ hugo version  
	hugo v0.82.0-9D960784 linux/amd64 BuildDate=2021-03-21T17:28:04Z VendorInfo=gohugoio

