---
layout: post
title: "Life with Apache Spark"
description: "Apache Spark - Lightning-Fast Cluster Computing"
modified:
categories: articles
excerpt:
tags: [Spark,Big Data, Hadoop ,Machine learning]
image:
  feature:
date: 2014-12-03T15:39:55-04:00
comments: true
share: true
---

As programmers, we are frequently asked to play around with big data to solve some problems. Developing a solution for one-user, developers will easily do it.
But the fun part comes when the solution is going to production where very large no of people try to use our solution :D. Then we need to program in away to handle the load balance and to provide a very good responsive solution for users.

> The future has already arrived. It's just not evenly distributed yet. - William Gibson

Apache Spark is an open-source data analytics cluster computing framework. Spark writes to something called RDDs (Resilient Distributed Datasets), which can live in memory. Apache Spark is mostly popular as an alternative solution to MapReduce and Hive when manipulating big data. 

Rather than being restricted to maps and reduces, Apache Spark is wonderful distributed data manipulating framework 
Which supports a rich set of higher-level tools including Spark SQL for SQL and structured data processing, MLlib for [**machine learning (ML)**](https://spark.apache.org/docs/1.1.0/mllib-guide.html){:target="_blank"} , [**GraphX**](https://spark.apache.org/graphx/){:target="_blank"} for graph processing, and [**Shark**](https://spark.apache.org/sql/){:target="_blank"} Streaming.

<figure>
  <a href="/articles/spark-logo.png"><img src="/articles/spark-logo.png" alt="image" style="box-shadow: 5px 5px 2.5px #888888; margin: 0 0 10px 10px; max-width:200px;"></a>
</figure>
{: .pull-right}

> Lightning-Fast Cluster Computing

Spark can run on [**Hadoop**](http://hadoop.apache.org/){:target="_blank"}, [**Mesos**](http://mesos.apache.org/){:target="_blank"}, standalone, or in the cloud. It can access diverse data sources including **HDFS**, **Cassandra**, **HBase**, [**S3**](http://aws.amazon.com/s3/){:target="_blank"}.

I’m really impressed with Apache Spark and the way it works on a distributed environment. I’m planning to use it on Hadoop lets see how Apache Spark can run like a lighting bolt :D to produce the data and to do machine learning on distributed an environment with real-time data.

### Learning Guide

<figure>
  <a href="/articles/apache-spark-book.png"><img src="/articles/apache-spark-book.png" alt="image" style="box-shadow: 5px 5px 2.5px #888888; margin: 0 0 10px 10px; max-width:200px;"></a>
</figure>
{: .pull-right}


Fast Data Processing with Spark by Holden Karau helped me to learn and to understand all the fundamentals of Apache Spark. If you follow the book from Chapter 1 to the end you will be able to understand the entire concept and the use of Apache Spark. It also provides a guide to compile, build and run Spark on Hadoop.
