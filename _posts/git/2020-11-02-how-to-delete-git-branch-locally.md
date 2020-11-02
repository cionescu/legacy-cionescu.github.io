---
layout: post
title: How to Delete a Git Branch Locally?
date: 2020-11-02
image:
image_caption:
permalink: how-to-delete-git-branch-locally
tags: [git]
---

## You can delete a Git Branch using the `-d` option

{% highlight bash %}
  $ git branch -d <branch_name>
{% endhighlight %}

## According to the Git documentation, `-d` is the shorthand for `--delete`, so both options are acceptable.

{% highlight bash %}
  $ git branch --delete <branch_name>
{% endhighlight %}

## If you want to delete the branch irrespective of the merged status, use the `-D` option

{% highlight bash %}
  $ git branch -D <branch_name>
{% endhighlight %}

## Here's the complete Git documentation about deleting branches

```
OPTIONS
       -d, --delete
           Delete a branch. The branch must be fully merged in its upstream branch, or in HEAD if no upstream was set with --track or --set-upstream-to.

       -D
           Shortcut for --delete --force.

       -f, --force
           In combination with -d (or --delete), allow deleting the branch irrespective of its merged status.
```
