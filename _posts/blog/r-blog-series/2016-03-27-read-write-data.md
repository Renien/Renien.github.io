---
layout: post
title: "Read/Write Data into ‘R’ Language"
description: "Reading and Writing data into R"
modified:
categories: blog
excerpt:
tags: [R Language,Data]
image:
  feature:
date: 2016-03-27T15:39:55-04:00
comments: true
share: true
---

### Read 

There are few basic functions available to read data into R.

* _read.table_, _read.csv_ - To read tabular data. These functions are most commonly used function to read the data.
* _readLine_ – To read the text files as each lines. This function can read any type of text files and will return a list of lines.
* _source_ – It's used to read the ‘R’ code. For example, if we want to read a R function from the file the _'source'_ function will be used to achieve it.
* _dget_ – This is also used to read the ‘R’ code but actually the R objects that are deparsed in to text files.  
* _load_, _unserialize_ – These functions are used to read the binary object into R.

> But there are different R packages developed to read different kind of other dataset. 

Mostly in these functions we need to set few arguments to read the data effectively and it will increase the performance while dealing with large datasets.

{% highlight r %}
read.table(file, header = FALSE, sep = "", quote = "\"'",
           dec = ".", numerals = c("allow.loss", "warn.loss", "no.loss"),
           row.names, col.names, as.is = !stringsAsFactors,
           na.strings = "NA", colClasses = NA, nrows = -1,
           skip = 0, check.names = TRUE, fill = !blank.lines.skip,
           strip.white = FALSE, blank.lines.skip = TRUE,
           comment.char = "#",
           allowEscapes = FALSE, flush = FALSE,
           stringsAsFactors = default.stringsAsFactors(),
           fileEncoding = "", encoding = "unknown", text, skipNul = FALSE)

read.csv(file, header = TRUE, sep = ",", quote = "\"",
         dec = ".", fill = TRUE, comment.char = "", ...)

read.csv2(file, header = TRUE, sep = ";", quote = "\"",
          dec = ",", fill = TRUE, comment.char = "", ...)

read.delim(file, header = TRUE, sep = "\t", quote = "\"",
           dec = ".", fill = TRUE, comment.char = "", ...)

read.delim2(file, header = TRUE, sep = "\t", quote = "\"",
            dec = ",", fill = TRUE, comment.char = "", ...)
{% endhighlight %}

### Write

* _write.table_ – To write tabular structure data to text files.
* _writeLines_ – To write data/set of characters in line by line to files.
* _dump_ – To dump a textual representation of multiple R objects.
* _dput_ – To output a textual representation of an R object.
* _save_ – To save objects (arbitrary number) into binary format.
* _serialize_ -  To convert objects into binary format.

{% highlight r %}
write.table(x, file = "", append = FALSE, quote = TRUE, sep = " ",
            eol = "\n", na = "NA", dec = ".", row.names = TRUE,
            col.names = TRUE, qmethod = c("escape", "double"),
            fileEncoding = "")

write.csv(...)
write.csv2(...)
{% endhighlight %}

The read/write parameters are mostly straightforward. But if you need more details of all the parameters for the functions, You can find the R manuals in this [**_Link_**](https://stat.ethz.ch/R-manual/R-devel/library/utils/html/){:target="_blank"}. 

### Blog Series
* [**Introduction to R Language**](/articles/introduction-to-r-language/)
* [**Hello R World**](/blog/hello-r-world/)
* [**R Fundamentals**](/blog/r-fundamentals/)
* Read/Write Data into ‘R’ Language
* [**Store data – Text/Binary Format**](/blog/store-data/)
* [**Manipulate Connections in ‘R’ Language**](/blog/connections/)