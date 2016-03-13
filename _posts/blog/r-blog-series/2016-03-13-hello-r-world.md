---
layout: post
title: "Hello ‘R’ World"
description: "Installing R tools and getting familiar with the tool"
modified:
categories: articles
excerpt:
tags: [R Language,R Studio, R Tools]
image:
  feature:
date: 2016-03-13T15:39:55-04:00
comments: true
share: true
---

First of all we need to install the essential tools. There are so many tutorials available to install the tools. The following below videos will help,

* [**Installing R on Windows**](https://www.youtube.com/watch?v=Ohnk9hcxf9M&feature=youtu.be){:target="_blank"}
* [**Installing R on Mac**](https://www.youtube.com/watch?v=uxuuWXU-7UQ&feature=youtu.be){:target="_blank"}

The above installation will provide **_‘R console’_** window (_Figure 1_). But there is a development environment available and its called **_‘RStudio’_**. The RStudio can be downloaded from their [**website**]( https://www.rstudio.com/){:target="_blank"}.

<figure>
  <a href="/blog/r-blog-series/r-console.png"><img src="/blog/r-blog-series/r-console.png" alt="image"></a>
  <figcaption>Figure 1: R Console</figcaption>
</figure>


After you’ve installed the tools, launch R Studio (_Figure 2_).

### The Editor 

We should write our R code in the editor and it’s in the top left corner. The rest of the buttons in the editor is straightforward. This editor is very useful it provides quick intellisense while writing the code and also if we need to install the packages we can use this editor to write code to install new packages.

### Environment & History Tabs

These two tabs are located in top right corner.

* The Environment allows us to see all the list of defined variables or the dataset. This tab is very useful because when we are manipulating the dataset with different variables it allows to keep track all the dataset in each stage. In our implementation flow in a needed situation we can go through the list and use the dataset rather than running the full program.

* History helps to keep track all the executed commands in console. These information will be stored into a hidden folder **_‘.Rhistory’_**

### The Console 

It’s a **_Read Evaluate Print Loop (REPL)_** for R language and it’s in left bottom corner. Using the REPL we can test our code snippets. To get familiar with R language this area is very useful and it provides intellisense too.

### Helper & Visual Tabs

We can find 5 tabs in right bottom corner. 

* The files tab is straightforward, it will show the folder tree structure of your current working folder.  
* The plots tab is used to show the graphs when you execute visualization code. 
* The package tab helps to install the needed packages for our logics. So that you don’t need to write code in console/editor to install the package.
* The help tab allows reading the R Language documents. So once you execute the helper command (_eg: ?data.frame_) it will automatically open the relevant documents in the tab.
* Viewer is a browser built-in RStudio. We can develop web app using R Language and launch it in locally.

<figure>
  <a href="/blog/r-blog-series/r-studio.png"><img src="/blog/r-blog-series/r-studio.png" alt="image"></a>
  <figcaption>Figure 2: R Studio</figcaption>
</figure>

Now that we have an idea about the IDE lets implement a small code. Write the following code in the editor panel Highlight the code snippet and press **_‘Run’_** button in editor panel or mac users press **_‘Command + Enter’_** ([**Keyboard Shortcuts**](
 https://support.rstudio.com/hc/en-us/articles/200711853-Keyboard-Shortcuts){:target="_blank"}).

{% highlight r %}
print("Hello R World :)") # Print the text
hello <- "Hello R World varibale" # Assign a varible
print(hello) # Print
{% endhighlight %}

