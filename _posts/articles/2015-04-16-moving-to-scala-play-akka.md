---
layout: post
title: "Moving to Scala | Play | Akka | Life is becoming more fascinating"
description: "Fault tolerance reactive application"
modified:
categories: articles
excerpt:
tags: [Scala,Play,Akka]
image:
  feature:
date: 2015-04-15T15:39:55-04:00
comments: true
share: true
---

For very long time I was die-hard fan of all the Microsoft technologies. My world was so elegant and beautiful with so many variation of languages C#, VB, F# etc. But coding life got more excited after experiencing Play, Akka.io and Scala, a beautiful language that can run in JVM.

For couple of months I was under serious production development where I couldn’t finish my Scala and Akka blog series. Sorry about that I will try my best to find some free time and finish the blog-tutorials.  Though I had so many prioritized works in the pipeline I forced my self to share my happiness on certain technologies because they mesmerize me.

<figure style="text-align: center;">
	<a href="/articles/technology-love.jpg"><img src="/articles/technology-love.jpg" alt="image" style="
    width: 35%;
    height: 35%;"></a>
</figure>

> So much love #Scala #Play #Akka

We started a proof of concept Search Engine project where it happens to be attracted by the clients. Initially for a quick development and to implement mathematical models we started on with Python and ended with Python web application where we exposed an API to provide the search results. During the demo it was perfect but as a product we always need to consider the load and the number of request sent by the users and a lot more. Hence, obviously it failed to balance the load and to return the search result properly in the production environment.

During this time we started our investigation and found the life saving technology [**Akka.io**](http://akka.io/){:target="_blank"} and [**Scala**](http://www.scala-lang.org/){:target="_blank"}**-**[**play framework**](https://www.playframework.com/){:target="_blank"} in [**Typesafe**](https://typesafe.com/){:target="_blank"} stack. Starting is always a bit hard with our limited time frame. We were under big pressure but at the end we all were so happy and proud when we look at our end product. 

<figure style="text-align: center;">
	<a href="/articles/so-much-win.jpg"><img src="/articles/so-much-win.jpg" alt="image"></a>
</figure>

Play and Akka.io can be used using java but why going back to old school again? Scala is flexible. Flexibility comes at the price of simplicity, but in the right hands Scala is a very elegant language that is much more than just a “better Java”.

<figure style="text-align: center;">
	<a href="/articles/no-code-errors.jpg"><img src="/articles/no-code-errors.jpg" alt="image" style="
    width: 35%;
    height: 35%;"></a>
</figure>

> Its all about the programing and passion towards it

Akka drive me beyond my limitation and forced me to think differently to solve so many load-balancing problems in the context of concurrency programming. During the learning process felt so much proud as being a programmer and [**Jonas Bonér**](http://jonasboner.com/){:target="_blank"} inspired me a lot.

At the end it’s a happy ending for us too and believe me Akka.io helped me to think totally in different perspective. We were able to implement a fault tolerance reactive web application built underneath on Akka. The beauty is we still use our core search engine (developed by python) wrapped by Akka actor and replicated under akka actor system environment as separate nodes. But slowly we are moving the python search engine core components to scala with the help of [**Scala NLP**](http://www.scalanlp.org/){:target="_blank"}.

<figure class="half" style="text-align: center;">
	<a href="/articles/team-cry.jpg"><img src="/articles/team-cry.jpg" alt="image" ></a>
    <a href="/articles/challenge-accepted.jpg"><img src="/articles/challenge-accepted.jpg" alt="image"></a>
	<figcaption>Then & Now: How the technology transfromed our team from 'worriers' into 'believers'</figcaption>
</figure>


These trending technologies are not another usual technology component. Remember when developing web application these technologies will be suitable solution for the enterprise application — and already in the enterprise — **now!**


