---
layout: post
title: "Manipulate Connections in ‘R’ Language"
description: "These connections can be made to different things.."
modified:
categories: blog
excerpt:
tags: [R Language,Data]
image:
  feature:
date: 2016-04-01T15:39:55-04:00
comments: true
share: true
---

Like in most other languages R too provides some interfaces to read data and they are called _connection_ interfaces. These _connections_ can be made to different things. Lets try to understand few connections. 

* _file_ – make connection to a file 
* _url_ – make connection to url 
* _gzfile_, _bzfile_ – make connection to compressed files

### File Connection   

In R function we need to deal with lot of arguments. But most of the function name and arguments are very straightforward. If you want to a get clear understanding of the arguments you can checkout in the [**manuals**](https://stat.ethz.ch/R-manual/R-devel/library/base/html/connections.html){:target="_blank"} and it’s documented clearly.

In my [**‘Read/Write Data into ‘R’ Language’**](/blog/read-write-data/){:target="_blank"} post I was talking about some useful essential functions where we didn’t use any file connection code.  Because we don’t need to deal with connections directly as many functions have implemented to run inside them. So when we are reading and writing a file we don’t need to think much about it. 

{% highlight sh %}
> data <- read.csv(“test.txt”)
{% endhighlight %}

Lets look at the below code and try to understand to create a connection with the file.

{% highlight sh %}
> con <- file("test.txt")  
> open(con, "r") ## Open connection to test.txt' in read-only mode
> data <- read.csv(con) ## Read from the connection
> close(con) ## Close the connection
{% endhighlight %}

### URL Connection 

The _readLines()_ function is a useful once you have made the connection with the data location. Therefore, after creating the URL connection using _readLines()_ function we will be able to read the webpages line by line.

{% highlight sh %}
> con <- url("http://renien.com/blog/hello-r-world/", "r") ## open the URL connection 
> lines <- readLines(con) ## read the webpage line by line
> head(lines) ## print few lines 
[1] "<!doctype html>"                                                                         
[2] "<!--[if lt IE 7]><html class=\"no-js lt-ie9 lt-ie8 lt-ie7\" lang=\"en\"> <![endif]-->"   
[3] "<!--[if (IE 7)&!(IEMobile)]><html class=\"no-js lt-ie9 lt-ie8\" lang=\"en\"><![endif]-->"
[4] "<!--[if (IE 8)&!(IEMobile)]><html class=\"no-js lt-ie9\" lang=\"en\"><![endif]-->"       
[5] "<!--[if gt IE 8]><!--> <html class=\"no-js\" lang=\"en\"><!--<![endif]-->"               
[6] "<head>"  
{% endhighlight %}

### Connection to Compressed

To open _.gz_ file we can use _gzfile()_ interface.

{% highlight sh %}
> con <- gzfile(test.gz) ## open connection to compressed file
{% endhighlight %}

Once we open the compressed file using the connection interface we can use _readLines()_ function to read the content line by line from the text files.

{% highlight sh %}
> lines <- readLines(con,2)
[1] Renien
[2] Joseph
{% endhighlight %}

### Blog Series
* [**Introduction to R Language**](/articles/introduction-to-r-language/)
* [**Hello R World**](/blog/hello-r-world/)
* [**R Fundamentals**](/blog/r-fundamentals/)
* [**Read/Write Data into ‘R’ Language**](/blog/read-write-data/)
* [**Store data – Text/Binary Format**](/blog/store-data/)
* Manipulate Connections in ‘R’ Language
* [**Subsetting Data/R Objects**](/blog/subsetting/)
* [**Control Structures**](/blog/control-strcuture/)
* [**Functions in R**](/blog/functions/)
* [**Scoping Rules of R**](/blog/scoping-rules/)