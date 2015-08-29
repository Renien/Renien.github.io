---
layout: post
title: "Supervision / Supervisor"
description: "The Akka application and the Actor model are well known for resiliency."
category: blog
tags: [Akka.io, scala, Concurrency, Supervision, Crash, fault-tolerant]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

The Akka application and the Actor model are well known for resiliency. In large application one of the major challenge is to handle the failures and to keep alive the application. It’s like in real life when we are hurt and broken down their will always some one with us to overcome from our failures. The same thing happens in Akka System. Actor model come to your rescue when it comes to your system failures.

In this post we are going to look in to Akka Supervision. The supervision is handled with Actor life cycle, because it has been design in such away.

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/supervison.jpg"><img src="/blog/akka-blog-series/supervison.jpg" alt="image"></a>
  <figcaption>Figure 1 - Akka Supervision</figcaption>
</figure>

##What is a supervisor?

Supervisor is like an attribute for Actor model that will take care of the children that are created within their **_Context_**. To achieve this task we need to implement a piece of code that includes the supervise strategy. The default implementation will looks like this:

{% highlight scala %}
final val supervisorStrategy = OneForOneStrategy() {
 case _: ActorInitializationException  => Stop
 case _: ActorKilledException => Stop
 case _: Exception => Restart
 case _ => Escalate
}
{% endhighlight %}

So now we can see once the exception is thrown in the child actor it will be passed to (**_Figure 1_**) the parent actor which is the supervise actor.  During that time the **_supervisorStrategy_** will capture the message and decide what needs to be done to child actor (Stop or Restart).

* Escalate message basically will pass the exception message to the supervisor’s parent.

There are two type of supervisorStrategy :

* **_OneForOneStrategy() :_** This strategy dealts with on one-for-one-basic action. When an Actor is failed the decision of the supervisor is given to the injured/failed actor.   
* **_AllForOneStrategy() :_** This strategy is contrast to OneForOneStrategy(). Though it’s a single child actor failure, the decision that made by the supervisor will be applied to all the children actors.

> SupervisorStrategy helps keep an Actor Application fault-tolerant

In Actor model to change the life cycle there are certain methods provided that can be overridden and use it to do our operations. These are some of the methods that helps to execute some jobs within the failing Actor.

* **_preStart() :_** Can perform any initialization methods here that need to be executed before to achieve the main task. During this stage we can send messages to the actor itself. Eg: self ! Initialize 
* **_postStop() :_** Once the actor is ready to stop, can use the method to finalize some activities. Eg: Close the session or clean up the data.
* **_postRestart() :_** After a injury  once the actor model is restarted using this method we can execute some activates. Eg: Inform an actor that I’m back to normal state.
* **_preRestart() :_** After a injury  before the actor model is up and live can use this method to achieve some task that are used by the actor before it’s failure. Eg: Connect to the data base or create a new session. 

Now lets take the same previous example but with some slight modification in Family Hierarchy (**_Figure 2_**).  In family when sons and daughters are broken down parents are the first people to notice and to help them. It’s obvious mostly sons are attached to mother and daughters are to their father. Therefore lets create our actor models as follows.

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/actor-family-members-supervision.jpg"><img src="/blog/akka-blog-series/actor-family-members-supervision.jpg" alt="image"></a>
  <figcaption>Figure 2 - Family Members (Mom & Dad - Supervisors)</figcaption>
</figure>

Now we can see Sons (Petter & Roy) are under Mother’s (Mary) supervision and daughters (Sally & Victoriya) are under Father’s (John) supervision. Therefore now Mary and John Actor models need to be implemented with supervisor strategy and also the children need to be created under their context. I’ll be using the **_preStart()_** method to crate the child actors.

{% highlight scala %}
//preStart() method from Father Actor
@scala.throws[Exception](classOf[Exception])
  override def preStart(): Unit = {
    //Daughters are under father
    val numberOfDaughters: Int = 2
    val daughtersNames = context.system.settings.config.getStringList(
      "akka.apartment.familyMembers.daughtersNames").asScala
    daughtersNames take numberOfDaughters foreach { dName =>
      context.actorOf(Props[Daughter], dName)
    }
  }

//preStart() method from Mother Actor
@scala.throws[Exception](classOf[Exception])
  override def preStart() = {
    //Sons are under Mother
    val numberOfSons: Int = 2
    val sonsNames = context.system.settings.config.getStringList(
      "akka.apartment.familyMembers.sonsNames").asScala
    sonsNames take numberOfSons foreach { sName =>
      context.actorOf(Props[Son], sName)
    }
  }
{% endhighlight %}

In this example we’ll be using the default action in the supervisorStrategy and we will try to **_restart_** and **_stop_** the child actors. In our Daughter Actor model we are going to **_throw Exception_** to crash the model. During the failure Father Actor model will Restart the failing actor. 

