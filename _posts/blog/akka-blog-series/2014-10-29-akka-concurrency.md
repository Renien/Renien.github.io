---
layout: post
title: "Akka Concurrency"
description: "Akka Concurrency"
category: blog
tags: [Akka.io, scala, Concurrency, Actor, Mailbox, Dispatcher]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

Akka is a toolkit designed to building scalable, fault-tolerant applications on the JVM. It provides many components to achieve our goals.

###The Actor

When we start looking at Akka containers, it’s the

> Actor

That’s come in front of us first. The Actor does a major role in Akka systems, due to its flexibility, location independence and fault- tolerant behavior.

Obviously, our world is full of concurrency. Think about your self and your working environment at office. At office your hired to do a particular job and your boss and core-workers impose with different types of work on you. Hence, you will some how manage this literally doing only one thing at a time.

> Its obvious, we like to pretend that we can multi-task ;)

But it’s not true at all. We just plan our work according to priority level and we do just that one work at a time. If you feel bored with one particular work and deadline is near (priority increases) to another work. We will pause the current task and start working on a different task. If needed resume it later.

So what if we want to do more than one thing at a time? The answer is pretty obvious:

> We just use more than one person.

So basically to achieve big goals we should end up with teamwork.

> “Alone we can do so little; together we can do so much” ― Helen Keller

###Message Passing

Like we previously discussed your working as Developer at a software company. To implement and produce a software product application you will get assign to task by coworkers and meantime you will try to do other tasks as well.(**Figure 1**).

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/akka-actor-message passing.png"><img src="/blog/akka-blog-series/akka-actor-message passing.png" alt="image"></a>
  <figcaption>Figure 1 - Message passing in development enviorment</figcaption>
</figure>


Once you assign to a job then you will do the task perfectly but in mean time if you need a input from other core workers you will pause and wait until you get their signal message with relevant input through email.

> Actors - Doing One Thing at a Time

Like our day-to-day life experiences; Akka actors are design to do one thing at a time. If you want to have more than one thing happen simultaneously, then you need to create more than one Actor to do that work.

If you’re sending a set of jobs to be done to a specific actor, it will be in queue. Then according to our concurrency model implementation (eg: Round Robin, Simple Mail Box) actor will does the job very neatly.

Akka actor consist of mailbox and dispatcher in its own world. But if you need to write a custom **mailbox** and **dispatcher** Akka provide that freedom too. **Figure 2** provides a general idea about Akka actor structure.

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/akka-queue.png"><img src="/blog/akka-blog-series/akka-queue.png" alt="image"></a>
  <figcaption>Figure 2 - Message queue</figcaption>
</figure>

According to your mailbox implementation the messages come into a mailbox through and this allows the caller to do other jobs and doesn’t need tie up on waiting thread.

The **enqueue** operation wakes up the **dispatcher** who sees that there’s a new message for the Actor to process. But in the scenario of **Figure 2** since Actor is processing a job **dispatcher** doesn’t have a job but if the **dispatcher** is configured with a concurrency model along with many actors it will send the message to the relevant actor.

Actor does its processing job in its own world. Hence, its not effected with other Actors or messages, which are queued. Once the Actor finish processing the message it will automatically signal the dispatcher and then it can **dequeue** the next message from mailbox and give it to the Actor to start the job again.

This is the abstract of **Akka Concurrency**. But there are many things in akka concurrency and we will look in to depth with sample code in my next blog. Hopefully this post has demonstrated and gave a ground level introduction about Akka Actor.



###Blog Series
* [**Life with Akka.io**](/articles/life-with-akka/)
* [**Set Up Akka**](/blog/set-up-akka/)
* Akka Concurrency
* [**Actor**](/blog/actor/)

