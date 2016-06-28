---
layout: post
title: "Exclude particular fields from SELECT queries in Hive"
description: "In Hive SELECT queries aviod particular fields"
category: blog
tags: [BigData, Hive, MapReduce]
image:
  feature: 
  credit:
  creditlink:
comments: true
share: true
---

Hive is a high level language to analyse large volumes of data. The easiest way to select specific columns in Hive query is by specifying the column name in the select statement.

{% highlight sql %}
SELECT col1, col3, col4 .... 
FROM Table1;
{% endhighlight %}

But imagine your table contains many columns (i.e : more than 100 columns) and you need to only exclude a few columns in the select statement. Therefore, Hive query should be able to select all the columns excluding the defined columns in the query. To achieve it you need to follow these steps.

In _‘hive-site.xml’_ add the following configuration,

{% highlight bash %}
hive.support.quoted.identifiers=none
{% endhighlight %}

and execute the query as 

{% highlight sql %}
SELECT `(extract_date)?+.+` FROM <TABLE_NAME>;
{% endhighlight %}

with appropriate column and table name.

_i.e_ Think you need to exclude only _‘transaction_date’_ column in a select statement from a _‘cart’_ table. Then the query will be,

{% highlight sql %}
SELECT `( transaction_date)?+.+`
FROM cart;
{% endhighlight %}
