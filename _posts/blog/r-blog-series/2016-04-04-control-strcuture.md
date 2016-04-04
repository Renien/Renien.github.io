---
layout: post
title: "Control Structures"
description: "This will help us to control the flow of the R program."
modified:
categories: blog
excerpt:
tags: [R Language,Data]
image:
  feature:
date: 2016-04-04T15:39:55-04:00
comments: true
share: true
---

This will help us to control the flow of the R program. It is very much similar to other type of programming language’s Control Structure. Lets look into some common ones,

* If-else
* For loops
* Nested for loops
* While Loops
* Repeat Loops and break
* Next

### If-else

{% highlight sh %}
> num <- 10
> if(num <= 0){ ## Condition 
+   ## do something
+   print("'num' is less than 0")
+ }else{
+   ## do something else
+   print("'num' is greater than 0")
+ }
[1] "'num' is greater than 0"
> ## Condition with ifelse (Compact way)
> ifelse(num <= 0,"'num' is less than 0","'num' is greater than 0")
[1] "'num' is greater than 0"
{% endhighlight %}

### For loops

A _for_ loop will help to iterate through iterable objects.

{% highlight sh %}
> for(i in 1:3){
+   print(i)
+ }
[1] 1
[1] 2
[1] 3
> veh <- c("car", "van", "bus") ## Create a vector with vehicles
> 
> ## Iterate without index value
> for(i in veh){
+   print(i)
+ }
[1] "car"
[1] "van"
[1] "bus"
> 
> ## Iterate through the vector object based on the interger vector
> for(i in 1:3){
+   print(veh[i])
+ }
[1] "car"
[1] "van"
[1] "bus"
> 
> ## Generate a sequence based on length of 'veh' object
> for(i in seq(veh)){
+   print(veh[i])
+ }
[1] "car"
[1] "van"
[1] "bus"
> 
> ## Curly brakets are not a must
> for(i in veh) print(i)
[1] "car"
[1] "van"
[1] "bus"
{% endhighlight %}

### Nested Loop

{% highlight sh %}
> ## Create a matrix
> my_mat <- matrix(1:6, 2, 3) 
> 
> ## Iterate the matrix using nested loops
> for(r in seq_len(nrow(my_mat))){
+   for(c in seq_len(ncol(my_mat))){
+     print(my_mat[r, c])
+   }
+ }
[1] 1
[1] 3
[1] 5
[1] 2
[1] 4
[1] 6
{% endhighlight %}

### While Loop

{% highlight sh %}
> c <- 0 ## Count 
> while(c < 3){
+   print(c) ## Iterate until it reach c=2
+   c <- c + 1
+ }
[1] 0
[1] 1
[1] 2
{% endhighlight %}

### Repeat Loops and break

The _repeat_ loop initiates an _infinite loop_. Like in other programming language if we want to stop the loop we should use _break_. 

{% highlight sh %}
> c <- 1 ## Count
> repeat{
+   if(c == 3){
+     print("'c' reached to 3")
+     break ## break the infinite loop
+   }
+   print(c)
+   c <- c + 1 ## Increment
+ }
[1] 1
[1] 2
[1] "'c' reached to 3"
{% endhighlight %}

### Next 

_next_ is used to skip an iteration of a loop.

{% highlight sh %}
> for(c in 1:10){
+   if(c <= 5){
+     next ## Skip the first 5 indices
+   }
+   print(c) ## Do something here
+ }
[1] 6
[1] 7
[1] 8
[1] 9
[1] 10
{% endhighlight %}

### Blog Series
* [**Introduction to R Language**](/articles/introduction-to-r-language/)
* [**Hello R World**](/blog/hello-r-world/)
* [**R Fundamentals**](/blog/r-fundamentals/)
* [**Read/Write Data into ‘R’ Language**](/blog/read-write-data/)
* [**Store data – Text/Binary Format**](/blog/store-data/)
* [**Manipulate Connections in ‘R’ Language**](/blog/connections/)
* [**Subsetting Data/R Objects**](/blog/subsetting/)
* Control Structures
