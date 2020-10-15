---
layout: post
title: Implicit Declaration of Function is Invalid in C99
description: I ran into this error when installing the thin Ruby Gem on MacOS and found the solution.
date: 2020-10-12
image: /assets/img/til-implicit-declaration-of-function.jpg
image_caption: Photo by <a href="https://unsplash.com/@maxchen2k">Max Chen</a>
tags: [today-i-learned]
---

## Implicit Declaration of Function is Invalid in C99

If you get the following error when attempting to install the thin gem on MacOS (`gem install thin`):

{% highlight bash %}
Fetching thin-1.7.2.gem
Building native extensions. This could take a while...
ERROR:  Error installing thin:
	ERROR: Failed to build gem native extension.

[Omitted for brevity]

thin.c:374:10: error: implicit declaration of function 'thin_http_parser_is_finished' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
  return thin_http_parser_is_finished(http) ? Qtrue : Qfalse;
         ^
9 errors generated.
make: *** [thin.o] Error 1
{% endhighlight %}

## The solution:

Install the gem with the following C flags:

{% highlight bash %}
gem install thin -- --with-cflags="-Wno-error=implicit-function-declaration"
{% endhighlight %}

## Same solution works if you are trying to install `mailcatcher`

{% highlight bash %}
gem install mailcatcher -- --with-cflags="-Wno-error=implicit-function-declaration"
{% endhighlight %}

### Credits for the solution:

[Mike Szyndel on Github](https://github.com/macournoyer/thin/issues/365#issuecomment-692063842)
