---
layout: post
title: "Store data – Text/Binary Format in ‘R’ Language"
description: "In all the programming language there are mainly two ways to store data."
modified:
categories: blog
excerpt:
tags: [R Language,Data]
image:
  feature:
date: 2016-03-29T15:39:55-04:00
comments: true
share: true
---

In all the programming language there are mainly two ways to store data.

* Textual Format 
* Binary Format 

### Textual Format 

In textual format mostly programmers always follow a standard format like CSV to store data. But in R Language in our intermediate steps we have the ability store the R objects in textual format. So data scientists can preserve/deparse R object by using the _dput()_ or _dump()_ functions. 


{% highlight sh %}
> x <- data.frame(num = 1:3, name = c('Renien', 'John', 'Joseph')) ## Sample data frame
> dput(x) ## Print the ‘dput’ to console
structure(list(num = 1:3, name = structure(c(3L, 1L, 2L), .Label = c("John", 
"Joseph", "Renien"), class = "factor")), .Names = c("num", "name"
), row.names = c(NA, -3L), class = "data.frame")
{% endhighlight %}

The output from _dput()_ is in sort of a R code format with all the class details. Therefore it preserves the object in away using _dget()_ we can read back the object into the R Language.

{% highlight sh %}
> dput(x, file = 'x.R') ## Store the data in x.R filed
> stored_object <- dget('x.R') ## Read the output from file
> stored_object
  num   name
1   1 Renien
2   2   John
3   3 Joseph
{% endhighlight %}

To store multiple objects we need to use _dump()_.

{% highlight sh %}
> y <- "Hello dump function" ## vector object
> x <- data.frame(num = 1:3, name = c('Renien', 'John', 'Joseph')) ## data frame object
> dump(c('x','y'), file = "dumpData.R") ## Store the multiple objects
> rm(x,y) ## Remove the variables 
{% endhighlight %}

To read the _dump()_ file we need to use _source()_ function.

{% highlight sh %}
> source("dumpData.R") ## Load the objects 
> x
  num   name
1   1 Renien
2   2   John
3   3 Joseph
> y
[1] "Hello dump function"
{% endhighlight %}

### Binary Format 

Considering the effectiveness purpose, we need to store R objects in binary format. The key functions are _save()_, _save.image()_ to store in binary format.

{% highlight sh %}
> y <- "Hello dump function"
> x <- data.frame(num = 1:3, name = c('Renien', 'John', 'Joseph'))
> save(x,y,file = "my_xy_data.rda")
> rm(x,y)
> x
Error: object 'x' not found
> load("my_xy_data.rda")
> x
  num   name
1   1 Renien
2   2   John
3   3 Joseph
> y
[1] "Hello dump function"
{% endhighlight %}

> To store the data we can use any file extensions. But .rda and . RData are fairly common extensions widely used.

The below code snippet clearly shows all the arguments for _save_ and _save.image_ functions.

{% highlight r %}
save(..., list = character(),
     file = stop("'file' must be specified"),
     ascii = FALSE, version = NULL, envir = parent.frame(),
     compress = isTRUE(!ascii), compression_level,
     eval.promises = TRUE, precheck = TRUE)

save.image(file = ".RData", version = NULL, ascii = FALSE,
           compress = !ascii, safe = TRUE)
{% endhighlight %}

### Blog Series
* [**Introduction to R Language**](/articles/introduction-to-r-language/)
* [**Hello R World**](/blog/hello-r-world/)
* [**R Fundamentals**](/blog/r-fundamentals/)
* [**Read/Write Data into ‘R’ Language**](/blog/read-write-data/)
* Store data – Text/Binary Format