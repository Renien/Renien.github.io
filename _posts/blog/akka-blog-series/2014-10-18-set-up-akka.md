---
layout: post
title: "Set Up Akka"
description: "Set Up Akka"
category: blog
tags: [Akka.io, scala, java, intellij]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

Before we go any further, let’s set up so that you’re all ready to start coding in Akka. Akka.io can be written using Java and Scala.  To reduce the learning time and easy to learn I will choose Scala to explain Akka based concurrency.
At the time of this post Akka stable version is – Akka 2.3.6 and supported Scala stable version is - Scala 2.11.

###Scala Setup with SBT

The Simple Build Tool (SBT) has become most popular and easier to work. SBT is basically a building tool like Maven and Ant. Though SBT is a new for building tool mostly it downloads all the libraries from Maven repository ☺. In my scala [**blog series**](http://renien.github.io/blog/installing-tools/){:target="_blank"} I have discussed about installing Scala with SBT very clearly. After setting up scala with SBT to download akka we need only to add dependencies from the [**maven repository**](http://mvnrepository.com/artifact/com.typesafe.akka/akka-actor_2.10/2.3.6){:target="_blank"}

{% highlight scala %}
name := "akka-tutorial"

version := "1.0"

scalaVersion := "2.11.1"

libraryDependencies ++= Seq(
  "com.typesafe.akka" %% "akka-actor" % "2.3.6"
)
{% endhighlight %}

###Pull Akka Actors into SBT

If your using an Intellij IDEA once you have added the dependencies it will automatically download all the needed components. To update it through command line we’ll run **sbt update**, so we can let SBT do its things.

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/sbt-akka-downloading.png"><img src="/blog/akka-blog-series/sbt-akka-downloading.png" alt="image"></a>
  <figcaption>Figure 1 - Downloading Akka.io</figcaption>
</figure>

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/scala-akka-libraries.png"><img src="/blog/akka-blog-series/scala-akka-libraries.png" alt="image"></a>
  <figcaption>Figure 2 - Akka.io libraries</figcaption>
</figure>

> We’re now ready to go! :D

{% highlight scala %}
import java.util.concurrent.Executors
import scala.concurrent.duration.Duration
import scala.concurrent.{Await, Future, ExecutionContext}

/**
 * Created by renienj on 10/17/14.
 */
object MainAkka {
  val pool = Executors.newCachedThreadPool()
  implicit val ec = ExecutionContext.fromExecutorService(pool)
  def main(args: Array[String]) {
    val duration = Duration(10000, "millis")
    val future = Future { "<3 Akka Awesome <3 " }
    val result = Await.result(future, duration)
    println(result)
    pool.shutdown()
  }
}
{% endhighlight %}

To make sure everything can be complied and run properly create MainAkka.scala file, add the above code compile and run. Its juts a test application with Akka Future and if it prints the following output :

> <3 Akka Awesome <3

That’s it ☺. Now the tools are ready to build a large-scale concurrent application. In my next blog post lets discuss about Actors in Akka.

###Blog Series
* [**Life with Akka.io**](/articles/life-with-akka/)
* Set Up Akka
* [**Akka Concurrency**](/blog/akka-concurrency/)
* [**Actor**](/blog/actor/)
* [**Actor System**](/blog/actor-system/)
* [**Supervision / Supervisor**](/blog/supervisor/)
* [**Being Stateful](/blog/being-stateful/)