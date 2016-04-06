---
layout: post
title: "Subsetting Data/R Objects"
description: "R Language’s most powerful feature is indexing feature.."
modified:
categories: blog
excerpt:
tags: [R Language,Data]
image:
  feature:
date: 2016-04-03T15:39:55-04:00
comments: true
share: true
---

R Language’s most powerful feature is indexing feature. Indexing feature plays an essential role to represent the data. During the data analysis stage its vital to extract and manipulate subset of the data.

### Subsetting a Vector

The basic object of R is a vector. To extract the elements can use _’[’_ operator. 

{% highlight sh %}
> num <- c(1, 2, 3, 3, 3, 5, 6, 7, 8, 8, 9, 10) ## Create a vector
> num[1] ## Extract the first element 
[1] 1
> num[3] ## Extract the third element 
[1] 3
{% endhighlight %}

Not only one element, using _’[’_ operator we can extract multiple elopements from the vector.

{% highlight sh %}
> ## Extract multiple elements
> num[2:5] 
[1] 2 3 3 3
> ## Extract multiple elements (un order sequence- access from indices
> num[c(2,3,1,6)])
[1] 2 3 1 5
> ## Extract multiple elements (duplicate indices)
> num[c(2, 2, 2)] 
[1] 2 2 2
{% endhighlight %}

Use of negative indices 

{% highlight sh %}
> num
 [1]  1  2  3  3  3  5  6  7  8  8  9 10
> num[-1] ## Skip the first element
 [1]  2  3  3  3  5  6  7  8  8  9 10
> num[-c(1,3)] ## Skipt first and third elements
 [1]  2  3  3  5  6  7  8  8  9 10
{% endhighlight %}

Use of logic

{% highlight sh %}
> num_bool <- num > 3 ## Condition to check 
> num_bool ## Condition results 
 [1] FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[12]  TRUE
> ## Extract the result adhering to the condition
> num[num_bool] 
[1]  5  6  7  8  8  9 10
> num[num > 8] ## More compact way to do
[1]  9 10
{% endhighlight %}

### Subsetting a Matrix

Matrix can be subsetted in the usual way with their row and column indices.

{% highlight sh %}
> my_mat <- matrix(1:6, 2, 3) ## Create matrix
> colnames(my_mat) <- c("a","b","c") ## Assign name for columns 
> my_mat
     a b c
[1,] 1 3 5
[2,] 2 4 6
{% endhighlight %}

Accessing the _row=1_ and _col=2_.

{% highlight sh %}
> my_mat[1,] ## Extracting the first row
a b c 
1 3 5 
> my_mat[,2] ## Extracting the second column
[1] 3 4
{% endhighlight %}

Accessing the element using matrix indices points _row=2_,_col=3_ and _row=1_,_col=1_.

{% highlight sh %}
> my_mat[2,3] ## row=2,col=3 
c 
6 
> my_mat[1,1] ## row=1,col=1 
a 
1
{% endhighlight %}

While extracting the element from a matrix we would have seen in the above code the _**Matrix dimension has dropped**_. But during subsetting the object we have the option to turnoff by setting _**drop =FALSE**_.

{% highlight sh %}
> my_mat ## Matrix
     a b c
[1,] 1 3 5
[2,] 2 4 6
> my_mat[1, 2] ## Default drop = TRUE
b 
3 
> my_mat[1, 2, drop = FALSE] ## Set drop = FALSE
     b
[1,] 3
> my_mat[2,] ## row=2 | default drop = TRUE
a b c 
2 4 6 
> my_mat[2,, drop = FALSE] ## row=2 | default drop = FALSE
     a b c
[1,] 2 4 6
{% endhighlight %}

### Subsetting Lists 

Subsetting a list is almost like vectors. Since list can contain different objects within the list, to extract the elements we should use _[[_ or _$_ operator.

{% highlight sh %}
> ## Create a list
> my_list <- list(no = 1:10, id = 1001)
> my_list
$no
 [1]  1  2  3  4  5  6  7  8  9 10

$id
[1] 1001

> my_list[[1]] ## Use [[ operator to extract elements
 [1]  1  2  3  4  5  6  7  8  9 10
> my_list$no ## Use $ operator to extract elements
 [1]  1  2  3  4  5  6  7  8  9 10
{% endhighlight %}

### Subsetting Data Frames

It similar to matrix, we need using the indices of row and column.

{% highlight sh %}
> df <- data.frame(num = 1:3, name = c('Renien', 'John', 'Joseph'))
> df ## Data frame created
  num   name
1   1 Renien
2   2   John
3   3 Joseph
> df[1,] ## Extract the first row
  num   name
1   1 Renien
> df[1,1] ## Extract the first row’s first column element 
[1] 1
> df[c(1,3),]	## Extract the first and third row
  num   name
1   1 Renien
3   3 Joseph
> df[1,1, drop = FALSE] ## Keep the dimension
  num
1   1
{% endhighlight %}

### Blog Series
* [**Introduction to R Language**](/articles/introduction-to-r-language/)
* [**Hello R World**](/blog/hello-r-world/)
* [**R Fundamentals**](/blog/r-fundamentals/)
* [**Read/Write Data into ‘R’ Language**](/blog/read-write-data/)
* [**Store data – Text/Binary Format**](/blog/store-data/)
* [**Manipulate Connections in ‘R’ Language**](/blog/connections/)
* Subsetting Data/R Objects
* [**Control Structures**](/blog/control-strcuture/)
* [**Functions in R**](/blog/functions/)
* [**Scoping Rules of R**](/blog/scoping-rules/)