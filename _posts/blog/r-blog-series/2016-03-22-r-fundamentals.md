---
layout: post
title: "‘R’ Fundamentals"
description: "R Language data types and fundamentals"
modified:
categories: blog
excerpt:
tags: [R Language,Data Types]
image:
  feature:
date: 2016-03-22T15:39:55-04:00
comments: true
share: true
---

### Assign value

To assign a value we use the **_‘<-’_** symbol.

{% highlight sh %}
> hello <- "hello world" ## assign value
> print(hello) ## explicit printing
[1] "hello world"
> hello <- 100
> hello ## auto-print 
[1] 100
{% endhighlight %}

Like in usual programming language after assigning the value to test/evaluate, we can use **_print_** keyword to print the value. The above example was executed in console window. So it’s much easier to just type the variable to show the values rather than explicitly print. When we are printing R vector we can see [ ] brackets. In our above example its shown in the output indicates that **_‘hello’_** is a vector and 100 is its first element.

### Comments 

Unlike other programming language R doesn’t support multiple line comments. Therefore, only single line comment with **_‘#’_** character work with R language.

### Data Types

In any programming language we need various variables to implement our logics. Comparing to other programming language R, variables are not declared as some data type. The mostly used R-objects are,

* Vectors 
* Lists
* Matrices
* Arrays 
* Factors 
* Data Frames 

### Vectors

The basic type of R object is a vector. A vector can only contain objects of the same class. It can contain the following basic classes of objects:

* Logical 
* Numeric 
* Integer 
* Complex 
* Character 

{% highlight sh %}
> v <- c(T,F) ## logical
> print(class(v))
[1] "logical"
> v <- c(0.2,1) ## number
> print(class(v))
[1] "numeric"
> v <- c('a','c') ## character
> print(class(v))
[1] "character"
> v <- c(1+0i, 2+4i) ## complex
> print(class(v))
[1] "complex"
> v <- 1:10 ## integer
> print(class(v))
[1] "integer"
{% endhighlight %}


If you want to assign more than one element in a vector, we should use **_‘c()’_** function.

{% highlight sh %}
> hello <- c('h','e','l','l','0')
> hello
[1] "h" "e" "l" "l" "0"
{% endhighlight %}

### List 

A list represents has vector but can contain different objects of classes.

{% highlight sh %}
> helloList <- c(hello,12,23,34.44)
> helloList
[1] "h"     "e"     "l"     "l"     "0"     "12"    "23"    "34.44"
{% endhighlight %}

### Matrices

It’s like vectors but with ‘dimension’ attributes (two-dimensional data set). It contains row and column size.

{% highlight sh %}
> helloMat <- matrix(nrow = 2, ncol = 3)
> helloMat
     [,1] [,2] [,3]
[1,]   NA   NA   NA
[2,]   NA   NA   NA
{% endhighlight %}

### Arrays

Unlike matrices array can be created with any number of dimensions.

{% highlight sh %}
> helloArr <- array(dim = c(4,4))
> helloArr
     [,1] [,2] [,3] [,4]
[1,]   NA   NA   NA   NA
[2,]   NA   NA   NA   NA
[3,]   NA   NA   NA   NA
[4,]   NA   NA   NA   NA
{% endhighlight %}

### Factors 

It’s used to store categorical data. Factors are important in statistical modeling and this feature will be very handy to use. Basically its like keeping label in a vector.

{% highlight sh %}
> helloList <- c('hello', 'world','world','hello','world')
> helloFac <- factor(helloList)
> helloFac
[1] hello world world hello world
Levels: hello world
> table(helloFac)
helloFac
hello world 
    2     3 
{% endhighlight %}

### Data Frame

It's something similar to matrices but with different data objects in columns. Therefore, it helps to store tabular data in R Language.

{% highlight sh %}
> helloDF <- data.frame(num = 1:3, name = c('Renien', 'John', 'Joseph'))
> helloDF
  num   name
1   1 Renien
2   2   John
3   3 Joseph
{% endhighlight %}


### Blog Series
* [**Introduction to R Language**](/articles/introduction-to-r-language/)
* [**Hello R World**](/blog/hello-r-world/)
* R Fundamentals