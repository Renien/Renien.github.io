---
layout: post
title: "Installing PySpark - SPARK"
description: "Installing PySpark - SPARK"
category: blog
tags: [hadoop, spark, python, bigdata, scala, java]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

The Apache Hadoop project is open-source software for reliable, scalable, distributed computing. It has revolutionized big data processing. Hadoop provides the users to store and process huge amounts of data at very low costs.

Hadoop MapReduce is used to process vast amounts of data in parallel on large clusters to manipulate these data on Hadoop in a fault-tolerant manner.

>“Big data is not about the data” – Gary King

Spark is an open source alternative to MapReduce designed to make it easier to build and run fast data manipulation on Hadoop. Spark comes with a library of [**machine learning (ML)**](https://spark.apache.org/docs/1.1.0/mllib-guide.html){:target="_blank"} and [**graph algorithms**](https://spark.apache.org/graphx/){:target="_blank"}, and also supports real-time streaming and SQL apps, via [**Spark Streaming**](https://spark.apache.org/streaming/){:target="_blank"} and [**Shark**](https://spark.apache.org/sql/){:target="_blank"}, respectively. Spark exposes the Spark programming model to Java, Scala, or Python.

> Spark 10 to 100 times faster than equivalent MapReduce.

The following video tutorial helped me to successfully build Spark on Mac OS.

<iframe width="420" height="315" src="//www.youtube.com/embed/bWorBGOFBWY" frameborder="0" allowfullscreen></iframe>

Hope it will help you all too ☺

To start the PySpark shell, after successfully building spark (It will take some time), in the spark root folder we can see a **bin** folder. Run the following command in your terminal to open the shell (**Figure 1**).

{% highlight bash %}
./bin/pyspark
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/pyspark-shell.png"><img src="/blog/pyspark-shell.png" alt="image"></a>
  <figcaption>Figure 1 - Spark Shell</figcaption>
</figure>

To test Spark installation run the following python code (**Figure 2**)

{% highlight python %}
words = sc.parallelize(["scala","java","hadoop","spark","akka"])
words.count()
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/spark-python-api.png"><img src="/blog/spark-python-api.png" alt="image"></a>
  <figcaption>Figure 2 – Spark Python API</figcaption>
</figure>

