---
layout:     post
title:      git diff with one liners
date:       2014-12-02
summary:    Simple way to review one liner changes by git diff
categories: git
---

If you need to review one liners which change just a few bytes, it is helpful to use a proper command:

{% highlight bash %}
git diff --ignore-all-space --word-diff=color  --unified=0 HEAD^1..HEAD
{% endhighlight %}

This will highlight the changes in color and won't show you the lines above and below.