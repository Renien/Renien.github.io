---
layout: post
title: "Cloud-DataSync"
description: "There are plenty of good reasons to move towards cloud, but mainly it make good business sense. Service like AWS Elastic MapReduce (EMR Cluster) and GCP DataProc makes life easy"
modified:
categories: articles
excerpt:
tags: [Big Data, Cloud, Shell, Hadoop]
image:
  feature:
date: 2017-05-09T15:39:55-04:00
comments: true
share: true
---

There are plenty of good reasons to move towards cloud, but mainly it make good business sense. Service like AWS Elastic MapReduce (EMR Cluster) and GCP DataProc makes life easy for the companies to maintain and extract intent from large data. 

In big data platform Lamda Architecture (LA) is a well-known concept for scalable and fault-tolerant data processing platform. Nathan Marz address the importans of [*‘vertically partitioned data’ – Big Data*](https://www.amazon.com/Big-Data-Principles-practices-scalable/dp/1617290343){:target="_blank"}

If you determine the requirement of big data storage the main thing is reliable and It is recommended to store the data as different partitioned (eg: daily, hourly partitioned). There are many advantages by partitioning vertically the data. One of the important scenario is while processing the data, if the extracted click stream data is corrupted after a deployment change due a bug it will be really easy to skip those corrupted partitioned than spending long hours to debug the large data. 

Therefore, during the migration process the biggest challenge is to move all the partitioned/non-partitioned HDFS data to Cloud buckets. Considering the migration process and to sync the data,

<figure style="text-align: center;">
	<a href="/articles/cloud-data-sync.png"><img src="/articles/cloud-data-sync.png" alt="image" style="width: 25%; height: 25%;"></a>
</figure>

Introducing: [**cloud-datasync**](https://github.com/Renien/cloud-datasync){:target="_blank"}


The cloud-datasync tool currently supports to incrementally copy the partitioned and bulk copy the non-partitioned data to GCP/AWS cloud data storage from any local linux/mac machines. These are new features I have planned for the tool,

* Using ‘distcp’ command effectively copy the data from local HDFS cluster to any cloud service 
* Automatically generate Azkaban job flow and schedule the data copy jobs in Azkaban servers. We can use [*Azkaban Python Package*](https://pypi.python.org/pypi/azkaban/0.6.43){:target="_blank"} to implement this feature.

Let me know what you think about ‘cloud-datasync’ below in the comments and share your thoughts. If you want to share any new features/issues, feel free to open an issue in the GitHub repository.

