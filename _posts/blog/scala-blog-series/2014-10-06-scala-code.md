---
layout: post
title: "Scala Code"
description: "Scala Code"
category: blog
tags: [tools, scala, java, variables]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

###Defining variables

Scala has two kinds of variables, vals and vars. A val is similar to a final variable in Java. Once initialized, a val can never be reassigned. A var, its more likely var variables in C#. A var can be reassigned throughout its lifetime. Here’s a val definition: **Figure 1**

{% highlight scala %}
 val msg = "Hello Scala World!"
/*
  Compilation error
  Can't assign value to "val"
 * */
msg = "Scala Confusing"

var msg = "Hello Scala World!"
/*
  Can assign value to "var"
 * */
msg = "Scala <3"
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/scala-varibles.png"><img src="/blog/scala-blog-series/scala-varibles.png" alt="image"></a>
  <figcaption>Figure 1 - Scala Varibles</figcaption>
</figure>

###Scala Functions

<figure>
  <a href="/blog/scala-blog-series/scala-funtion.png"><img src="/blog/scala-blog-series/scala-funtion.png" alt="image"></a>
  <figcaption>Figure 2 - Scala Function</figcaption>
</figure>

###Loops with while and for decision if

{% highlight scala %}
var args = Array(-1,3,4,-5) //Array
var i = 0
while (i < args.length) { //While loop
  if (i != 0) //If condition
  print(" ")
  print(args(i))
  i += 1
}
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/while-if.png"><img src="/blog/scala-blog-series/while-if.png" alt="image"></a>
  <figcaption>Figure 3 - While and If</figcaption>
</figure>

###Iterate with foreach and for

{% highlight scala %}
var args = Array(-1,3,4,-5) //Array
args.foreach(arg => println(arg))
for (arg <- args)
    println(arg)
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/scala-foreach.png"><img src="/blog/scala-blog-series/scala-foreach.png" alt="image"></a>
  <figcaption>Figure 4 - Foreach</figcaption>
</figure>

###Array

{% highlight scala %}
val greetStrings = new Array[String](3)
  greetStrings(0) = "Hello"
  greetStrings(1) = ", "
  greetStrings(2) = "world!\n"
  for (i <- 0 to 2)
    print(greetStrings(i))
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/scala-array.png"><img src="/blog/scala-blog-series/scala-array.png" alt="image"></a>
  <figcaption>Figure 5 - Array</figcaption>
</figure>

###Operations

Basically all operations are methods call in scala

<figure>
  <a href="/blog/scala-blog-series/scala-all-function.png"><img src="/blog/scala-blog-series/scala-all-function.png" alt="image"></a>
  <figcaption>Figure 6 - Operations are functions</figcaption>
</figure>

###List

* Mutated (:::)
Basically it’s like ‘Python Extends’. It will include two list and will return with a new list.
{% highlight scala %}
val l1 = List(1, 2, 3)
val l2 = List(1, 2)
val l3 = List(3, 4)
/* Mutated and created and
 * Created a new list */
val l4 = l2 ::: l3
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/scala-mutated.png"><img src="/blog/scala-blog-series/scala-mutated.png" alt="image"></a>
  <figcaption>Figure 7 - Mutated</figcaption>
</figure>

* Cons (::)
Cons prepend a new element to the beginning of an existing list, and return the resulting list.
{% highlight scala %}
val l1 = List(1, 2, 3)
//Cons
val l2 = 0 :: l1
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/scala-cons.png"><img src="/blog/scala-blog-series/scala-cons.png" alt="image"></a>
  <figcaption>Figure 8 - Cons</figcaption>
</figure>

* Nil
{% highlight scala %}
val ls1 = List(1,2,3)
val ls2 = 1::2::3::Nil

println(s"New list with 'List', $ls1")
println(s"New list with 'Nil', $ls2")
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/scala-nil.png"><img src="/blog/scala-blog-series/scala-nil.png" alt="image"></a>
  <figcaption>Figure 9 - Nil</figcaption>
</figure>

To get more details on list check the [**scala api doc**](http://www.scala-lang.org/api/current/index.html#scala.collection.immutable.List){:target="_blank"}

###Tuples

If you are a Python programmer you would have probably know about this container. It’s a very useful container object. Like lists, tuples are immutable, but unlike lists, tuples can contain different types of elements.

{% highlight scala %}
//Tuples
val pair = (99, "Scala <3")
println(pair)
println(pair._1)
println(pair._2)
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/scala-tuple.png"><img src="/blog/scala-blog-series/scala-tuple.png" alt="image"></a>
  <figcaption>Figure 10 - Tuple</figcaption>
</figure>

###Mutable and Immutable
Mutable and immutable are English words meaning "can change" and "cannot change" respectively. The meaning of the words is the same in the IT context; i.e.
*	a mutable string can be changed, and
*	an immutable string cannot be changed.
*	For example, arrays are always mutable; lists are always immutable

###Sets and Maps

{% highlight scala %}
//Set
var fishSet = Set("Gold Fish", "Angel Fish")
fishSet += "Piranha"
println(fishSet.contains("Cichlid"))
{% endhighlight %}


{% highlight scala %}
//Map
val romanNumbers = Map(
  1 -> "I", 2 -> "II", 3 -> "III", 4 -> "IV", 5 -> "V"
)
println(romanNumbers(4))
{% endhighlight %}

<figure>
  <a href="/blog/scala-blog-series/scala-map.png"><img src="/blog/scala-blog-series/scala-map.png" alt="image"></a>
  <figcaption>Figure 11 - Set and Map</figcaption>
</figure>

Now that we have seen some scala code, you can try and have fun with scala ☺. In my next blog lets dive into more details on class and objects.

###Blog Series
* [**Introduction to Scala**](/articles/introduction-to-scala/)
*	[**Installing Tools**](/blog/installing-tools/)
* [**Hello Scala World**](/blog/hello-scala-world/)
* Scala Code
* [**Classes and Objects**](/blog/classes-and-objects/)
* [**Functional Objects and Methods**](/blog/functinal-objects-methods/)
