---
layout: post
title: Git Checkout Remote Branch
date: 2020-12-22
image:
image_caption:
permalink: git-checkout-remote-branch
tags: [git]
---

## With Git versions ≥ 1.6.6, with only one remote, you can do:

{% highlight bash %}
  $ git fetch
  $ git checkout <branch_name>
{% endhighlight %}

## If you have multiple remotes:

{% highlight bash %}
  $ git checkout -b <branch_name> <remote>/<branch_name>
{% endhighlight %}
