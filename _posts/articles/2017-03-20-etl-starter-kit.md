---
layout: post
title: "ETL-Starter-Kit (Extract Transform Load)"
description: "Lambda Architecture(LA) is a well-known data processing architecture designed to handle massive amount of data"
modified:
categories: articles
excerpt:
tags: [Data Science,Big Data, ETL, Hadoop, Scalding, Azkaban, Gradle]
image:
  feature:
date: 2017-03-20T15:39:55-04:00
comments: true
share: true
---

<div class="github-fork-ribbon" style="position: fixed;padding: 2px 0;background-color: #000;background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.15));-webkit-box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);-moz-box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);z-index: 9999;pointer-events: auto;top: 42px;right: -43px;-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);-ms-transform: rotate(45deg);-o-transform: rotate(45deg);transform: rotate(45deg);"><a href="https://github.com/Renien/ETL-Starter-Kit" style="font: 700 13px &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif;color: #fff;text-decoration: none;text-shadow: 0 -1px rgba(0, 0, 0, 0.5);text-align: center;width: 200px;line-height: 20px;display: inline-block;padding: 2px 0;border-width: 1px 0;border-style: dotted;border-color: rgba(255, 255, 255, 0.7);">Fork me on GitHub</a></div>

Lambda Architecture(LA) is a well-known data processing architecture designed to handle massive amount of data and it’s commonly known as Big Data. It contains both batch and stream processing methods.

<figure style="text-align: center;">
	<a href="/articles/etl-lamda.jpg"><img src="/articles/etl-lamda.jpg" alt="image" ></a>
</figure>

When I started my journey in Data Science to process massive data came across an excellent book,

<figure style="text-align: center;">
	<a href="/articles/big-data-book.jpeg"><img src="/articles/big-data-book.jpeg" alt="image" ></a>
</figure>

> “Big Data Principles and best practices of scalable real-time data systems by [Nathan Marz](https://twitter.com/nathanmarz){:target="_blank"} and James Warren.”  

I recommend to read this book for all Big Data/Data Science developers.

In Big Data/Data Science project LA aims to satisfy the need to scale up and shrink indecently and also the system that is fault tolerant. Therefore, it is essential to get a correct structure for your project before starting over the implementation.

I spent almost couple of years building Lambda Architecture design for client specific projects. I realized in Big Data domain starter-kit projects are lacking when comparing to JavaScript world. So, I have published minimal skeleton project to process Big Data,

<figure style="text-align: center;">
	<a href="/articles/ELT.png"><img src="/articles/ELT.png" alt="image" width="20%" height="20%"></a>
</figure>

Introducing: [**ETL-Starter-Kit**](https://github.com/Renien/ETL-Starter-Kit){:target="_blank"}

Since the repository is to keep only the structure; different type of many sample jobs are not implemented. Based on your requirement be free to modify and implement different type of batch/streaming jobs (Spark, Hive, Pig etc)



