---
layout: post
title: How to install Ruby on Rails 6 on MacOS Catalina?
description: I will walk you through installing Ruby on Rails for development on macOS 10.15 Catalina.
date: 2020-11-05
image: /assets/img/install_rails_mac.png
image_caption: Photo by <a href="https://2.flexiple.com/scale/all-illustrations" rel="nofollow">Flexiple</a>.
permalink: how-to-install-ruby-on-rails-on-macos-catalina
tags: [ruby-on-rails]
---

## Overview

In this tutorial we'll be setting up Ruby on Rails 6.0 for development using macOS 10.15 Catalina.

---

## Use oh-my-zsh

This will change your terminal from Bash to ZSH. You'll thank me later:

{% highlight bash %}
  $ sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
{% endhighlight %}

_Read more about oh-my-zsh [here](https://github.com/ohmyzsh/ohmyzsh)._

---

## Installing Homebrew

Homebrew allows us to install packages from source on macOS.

{% highlight bash %}
  $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

_Read more about installing Homebrew [here](https://brew.sh/)._

---

## Installing rbenv

We'll be using **rbenv** for installing Rubies and managing Ruby versions.

{% highlight bash %}
  $ brew install rbenv ruby-build
{% endhighlight %}

We'll then add rbenv to zshrc so that it loads every time a new session (terminal) is opened.

{% highlight bash %}
  $ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.zshrc
  $ source ~/.zshrc
{% endhighlight %}

---

## Install Ruby 2.7.2

We will use Ruby 2.7.2 (latest release as of November 2020) and manage our Ruby versions using rbenv.

{% highlight bash %}
  $ rbenv install 2.7.2
  $ rbenv global 2.7.2
{% endhighlight %}

---

## Installing Ruby and Rails

As of November 2020, the latest Rails version is 6.0.3.4.

{% highlight bash %}
  $ gem install rails -v 6.0.3.4
{% endhighlight %}

---

## Create a new Rails 6 Application with PostgreSQL and React

{% highlight bash %}
  $ rails new my-app —database=postgresql —webpack=react
{% endhighlight %}

---

## Create the development and test databases

{% highlight bash %}
  $ cd my-app; bin/rails db:create
{% endhighlight %}

You can now visit [http://localhost:3000](http://localhost:3000) to view your new website!
