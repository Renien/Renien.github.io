---
layout: post
title: "Building Apache Spark with Play Framework"
description: "Building Apache Spark with Play Framework"
modified:
categories: articles
excerpt:
tags: [Data Science,Big Data, Spark, PlayFramework, Scala, Machine Learning]
image:
  feature:
date: 2020-03-10T15:39:55-04:00
comments: true
share: true
---


<div class="github-fork-ribbon" style="position: fixed;padding: 2px 0;background-color: #000;background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.15));-webkit-box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);-moz-box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);z-index: 9999;pointer-events: auto;top: 42px;right: -43px;-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);-ms-transform: rotate(45deg);-o-transform: rotate(45deg);transform: rotate(45deg);"><a href="https://github.com/Renien/play-with-spark-starter-kit" style="font: 700 13px &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif;color: #fff;text-decoration: none;text-shadow: 0 -1px rgba(0, 0, 0, 0.5);text-align: center;width: 200px;line-height: 20px;display: inline-block;padding: 2px 0;border-width: 1px 0;border-style: dotted;border-color: rgba(255, 255, 255, 0.7);">Fork me on GitHub</a></div>

Nowadays businesses are hiring data scientists in droves to make rigorous, scientific, unbiased, data-driven decisions.  The data is huge, therefore the biggest challenge is to build faster and scalable systems for prediction and decision making engines.

<figure style="text-align: center;">
	<a href="/articles/decision.jpeg"><img src="/articles/decision.jpeg" alt="image" ></a>
</figure>

> Without faster and scalable decision-making engine business will not be able to create data driven business models

There are situations where business needs real time predictions for daily trained models. One of the most popular high velocity framework is Play Framework. It allows to build web applications which follow the model-view-controller (MVC) architectural pattern. Apache Spark is a lightning-fast cluster computing engine that supports well matured many distributed machine learning algorithms.

> What if we can run Apache Spark on a local machine along with Play Framework controllers?

If we can manage to run Apache Spark application along with Play application we can leverage Spark ML algorithms for real time predictions.  

In my recent work I had to setup play with spark and I faced multiple dependency issues in Akka and guava versions. Therefore I have created a starter kit for anyone who is interested in working with play-spark.

In this starter kit you will find an API where it will count the words on top of spark context and the result will be returned as response (http://localhost:9000/prediction).

<figure style="text-align: center;">
	<a href="/articles/decision.jpeg"><img src="/articles/model-prediction.png" alt="image" ></a>
</figure>

In this example it includes, Spark Model loading guice module where it creates a Spark Context/Spark Session as singleton object during the Application startup time.

By following this example we can integrate any complex Spark ML models to provide real time prediction.

{% highlight bash %}
.
├── app
│   ├── controllers
│   │   └── HomeController.java
│   ├── guice
│   │   └── module
│   │       └── MLLibModule.java              --> Machine Learning guice module
│   ├── ml
│   │   └── ModelPrediction.scala             --> Model prediction class (word count example)
│   ├── response
│   ├── startup
│   │   └── AppLoader.java                    --> App loader module
.
.
{% endhighlight %}

Starter Kit: [**Play-With-Spark**](https://github.com/Renien/play-with-spark-starter-kit){:target="_blank"}
