---
layout: post
title: "Installing Color Scheme For Vim Editor"
description: "Installing Color Scheme For Vim Editor"
category: blog
tags: [vim, mac,linux]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

You’re a busy programmer? All the day looking at default color scheme of vim editor and getting bored?

> With the new day comes new strength and new thoughts. - Eleanor Roosevelt

You can install **new color schemes** for vim editor as you want and then you can switch between them. It can be done with in few seconds ☺. 

**Figure 1** shows default color scheme and without syntax highlight in the terminal.

<figure style="text-align: center;">
  <a href="/blog/default-syntax-off.png"><img src="/blog/default-syntax-off.png" alt="image"></a>
  <figcaption>Figure 1 - default color scheme</figcaption>
</figure>

### Turn on the syntax highlight 

Edit the file **“~/.vimrc”**. Create the file if not exists **“touch ~/.vimrc”**. Then in side the file type **“syntax on”**.

**Figure 2** shows default syntax highlight in the terminal.

<figure style="text-align: center;">
  <a href="/blog/default-syntax-on.png"><img src="/blog/default-syntax-on.png" alt="image"></a>
  <figcaption>Figure 2 - syntax on</figcaption>
</figure>

### Installing new Color Scheme for Vim

Lets try to install a new Vim color scheme – [**“distinguished”**](https://github.com/Lokaltog/vim-distinguished){:target="_blank"}. Download the color scheme from git repository.

Navigate to **“~/.vim/colors/”** in the root directory. Create **"colors"** folder if not exists. Now move the **"distinguished.vim"** file inside **“~/.vim/colors/”** directory.

Now again edit the file **“~/.vimrc”** and add the following lines.

{% highlight bash %}
syntax on 
colorscheme distinguished
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/distinguish-syntax-on.png"><img src="/blog/distinguish-syntax-on.png" alt="image"></a>
  <figcaption>Figure 3 - distinguish color scheme</figcaption>
</figure>

That’s it, when you open the Vim editor next time it will apply the new color scheme (**Figure 3**).

To switch between different color scheme in Vim editor(**Figure 4**), switch to command mode (by pressing “esc” key, and type :colorscheme default/new_color_scheme(distinguished)

<figure style="text-align: center;">
  <a href="/blog/color-scheme.png"><img src="/blog/color-scheme.png" alt="image"></a>
  <figcaption>Figure 4 - change color scheme</figcaption>
</figure>

