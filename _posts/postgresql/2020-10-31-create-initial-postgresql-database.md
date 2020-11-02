---
layout: post
title: How to Create the Initial Postgresql Database?
description: "You've just installed PostgreSQL and attempt to run psql and get the following error: FATAL:  database 'user' does not exist. Here's how to fix that"
date: 2020-10-31
image:
image_caption:
permalink: create-initial-postgresql-database
tags: [postgresql]
---

## How to Install PostgreSQL

You can use **brew** to install PostgreSQL:

{% highlight bash %}
  $ brew install postgresql
{% endhighlight %}

## Start the process

You can use brew services to manage your processes like this:

{% highlight bash %}
  $ brew services start postgresql
{% endhighlight %}

## Create the initial database

If you try starting the PostgreSQL console (using `psql`) and get the following error:

```
  psql: error: could not connect to server: FATAL:  database "user" does not exist
```

then you need to create the initial database using:

{% highlight bash %}
  $ createdb
{% endhighlight %}
