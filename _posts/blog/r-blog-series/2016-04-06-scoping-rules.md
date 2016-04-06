---
layout: post
title: "Scoping Rules of R"
description: "When we use some symbol to implement our logics, how does R know which value to assign?"
modified:
categories: blog
excerpt:
tags: [R Language,Data]
image:
  feature:
date: 2016-04-06T15:39:55-04:00
comments: true
share: true
---

When we use some symbol to implement our logics, how does R know which value to assign?

> R functions are treated much like any other R objects.

Assume we are running the following code,

{% highlight sh %}
> c <- 100 ## Assign a value to 'c'
> (c+1) ## Increment 
[1] 101
> 
> vec <- c(1:10) ## Create a vector
> vec
 [1]  1  2  3  4  5  6  7  8  9 10
{% endhighlight %}

If we observe properly, we can still use **_c()_** to create vectors. Now the question is how does R know to use which **_c_** symbol to use and when? It’s because,

> R has separate namespace for functions and non-functions.

Lets try to understand it clearly. When R tried to **_‘bind/connect’_** a value to a symbol (in our case **_c()_**, it search for the corresponding symbol in an order.

* Search the global environment (workspace) for a symbol name matching the request.
* Search the namespaces of each of the packages on the search list.

So the search list will have the follow packages (packages which we have loaded) including **_".GlobalEnv"_**  as a first item in the search list and the **_“base”_** is always at the very end.

{% highlight sh %}
> search()
 [1] ".GlobalEnv"        "tools:rstudio"     "package:stats"    
 [4] "package:graphics"  "package:grDevices" "package:utils"    
 [7] "package:datasets"  "package:methods"   "Autoloads"        
[10] "package:base"
{% endhighlight %}

**_".GlobalEnv"_** is just our workspace. If there is a symbol matching it will get it from workspace. If nothing found it will search from the rest of the namespace in each of the packages.

## Rules of scoping 

R uses scoping rules called **_Lexical scoping_** (static scoping).

It will determine the value associated with free variable function.

{% highlight sh %}
> fun <- function(x,y){
+   x^2 + y / z
+ }
> fun(2,3)
{% endhighlight %}

In the above function we have two arguments and they are **_x_**, **_y_**. But inside the function body we can find another symbol **_‘z’_**. In this case **_z_** is called **_free variable_**.

According to scoping rules in R it first searches in the environment where the function was defined. An environment is collection of symbols and values. Environments have patents.

{% highlight sh %}
> parent.env(globalenv())
<environment: 0x10390d6e0>
attr(,"name")
[1] "tools:rstudio"
{% endhighlight %}

Since we defined **_fun_** function in global environment, R will look for **_z_** in that scope (environment).

{% highlight sh %}
> environment(fun) ## to check the scope
<environment: R_GlobalEnv>
{% endhighlight %}

> These rule are matters because we can define some complex logics and function.

{% highlight sh %}
> y <- 10 ## y Symbol
> 
> f1 <- function(x) {
+   y <- 2 ## Binding value to 'y' symbol
+   y^2 + f2(x) ## 'f2' function is used
+ }
> 
> f2 <- function(x) {
+   x * y
+ }
> 
> f1(2) ## Execute 'f1' function 
[1] 24
> f2(2) ## Execute 'f2' fucntion
[1] 20
{% endhighlight %}


### Blog Series
* [**Introduction to R Language**](/articles/introduction-to-r-language/)
* [**Hello R World**](/blog/hello-r-world/)
* [**R Fundamentals**](/blog/r-fundamentals/)
* [**Read/Write Data into ‘R’ Language**](/blog/read-write-data/)
* [**Store data – Text/Binary Format**](/blog/store-data/)
* [**Manipulate Connections in ‘R’ Language**](/blog/connections/)
* [**Subsetting Data/R Objects**](/blog/subsetting/)
* [**Control Structures**](/blog/control-strcuture/)
* [**Functions in R**](/blog/functions/)
* Scoping Rules of R