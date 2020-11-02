---
layout: post
title: How to Install a Specific Version of a Ruby Gem?
description:
date: 2020-10-30
image:
image_caption:
permalink: how-to-install-specific-version-ruby-gem
tags: [ruby]
---

### You can use the `-v` flag

{% highlight bash %}
  $ gem install GEM_NAME -v VERSION_NAME
{% endhighlight %}

### You can also use the longer `--version` flag

{% highlight bash %}
  $ gem install GEM_NAME --version VERSION_NAME
{% endhighlight %}

### See all the gem CLI options with `gem --help`

```
  RubyGems is a sophisticated package manager for Ruby.  This is a
  basic help message containing pointers to more information.

  Usage:
    gem -h/--help
    gem -v/--version
    gem command [arguments...] [options...]

  Examples:
    gem install rake
    gem list --local
    gem build package.gemspec
    gem help install

  Further help:
    gem help commands            list all 'gem' commands
    gem help examples            show some examples of usage
    gem help gem_dependencies    gem dependencies file guide
    gem help platforms           gem platforms guide
    gem help <COMMAND>           show help on COMMAND
                                   (e.g. 'gem help install')
    gem server                   present a web page at
                                 http://localhost:8808/
                                 with info about installed gems
```
