---
layout: post
title: "Life with Akka.io"
description: "Introduction to Akka.io"
modified:
categories: articles
excerpt:
tags: [scala,java,concurrency]
image:
  feature:
date: 2014-10-07T15:39:55-04:00
comments: true
share: true
---

In computer science, concurrency is a property of systems in which several computations are executing simultaneously, and potentially interacting with each other. Basically concurrency is good; it means we can do multiple things at once (parallelism, multitasking).

The problem of concurrency control is fundamental and independent of the various programming models that exist to express or provide concurrency: events, threads, and processes.

There are two types in concurrency,

* Shared-state concurrency
*	Message passing concurrency

Share-state concurrency was dominating for very long time, before the message passing concurrency was born. Today, both concurrency types are widespread in the programming world.

Now days, comparatively small applications are developed using shared-state concurrency with thread, lock and synchronized mechanism, where as large systems uses message passing concurrency concept.

###Share-state Concurrency

Shared-state Concurrency is concurrency among two or more processes which have some shared state between them; which both processes can read to and write from. Basically only one process read or writes at one time and while one process is doing their job rest will be queued for some time.

* Advantages
	* Can be very fast.
	* Makes much easier to achieve

* Disadvantages
	* Requires lots of synchronization primitives to avoid [**race-conditions**](http://msdn.microsoft.com/en-us/magazine/cc546569.aspx){:target="_blank"}
  * Does not scale well to distributed systems.
  * Especially in the presence of unreliable connections between processes which needs to be connected over the network.

###Message Passing Concurrency

Message passing concurrency is totally different from share-state concurrency. Basically there is no shared region in between the two processes. Instead each processes communicates each other by passing messages. In a real world scenario it’s like passing the ball (Processed content/Data) between two or more people.

* Advantages:
  * Easy to implement, using the model concept (Actors, Clusters)
  * Models distributed systems very well.
  * Remote models can be accessed through network very easily.
  * Each process has its own state which no other process may point to, So no need to worry about [**mutual exclusion**](http://en.wikipedia.org/wiki/Mutual_exclusion){:target="_blank"}
* Disadvantages
  * When model increases, there is a slightly chance to face a race-condition situation.
  * Can be slower compared to share-state concurrency.

[**Akka.io**](http://akka.io/){:target="_blank"} is framework that helps to develop and solve the concurrency problem-using message passing type.  Akka is built programming model for:

* Scale up (Concurrency)
* Scale out (Remoting)
* Fault tolerance

Akka can be scalable and help to develop large distributed systems. The core of Akka, akka-actor, is very small and can be easily implement into an existing project where you need asynchronicity and concurrency without any locks. So far I’m so impressed about Akka.io and I love the way it works concurrently without blocking each other processing jobs. To understand the concept and the theory I had to go through many learning circles. So l will try to explain in a series of blog-post with sample tutorial projects in near future.

###The Learning guide

<figure>
  <a href="/articles/akka-concurency.png"><img src="/articles/akka-concurency.png" alt="image" style="box-shadow: 5px 5px 2.5px #888888; margin: 0 0 10px 10px; max-width:200px;"></a>
</figure>
{: .pull-right}

Akka concurrency by Derek Wyatt is a great book. It helped me in many ways to understand Akka structure and the working flow.  More than that, Akka official [**documentation**](http://akka.io/docs/){:target="_blank"} is also written very well. If you’re interested to work on Akka, start with Akka concurrency book and then follow up with [**akka documentation**](http://akka.io/docs/){:target="_blank"} ☺.

###Blog Series
* Life with Akka.io
* [**Set Up Akka**](/blog/set-up-akka/)
* [**Akka Concurrency**](/blog/akka-concurrency/)
* [**Actor**](/blog/actor/)
* [**Actor System**](/blog/actor-system/)
* [**Supervision / Supervisor**](/blog/supervisor/)
* [**Being Stateful](/blog/being-stateful/)
