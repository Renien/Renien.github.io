---
layout: post
title: "Functions in R"
description: "We need functions to avoid the repetitive same few lines of code. "
modified:
categories: blog
excerpt:
tags: [R Language,Data]
image:
  feature:
date: 2016-04-05T15:39:55-04:00
comments: true
share: true
---

We need _functions_ to avoid the repetitive same few lines of code. 

> R functions are treated much like any other R objects.

Like in JavaScript language the functions can be passed as arguments and it can be nested too. The functions are defined using the **_function()_** directive.

{% highlight sh %}
> func <- function(){
+   ## Body of the function [empty]
+ }
> class(func) ## Identify the class type
[1] "function"
> func() ## Execute the function
NULL
{% endhighlight %}

**_function arguments_** are another important option for a function.

{% highlight sh %}
> func <- function(num){ ## pass the num argument
+   for (c in num) {
+     cat("function reduces the # of code\n")
+   }
+ }
> func(1:3) ## Execute the function
function reduces the # of code
function reduces the # of code
function reduces the # of code
{% endhighlight %}

We can modify our code a bit by setting a **_default value_** for the arguments. Therefore we can call the function without passing any argument value to the interface.

{% highlight sh %}
> func() ## Execute the function
Error in func() : argument "num" is missing, with no default

> func <- function(num=1:2){ ## pass the num arguments
+   for (c in num) {
+     cat("function reduces the # of code\n")
+   }
+ }
> func() ## Execute the function
function reduces the # of code
function reduces the # of code
{% endhighlight %}

### Lazy Evaluation

Function arguments are evaluated **_lazily_**. The below code example clearly explains it.

{% highlight sh %}
> add <- function(a, b){ ## Evaluated lazily
+   cat(a) 
+ }
> add(3) ## Passing one argument value
3
{% endhighlight %}

When both arguments are used in the body then R will check for the next argument too.

{% highlight sh %}
> add <- function(a, b){ ## Evaluated lazily
+   cat(a + b) ## Both arguments are used 
+ }
> add(3) ## Passing one argument value
Error in cat(a + b) : argument "b" is missing, with no default
{% endhighlight %}

### Arguments with ‘…’

In R we can find a special argument **_..._** , which indicate a number of arguments that are usually passed on to other functions. The **_..._** argument is often used when extending another function.

{% highlight sh %}
> plot ## Execute to see the arguments 
function (x, y, ...) 
UseMethod("plot")
<bytecode: 0x10195dad0>
<environment: namespace:graphics>
> 
> myplot <- function(x, y, type = 'l', ...){
+   plot(x, y, type = type, ...) ## pass '...' to plot function
+ }
> 
> ## Create the x, y points to plot
> x=seq(0,2*pi,0.01)
> y=sin(x)
> 
> # Draw the plot graph [Figure 1]
> myplot(x,y)
{% endhighlight %}

<figure>
  <a href="/blog/r-blog-series/argument-Rplot.jpeg">
  <img src="/blog/r-blog-series/argument-Rplot.jpeg" alt="image" style="display: block;
    margin: 0 auto;">
  </a>
  <figcaption>Figure 1: Sample Plot Graph</figcaption>
</figure>


### Blog Series
* [**Introduction to R Language**](/articles/introduction-to-r-language/)
* [**Hello R World**](/blog/hello-r-world/)
* [**R Fundamentals**](/blog/r-fundamentals/)
* [**Read/Write Data into ‘R’ Language**](/blog/read-write-data/)
* [**Store data – Text/Binary Format**](/blog/store-data/)
* [**Manipulate Connections in ‘R’ Language**](/blog/connections/)
* [**Subsetting Data/R Objects**](/blog/subsetting/)
* [**Control Structures**](/blog/control-strcuture/)
* Functions in R