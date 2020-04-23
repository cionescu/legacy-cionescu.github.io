---
layout: post
title: Partial index in postgres
date: 2020-04-23
image: /assets/img/til-postgres-indexes.jpg
image_caption: Photo by <a href="https://unsplash.com/@ikukevk" rel="nofollow">Kevin Ku</a> on Unsplash
tags: [today-i-learned, postgresql]
---

## What is a partial index?

> A partial index is an index built over a subset of a table; the subset is defined by a conditional expression (called the predicate of the partial index). The index contains entries for only those table rows that satisfy the predicate.

## Syntax

{% highlight sql %}
  CREATE INDEX [INDEX_NAME] ON [TABLE_NAME] ([COLUMN]) WHERE [CONDITION];
{% endhighlight %}

A partial index is useful when you are dealing with large amounts of data and lots of inserts. Any index takes a toll on insert performance (because indexes must be rebuilt), so a partial index is an ideal improvement.

A real world example:

{% highlight sql %}
  CREATE TABLE public.events (
    id bigint NOT NULL,
    status integer,
    start_at timestamp without time zone NOT NULL,
    end_at timestamp without time zone NOT NULL
  );
{% endhighlight %}

The status is used as an enum:

{% highlight ruby %}
  enum status: {
    pending: 0,
    completed: 1,
    closed: 2
  }
{% endhighlight %}

Since most of our reads will deal with *pending* and *completed* events, we only want to index those:

{% highlight sql %}
  CREATE INDEX idx_events_status_not_closed ON public.events(start_at, end_at) WHERE status <> 2;
{% endhighlight %}
