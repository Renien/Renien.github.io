---
layout: post
title: "Installing Tools"
description: "Installing tools for scala development"
category: blog
tags: [tools, scala, java, intellij]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

At the time of this post Scala has been grown for a stable stage and the latest version of Scala is 2.11.2.

We can download the latest release from [**scala download**](http://www.scala-lang.org/downloads){:target="_blank"} where we’ll find download packages for different operating systems. There are 3 ways to install scala but I like to create my scala projects using [**Typesafe Activator**](){:target="_blank"}. Typesafe Activator is a browser-based or command-line
tool that helps developers get started with Scala quickly.


###Installing binaries  

[**Simply download**](http://downloads.typesafe.com/scala/2.11.2/scala-2.11.2.tgz?_ga=1.182497573.2099955192.1408334166){:target="_blank"} the binaries and unpack the archive

Now to quickly access, add scala and scalac to path variables.

| Environment | Variable | Value (example) |
|:--------|:-------:|--------:|
| Unix   | $SCALA_HOME   | /usr/local/share/scala   |
|        | $PATH         | $PATH:$SCALA_HOME/bin   |
|----
| Windows   | %SCALA_HOME%   | c:\Progra~1\Scala   |
|           | %PATH%   | %PATH%;%SCALA_HOME%\bin   |
|=====
{: rules="groups" class="gridtable" }

Open your terminal and type scala it will change to scala interactive interpreter (**Figure 1**). Now that we are ready, can try some single line of Scala code like arithmetic expression and enjoy the beauty of scala ☺.
Eg :- 2+3 = 5

<figure>
	<a href="/blog/scala-arithmetic.png"><img src="/blog/scala-arithmetic.png" alt="image"></a>
	<figcaption>Figure 1 : interactive interpreter</figcaption>
</figure>

###Typesafe Activator

The Typesafe Reactive Platform provides developers with the most powerful tools to build modern applications that react to events, react to load, react to failure, and react to users. Typesafe Reactive Platform consist of these following popular frameworks

* [Play Framework](https://playframework.com/){:target="_blank"}
*	[Akka](http://akka.io/){:target="_blank"}
*	[Scala](http://scala-lang.org/){:target="_blank"}
*	[Spark](https://spark.apache.org/){:target="_blank"}
*	[The highly reactive build tool –sbt (Simple Build Tool)](https://github.com/sbt/sbt){:target="_blank"}

All these technology are bundle together and the platform is distributed through Typesafe Activator, a browser-based tool that includes easy-to-use templates and tutorials.  To install Typesafe Activator watch the following video:

<iframe width="560" height="315" src="//www.youtube.com/embed/phFsLsvzBvY" frameborder="0" allowfullscreen></iframe>

Once it’s up and running use command or browser application to create scala template and start to work on it.

###Editor
Scala project can be setup on Eclipse but I would recommend to work on IntelliJ IDEA . It has a great support with scala and sbt build tool.

To work on IntelliJ IDEA we need to install the scala plugin. To install scala plugin follow the step (**Figure 2**) and you will be able to install the plugin successfully.

Click the Preference **(1)** button and Preference Window **(2)** will be opened. In preference window select Plugin **(3)** from the list and press Install Jetbrains plugin **(4)**. Now a new Plugins window **(5)** will be open from it search for Scala plugin **(6)** using the plugin search bar. That’s it , after selecting the scala plugin in right panel Install **(7)** button will appear. Since I have already installed the scala plugin it’s not visible on the screen shot.


<figure>
  <a href="/blog/intellij-IDEA.png"><img src="/blog/intellij-IDEA.png" alt="image"></a>
  <figcaption>Figure 2 : Installation steps</figcaption>
</figure>

Well, now we are ready with development environment ☺. Lets start with our mandatory “Hello World” program :D.

###Blog Series
* [**Introduction to Scala**](/articles/introduction-to-scala/)
*	Installing Tools
* [**Hello Scala World**](/blog/hello-scala-world/)
* [**Scala Code**](/blog/scala-code/)
* [**Classes and Objects**](/blog/classes-and-objects/)

<!-- CSS goes in the document HEAD or added to your external stylesheet -->
<style type="text/css">
table.gridtable {
	//font-family: verdana,arial,sans-serif;
	//font-size:11px;
	color:#333333;
	border-width: 1px;
	border-color: #666666;
	border-collapse: collapse;
  width:100%;
}
table.gridtable th {
	border-width: 1px;
	padding: 8px;
	border-style: solid;
	border-color: #666666;
	background-color: #dedede;
}
table.gridtable td {
	border-width: 1px;
	padding: 8px;
	border-style: solid;
	border-color: #666666;
	background-color: #ffffff;
}
</style>
