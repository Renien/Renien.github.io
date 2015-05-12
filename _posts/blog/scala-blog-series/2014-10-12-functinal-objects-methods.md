---
layout: post
title: "Functional Objects and Methods"
description: "Functional Objects and Methods"
category: blog
tags: [scala, classes, objects, implicit]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

The journey of exploring scala language continues. In our previous post we discussed about the class and object. In this post we will look into closer  use of objects and methods in scala. To understand the theory lets try to implement a simple calculator using scala.

>The Scala compiler will compile any code you place in the class body, which isn’t part of a field or a method definition, into the primary constructor.

{% highlight scala %}
class Calculator(n: Int, d: Int){
  //debug message
  println(s"cal values: $n and $d")
}
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/calculator-class-constructor.png"><img src="/blog/scala-blog-series/calculator-class-constructor.png" alt="image"></a>
  <figcaption>Figure 1 - Scala Constructor</figcaption>
</figure>

>Reimplementing the toString method

By default, scala class inherits the implementation of **“toString”** defined in class java.lang.Object, which just prints the class name, an @ sign, and a hexadecimal number (**Figure 1 - Calculator@57257f14**).
We can override the default implementation by adding a method toString to our class.

{% highlight scala %}
class Calculator(n: Int, d: Int){
  //override toString
  override def toString = s"cal values: $n and $d"
}
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/scala-tostring-override.png"><img src="/blog/scala-blog-series/scala-tostring-override.png" alt="image"></a>
  <figcaption>Figure 2 - toString Override</figcaption>
</figure>

In a calculator program mostly a known error, when a value is dividing by zero. So we need to handle this problem. The best approach is to define as a precondition of the primary constructor stage. One way to do that is to use scala **“require”** function.

>Require method takes one boolean parameter. If the condition is true it will return true or stop the execution by throwing an IllegalArgumentException

{% highlight scala %}
class Calculator(n: Int, d: Int){
  require(d != 0)
  //override toString
  override def toString = s"cal values: $n and $d"
}
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/scala-required.png"><img src="/blog/scala-blog-series/scala-required.png" alt="image"></a>
  <figcaption>Figure 3 - required</figcaption>
</figure>

###Auxiliary constructors

Sometimes we need multiple constructors in a class. In Scala other than the primary constructor other constructors are called **auxiliary constructors**.

{% highlight scala %}
class Calculator(n: Int, d: Int){
  require(d != 0)
  //override toString
  override def toString = s"cal values: $n and $d"

  // auxiliary constructor
  def this(n: Int) = this(n, 1)
}
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/auxiliary-constructor.png"><img src="/blog/scala-blog-series/auxiliary-constructor.png" alt="image"></a>
  <figcaption>Figure 4 - Auxiliary Constructor</figcaption>
</figure>

###Method

Now lets define a “add method” in our calculator class where it adds two values.

{% highlight scala %}
class Calculator(n: Int, d: Int){
  require(d != 0) //precondition
  //override toString
  override def toString = s"cal values: $n and $d"
  val n1: Int = n
  val n2: Int = d
  var result = 0
  // auxiliary constructor
  def this(n: Int) = this(n, 1)
  //adding two values
  def add() ={
    this.result = this.n1 + n2
    println(s"Add : $n1 + $n2 = $result")
  }
}
val cal = new Calculator(2)
cal.add()
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/calculator-add.png"><img src="/blog/scala-blog-series/calculator-add.png" alt="image"></a>
  <figcaption>Figure 5 - add method</figcaption>
</figure>

###Defining Operators

In scala we can do many interesting things ☺.

>Why shouldn't we use the natural arithmetic operators as methods?

Yes, We can do this in scala ☺.

{% highlight scala %}
def * (i: Int) ={
  val demon = this.result
  this.result = this.result * i
  println(s"Multiply : $demon + $i = $result")
}
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/scala-method-operator.png"><img src="/blog/scala-blog-series/scala-method-operator.png" alt="image"></a>
  <figcaption>Figure 6 - Method operators</figcaption>
</figure>

Now we can write **cal * 2**, we might also want to swap the operands, as in **2 * cal**. Unfortunately this does not work yet.

>Solution is Implicit

###Implicit Conversions

{% highlight scala %}
implicit def calToInt (n: Calculator): Int = {
  return n.result
}
val cal = new Calculator(2)
cal.add()
cal * 2
2 * cal
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/scala-implicit.png"><img src="/blog/scala-blog-series/scala-implicit.png" alt="image"></a>
  <figcaption>Figure 7 - Method operators</figcaption>
</figure>

We can create an implicit conversion that automatically converts Calculator object to integer when needed. Basically this will help to reduce the code a lot and to reuse the existing methods very effectively. I will discuss later in detail on scala implicit conversion ☺.

So far we saw more aspects of classes in Scala. In next post we will discuss about scala **traits**.


###Blog Series
* [**Introduction to Scala**](/articles/introduction-to-scala/)
*	[**Installing Tools**](/blog/installing-tools/)
* [**Hello Scala World**](/blog/hello-scala-world/)
* [**Scala Code**](/blog/scala-code/)
* [**Classes and Objects**](/blog/classes-and-objects/)
* Functional Objects and Methods