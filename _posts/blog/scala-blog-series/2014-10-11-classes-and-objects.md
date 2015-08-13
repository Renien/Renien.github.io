---
layout: post
title: "Classes and Objects"
description: "classes and objects in scala"
category: blog
tags: [scala, classes, objects, singleton]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

Like in java and .net a class is a blue print for objects. Once we define class, we can create multiple objects from the class with the keyword **new**.

{% highlight scala %}
class Product {
    // class definition goes here
}
//creating an object
new Product
{% endhighlight %}

###Fields

{% highlight scala %}
class Product {
    var price = 0 //Field
}
val soap = new Product
val chair = new Product
{% endhighlight %}

since field is var type after creating the object we can reassign with a different value to the field.

{% highlight scala %}
soap.price = 30
{% endhighlight %}

The image of the objects in memory might look like:**Figure 1**

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/class-memory.png"><img src="/blog/scala-blog-series/class-memory.png" alt="image"></a>
  <figcaption>Figure 1 - Memory allocation</figcaption>
</figure>

It’s obvious; **soap** object cannot be reinitialized because the objects given that they are vals, not vars.

{% highlight scala %}
// Won’t compile, because soap is a val
 soap = new Product
{% endhighlight %}

>“public” in Java, you simply say nothing in Scala

{% highlight scala %}
class Product {
    private var price = 0
    def add(b: Int): Unit = {
      price += b
}
}
{% endhighlight %}

>”semicolon” at the end of a statement is usually optional

{% highlight scala %}
var hello = “hello scala without semicolon”
{% endhighlight %}

But, a semicolon is required if you write multiple statements on a single line:

{% highlight scala %}
var hello = “hello scala with semicolon”; println(hello)
{% endhighlight %}

###Singleton Object

Scala is more unique and easy to use language than java.

>Scala cannot have static members

Scala has an easy way to define singleton object. Like we defining a class in scala we can easily define an object.

>Instead of the keyword "class" we use the keyword "object"

{% highlight scala %}
object Product {
    private var price = 0
    def add(b: Int): Unit = {
      price += b
}
}
{% endhighlight %}

Hope you understood about classes and objects in scala. Next we will look into functional objects and methods.

###Blog Series
* [**Introduction to Scala**](/articles/introduction-to-scala/)
* [**Installing Tools**](/blog/installing-tools/)
* [**Hello Scala World**](/blog/hello-scala-world/)
* [**Scala Code**](/blog/scala-code/)
* Classes and Objects
* [**Functional Objects and Methods**](/blog/functinal-objects-methods/)
* [**Scala Expression**](/blog/scala-expression/)
* [**Traits**](/blog/trait/)