---
layout: post
title: "[Modern] On-Prem Data Platform"
description: "[Modern] On-prem Data Platform"
modified:
categories: articles
excerpt:
tags: [DataPlatform, OnPrem, ELT, Trino, Presto]
image:
  feature:
date: 2023-08-27T15:39:55-04:00
comments: true
share: true
---


An on-premises data warehouse refers to a data storage and management solution that is physically hosted within an organization's own data center or facilities, as opposed to being hosted in the cloud. 

In recent years, the trend has been shifting toward cloud-based data warehousing solutions due to their scalability, flexibility, and reduced upfront costs. However, on-premises data warehouses continue to be relevant for organizations with specific requirements around data control, security, compliance, and performance.  

<figure style="text-align: center;">
  <a href="/articles/data-privacy.png"><img src="/articles/data-privacy.png" alt="image" width="25%" height="25%"></a>
  <figcaption>Data Privacy</figcaption>
</figure>

In recent times I’ve been solutioning/designing on-prem data platforms due to data residency law. When it comes to on-prem data platforms, the first thing that a data geek will think about is managing Hadoop clusters. But the intention on a SaaS data platform is to reduce the operational overhead and managing Hadoop clusters is actually a big overhead. 

If it’s only for canned reports that can be done easily with RDBMS databases. But nowadays a data centric approach is a key thing for any business. If we want to really do data driven business it's vital to have a proper data lake, data warehouse or data mesh strategy to enable it.

<figure style="text-align: center;">
	<a href="/articles/hadoop-dp.png"><img src="/articles/hadoop-dp.png" alt="image"></a>
  <figcaption>Hadoop Data Lake & Warehouse</figcaption>
</figure>

The technology growth has changed a lot of pieces on big data and data platform spectrum. As I said, managing Hadoop clusters is an overkill to a company and team. So basically we need to find reliable data lake storage similar to cloud bucket storage.

Minio & Chep / Rook both are very popular open source distributed storage that can be managed easily and it supports on top of the kubernetes cluster. This actually changed the whole thinking pattern of the Hadoop ecosystem. In our recent on-prem solution we wiped out the Hadoop ecosystem idea and managed to build a fully managed on-prem data platform on top of the kubernetes cluster. 


<figure style="text-align: center;">
  <a href="/articles/s3-bucket.png"><img src="/articles/s3-bucket.png" alt="image"></a>
    <figcaption>S3 like bucket</figcaption>
</figure>

Since managing and querying big data on Hadoop can be challenging. We found alternative solutions like Minio/CEPH S3 object stores which you can access and query with Presto or Trino. Therefore, we ended up relying on S3 object stores that’s deployed on K8 clusters and Hive metastore, Trino for data warehousing. 


<figure style="text-align: center;">
	<a href="/articles/On-Prem-DWH-Solution.png"><img src="/articles/On-Prem-DWH-Solution.png" alt="image" ></a>
    <figcaption>Modern On-Prem DWH Solution</figcaption>
</figure>

So far the journey looks really great and moto on building [**Data Platform-in-a-Box**](articles/data-platform-in-a-box/) rolling out to be real and enjoying the performance and scalability on the k8 cluster.

The current setup on on-prem data platform is somewhat equivalent to all cloud data platforms. One of the missing pieces in this blog is on masking policies and solutions. We have already solved it as well and in my next blog post I will explain about it. 

> Stay Tuned!... Cheers! 🍺



