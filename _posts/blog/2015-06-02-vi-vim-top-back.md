---
layout: post
title: "vi / vim Editor: Jump to the end of the file and back to top"
description: "vi / vim Editor: Jump to the end of the file and back to top"
category: blog
tags: [vim, vi, Unix]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

Unix operating system users mostly spend their time with vi/vim editors where we might to deal with large configuration file / code file. In this situation to reach the end and top you can save lot of time by using appropriate movement commands in vi and vim editors. It will really help you a lot.

To display and hide the line numbers enter the following command:

{% highlight bash %}
set number 
set nonumber
{% endhighlight %}

To move to the end of the file enter the following command (Press ESC and type capital ‘G’):

{% highlight bash %}
G
{% endhighlight %}

To jump back to the beginning of the file enter the following command (Press ESC and type simple 'gg'):

{% highlight bash %}
gg
{% endhighlight %}

Or

{% highlight bash %}
1G
{% endhighlight %}

To reach 200th line enter the following command (Press ESC and type):

{% highlight bash %}
200G
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/vi-vim-top-end.gif"><img src="/blog/vi-vim-top-end.gif" alt="image"></a>
  <figcaption>Figure 1 - vi/vim command demo </figcaption>
</figure>