{% highlight scala %}
override def receive: Receive = {
    case Injured(message) => throw new Exception //make it crash
  }
{% endhighlight %}

Now once the actor model bounce back to live we are going to use **_preRestart(reason: Throwable, message: Option[Any])_** method to inform parent Actors. 

{% highlight scala %}
//preRestart method of Daughter Actor 
@scala.throws[Exception](classOf[Exception])
  override def preRestart(reason: Throwable, message: Option[Any]): Unit = {
    context.parent ! Cured(self.path.name +": I'm Fine Dad!!!!!!")
  }

//preRestart method of Son Actor
@scala.throws[Exception](classOf[Exception])
  override def preRestart(reason: Throwable, message: Option[Any]): Unit = {
    context.parent ! Cured("I'm Fine Mom!!!!!!")
  }
{% endhighlight %}

Hence, once the failed actors are restarted it will execute the **_preRestart_** method. After executing the code you will understand the full flow of the Actor life cycle by looking at the log file.

I have discussed the entire important new code portion from our example. Now let’s send the messages to crash the child actor so that parent can Restart or Stop the crashing model. In this tutorial we are going to **_Kill/Stop_** Son actor and to **_Restart_** a Daughter actor.

{% highlight scala %}
val sally  = system.actorSelection("akka://family/user/familyMembers/John/Sally") //Daughter: Sally
val roy = system.actorSelection("akka://family/user/familyMembers/Mary/Roy") //Son: Roy
roy ! Kill                              //Kill the son
sally ! InjuredMessage.Injured("Crash") //Crash the daughter
{% endhighlight %}

You will be wondering about the **_Kill_** message which is defined Akka. Basically when Kill message is passed to an actor it will **_throw ActorKilledException_**. Therefore according to our supervisorStrategy implementation the failing actor will be stopped by the supervisor.

After running the sample application (TestSupervisor) the log file will be as follows,

{% highlight console  %}
[ERROR] [08/29/2015 21:05:01.609] [family-akka.actor.default-dispatcher-2] [akka://family/user/familyMembers/Mary/Roy] Kill (akka.actor.ActorKilledException)
[ERROR] [08/29/2015 21:05:01.609] [family-akka.actor.default-dispatcher-9] [akka://family/user/familyMembers/John/Sally] null
java.lang.Exception
	at com.tutorial.supervisor.Daughter$$anonfun$receive$2.applyOrElse(Children.scala:31)
	at akka.actor.Actor$class.aroundReceive(Actor.scala:467)
	at com.tutorial.supervisor.Daughter.aroundReceive(Children.scala:23)
	at akka.actor.ActorCell.receiveMessage(ActorCell.scala:516)
	at akka.actor.ActorCell.invoke(ActorCell.scala:487)
	at akka.dispatch.Mailbox.processMailbox(Mailbox.scala:238)
	at akka.dispatch.Mailbox.run(Mailbox.scala:220)
	at akka.dispatch.ForkJoinExecutorConfigurator$AkkaForkJoinTask.exec(AbstractDispatcher.scala:397)
	at scala.concurrent.forkjoin.ForkJoinTask.doExec(ForkJoinTask.java:260)
	at scala.concurrent.forkjoin.ForkJoinPool$WorkQueue.runTask(ForkJoinPool.java:1339)
	at scala.concurrent.forkjoin.ForkJoinPool.runWorker(ForkJoinPool.java:1979)
	at scala.concurrent.forkjoin.ForkJoinWorkerThread.run(ForkJoinWorkerThread.java:107)

[DEBUG] [08/29/2015 21:05:01.609] [family-akka.actor.default-dispatcher-9] [akka://family/user/familyMembers/John/Sally] restarting
[DEBUG] [08/29/2015 21:05:01.611] [family-akka.actor.default-dispatcher-3] [akka://family/user/familyMembers/Mary/Roy] stopped
Sally: I'm Fine Dad!!!!!!
[DEBUG] [08/29/2015 21:05:01.628] [family-akka.actor.default-dispatcher-9] [akka://family/user/familyMembers/John/Sally] restarted 
...........
{% endhighlight %}

We can see in the printed log **_Sally_** Actor was restarted and **_Roy_** Actor stopped by the supervisor.

To download the sample code : [**Download**](https://github.com/Renien/akka-tutorials){:target="_blank"}

###Blog Series
* [**Life with Akka.io**](/articles/life-with-akka/)
* [**Set Up Akka**](/blog/set-up-akka/)
* [**Akka Concurrency**](/blog/akka-concurrency/)
* [**Actor**](/blog/actor/)
* [**Actor System**](/blog/actor-system/)
* Supervision / Supervisor
