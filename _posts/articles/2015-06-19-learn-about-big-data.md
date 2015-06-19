---
layout: post
title: "Learn about Big Data"
description: "Big Data and Data Analyze"
modified:
categories: articles
excerpt:
tags: [Big Data,Hadoop,Lucene ]
image: 
  feature: 
date: 2015-06-19T15:39:55-04:00
comments: true
share: true
---

Big Data is one of the most buzzword in the recent years. The technology growth is currently ruling the word and it’s happened to be the key to handle huge data sets.

I got so attracted to these technologies and making me so crazy. The following list would be reference of the technologies I came across.  

<figure>
	<a href="/articles/bigdata-opensource-technology-stack.png"><img src="/articles/bigdata-opensource-technology-stack.png" alt="image" title="Big Data Technology Stack"></a>
	<figcaption><div style="text-align:center;">Big Data Technology Stack</div></figcaption>
</figure>


* **HDFS** is implemented to handle large set of data. Inaugural design is brought with the inspiration of the [**Google File System**](http://research.google.com/archive/gfs.html){:target="_blank"} (GFS). [**Apache Hadoop**](http://hadoop.apache.org/){:target="_blank"}, framework is build for distributed processing.  On HDFS to execute ELT (Extract, Load and Transform) jobs it uses [**MapReduce**](http://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html){:target="_blank"} and [**YARN**](http://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html){:target="_blank"}.

* **MapReduce** introduced by Google. They were internally implementing ETL jobs on huge data set and they published a [**Paper**](http://static.googleusercontent.com/media/research.google.com/en/us/archive/mapreduce-osdi04.pdf){:target="_blank"} that started it all. After google’s paper Amazon’s came up with their Hadoop instance of MapReduce is called [**Elastic MapReduce**](http://aws.amazon.com/elasticmapreduce/){:target="_blank"} (EMR).

* **Apache Spark** is emerging technology that vastly used by Big Data developers and Data Scientists. Spark deals the data with the concept of distributed data set, which is know as Resilient Distributed Dataset (RDDs). It includes not only MapReduce but also Spark SQL for SQL and structured data processing, [**MLlib**](https://spark.apache.org/docs/1.1.0/mllib-guide.html){:target="_blank"} for machine learning (ML), [**GraphX**](https://spark.apache.org/graphx/){:target="_blank"} for graph processing, and [**Shark**](https://spark.apache.org/sql/){:target="_blank"} Streaming.

* **Mahout** is very popular in the midst of Data Scientist. It bundles with collection list of machine learning libraries to analyze huge data set on Hadoop - [*https://mahout.apache.org/*](https://mahout.apache.org/){:target="_blank"}

* **Lucene** is mostly known as component to search indexing server. Because Lucene core has been used to develop the indexing search engine server. [**Lucene**](https://lucene.apache.org/){:target="_blank"} is bundle with NLP features that allows to indexing the linguistic data. [**Solr**](http://lucene.apache.org/solr/){:target="_blank"} is one of the most popular search engine-indexing servers, which uses Lucene Core. [**ElasticSearch**](https://www.elastic.co/){:target="_blank"} is also similar to Solr and it’s believed that ElasticSearch is much faster and pruned to work efficiently in any business domain.

* **Apache Pig** is a platform for analyzing huge data set on hadoop. It’s a high level language, which is easy to use without a prior programming knowledge - [*https://pig.apache.org/*](https://pig.apache.org/){:target="_blank"}

* **Hive** is SQL like data analyzing framework for big data on Hadoop. This language is called [**HiveQL**](https://hive.apache.org/){:target="_blank"}.

* **Apache Oozie** is a workflow scheduler to keep the track on ELT jobs/MapReduce Jobs - [*http://oozie.apache.org/*](http://oozie.apache.org/){:target="_blank"}

* **Azkaban** is also similar to Oozie. It’s a batch workflow scheduler. Its developed by linkedIn - [*https://azkaban.github.io/*](https://azkaban.github.io/){:target="_blank"}

* **Apache Sqoop** is a tool to transfer data from Hadoop to structured data stores - [*http://sqoop.apache.org/*](http://sqoop.apache.org/){:target="_blank"}

* **Hue** is a web application interface for Hadoop - [*http://gethue.com/*](http://gethue.com/){:target="_blank"}

* **Apache HBsae** is a column-oriented distributed data store. The cell is where HBase stores data as a value. A cell is identified by its [rowkey, column family, column qualifier] coordinate within a table. Its design and develop is inspired by google’s BigTable


The above lists are incomplete and always will be in the IT world. In future I’ll try to discuss more in detail about each of these technologies.


