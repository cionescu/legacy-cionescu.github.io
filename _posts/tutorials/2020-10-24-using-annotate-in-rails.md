---
layout: post
title: How to use the Annotate Gem in Rails 6
description: Get a summary of the Active Record schema at the top or bottom of relevant files.
date: 2020-10-24
image: /assets/img/annotate_gem.jpg
image_caption: Using the Annotate Gem in Rails 6
tags: [ruby-on-rails]
---

## Get a summary of the Active Record schema at the top or bottom of relevant files

The annotate gem will add a comment to the top of some selected files describing the database schema relevant for those files — including field names, index configuration and foreign keys.

It will update these comments automatically whenever you run `rails db:migrate`.

---

## Installation
In your Gemfile, you need to add this under the development group

{% highlight ruby %}
  group :development do
    gem 'annotate'
  end
{% endhighlight %}

Make sure to run `bundle` afterwards.

---

## Configuration

{% highlight ruby %}
  bundle exec rails g annotate:install
{% endhighlight %}

This will generate a rake task in `lib/tasks/auto_annotate_models.rake` with the default configuration.

As a personal preference, I always disable annotating the controllers (and controller specs) but keep the annotations for FactoryBot’s factories and models.

[This is the configuration I use.](https://gist.github.com/cionescu/9886248196a1382894e4a2f409ab2fe4)

---

## Route maps

Another cool feature of Annotate is displaying a set of comments at the top of `config/routes.rb`.

This is extremely useful if you find yourself always running the same command to find the route helper for a specific controller/action.

{% highlight bash %}
  bundle exec rails routes | grep user_password
{% endhighlight %}

To set it up, you can manually trigger the annotations using:
bundle exec rails annotate_routes

To make it automatically annotate the routes, change `lib/tasks/auto_annotate_models.rake` and update:

{% highlight ruby %}
  Annotate.set_defaults(
    'routes' => 'true', # was false
    # ...
  )
{% endhighlight %}

The results are pretty great.

![Annotating Routes in Rails 6](/assets/img/annotate_routes.jpg)
