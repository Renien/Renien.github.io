---
layout: post
title: "Scala Expression"
description: "Scala Expression"
category: blog
tags: [scala]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

###If Expression 

Like many other programming languages `Scala if expression` is not the same. After the execution of the code, if statements are expressions meaning that they return a value. Hence, this can be written in the following two ways:

{% highlight scala %}
var result = ""
val a = true
val b = true
if(a == b)
  result = "Scala say’s true"
else
  result = "Scala say’s not true "
{% endhighlight %}

or

{% highlight scala %}
result = if(a == b)
  "Scala say’s true"
else
  "Scala say’s not true"
{% endhighlight %}

###Loops

Scala’s `while loop` behave the same like Java and C#. Scala while loop has a condition and a body. According to the condition the body context will keep on looping.

{% highlight scala %}
var line = ""
while(line != "")
  line = readLine()
  println("Read: "+ line)
{% endhighlight %}

Scala also has `do-while loop`. Like while loop it will keep on looping until the condition is true.

{% highlight scala %}
do {
 line = readLine()
 println("Read: "+ line)
} while (line != "")
{% endhighlight %}

Scala’s `for loop` expression is bit different. It has some fancy way of implementing with arrow syntax to iterate through the collection dataset.

{% highlight scala %}
val nums = Array(1, 2, 3, 4)
for(num <- nums)
  println(num)
  
nums.foreach(num=>println(num))

for(count <- 0 to nums.length -1)
  println(nums(count))
{% endhighlight %}

The above loop functionality you may have come across in Java and C#. But Scala for loop offers a lot more feature like filter, nested loop and yield.

###Filtering 

We some times do not want to iterate through the entire collection data and we need to break down in to a small subset. So scala provide the freedom to do that by adding condition as filter.

{% highlight scala %}
class Fish(val name: String, val isBeautiful: Boolean)

val seaFish = List(new Fish("dinosaur bichir", false),
                new Fish("Ornate bichir", false),
                new Fish("Reedfish", true),
                new Fish("Emerald catfish", true),
                new Fish("Adolfo's catfish", false),
                new Fish("Banded corydoras", true))
                
for(fish: Fish <- seaFish
    if !fish.isBeautiful
    if fish.name.contains("catfish"))
  println(fish.name)
{% endhighlight %}

The following above code consist a `Fish` class with the attribute fish name and whether it’s a beautiful fish. In the next line list of `seaFish` is created and during the iteration process `ugly catfish` fishes are filtered.

###Nested loops

There can be a situation where you will need to iterate through a collection where it consists of another collection list. Basically it’s a nested collection data. Scala provides a great feature to run through the collection data with **one for loop** ☺.

You have come to a stage where you need to manipulate and analyse with two or more groups of dataset. The following below code shows clearly while iterating through `fish list` include the  `lakeFish` list in an effective way.

{% highlight scala %}
val lakeFish = List(new Fish("Freshwater drum", false), new Fish("Atlantic salmon", true))
val fishGroups = List(fish, lakeFish)
for(fish <- fishGroups; fish <- fish)
  println(" => "+fish.name)
{% endhighlight %}

###Yielding

Using the yield keyword with `for loop` expressions, can create and return new collections data set.

{% highlight scala %}
val names = for(fish <- seaFish) yield "new " + fish.name
for(name <- names) println("yield : " + name)
{% endhighlight %}

To understand the yield functionality lets take the fish example the ‘seaFish’ list object and during the for loop iteration process use the `yield` keyword to append **'new'** string value in front of all the sea fish names. So it will append and create a new collections list (**Figure 1**)

<figure style="text-align: center;">
  <a href="/blog/scala-blog-series/for-loop-yield.png"><img src="/blog/scala-blog-series/for-loop-yield.png" alt="image"></a>
  <figcaption>Figure 1 - Creating a new collections</figcaption>
</figure>

###Blog Series
* [**Introduction to Scala**](/articles/introduction-to-scala/)
* [**Installing Tools**](/blog/installing-tools/)
* [**Hello Scala World**](/blog/hello-scala-world/)
* [**Scala Code**](/blog/scala-code/)
* [**Classes and Objects**](/blog/classes-and-objects/)
* [**Functional Objects and Methods**](/blog/functinal-objects-methods/)
* Scala Expression
