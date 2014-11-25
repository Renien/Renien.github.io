---
layout: post
title: "Accessing PySpark in PyCharm"
description: "Accessing PySpark in PyCharm"
category: blog
tags: [hadoop, spark, python, bigdata, scala, java]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---
    
Apache Spark is big data powerful communication component to analyzing and data manipulations.  

In my previous [(**Installing PySpark - SPARK**)](/blog/installing-pyspark/) blog we discussed about to build and successfully run PySpark shell. But for development the PySpark module should be able to access from our familiar editor.


<figure style="text-align: center;">
  <a href="/blog/pyspark-preference-reference.png"><img src="/blog/pyspark-preference-reference.png" alt="image" style="box-shadow: 5px 5px 2.5px #888888; margin: 0 10px 10px 0px; max-width:200px;"></a>
  <figcaption>Figure 1 - PySpark Reference</figcaption>
</figure>
{: .pull-left}

Initially I tried with PyCharm Preference setting and added the PySpark module as an external library (**Figure 1**). But the editor couldn’t resolve the reference (**Figure 2**). Hence, ended up with adding the reference during the Python script runtime. 

<figure style="text-align: center;">
  <a href="/blog/pyspark-reference-problem.png"><img src="/blog/pyspark-reference-problem.png" alt="image" style="box-shadow: 5px 5px 2.5px #888888; margin: 0 0 10px 10px; max-width:200px;"></a>
  <figcaption>Figure 2 - Reference Problem</figcaption>
</figure>
{: .pull-right}

<br><br><br><br>

Go through the following below code and add the appropriate **SPARK HOME** directory and **PYSARK folder** to successfully import the Apache Spark modules.

{% highlight python %}
import os
import sys

# Path for spark source folder
os.environ['SPARK_HOME']="your_spark_home_folder"

# Append pyspark  to Python Path
sys.path.append("your_pyspark_folder ")

try:
    from pyspark import SparkContext
    from pyspark import SparkConf

   print ("Successfully imported Spark Modules")

except ImportError as e:
    print ("Can not import Spark Modules", e)
    sys.exit(1)
{% endhighlight %}

After executing the code it should print **"Successfully imported Spark Modules"** (**Figure 3**).

<figure style="text-align: center;">
  <a href="/blog/successfully-import-pyspark.png"><img src="/blog/successfully-import-pyspark.png" alt="image"></a>
  <figcaption>Figure 3 - Successfully import pyspark</figcaption>
</figure>

Now lets write a small spark task to check whether PySpark works. Add the following code after importing PySpark module and run the code (**Figure 4**).

{% highlight python %}
# Initialize SparkContext
sc = SparkContext('local')
words = sc.parallelize(["scala","java","hadoop","spark","akka"])
print words.count()
{% endhighlight %}

<figure style="text-align: center;">
  <a href="/blog/successfully-run-pyspark.png"><img src="/blog/successfully-run-pyspark.png" alt="image"></a>
  <figcaption>Figure 4 - Test pyspark</figcaption>
</figure>

