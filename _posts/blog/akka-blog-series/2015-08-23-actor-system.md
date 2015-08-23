---
layout: post
title: "Actor System"
description: "Like in large organisation actors form hierarchies."
category: blog
tags: [Akka.io, scala, Concurrency, Actor, Path, Erlang]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

Like in large organisation actors form hierarchies. In my previous [**Actors post**](/blog/akka-concurrency/) we discussed a bit on hierarchy. The **_Figure 1_** shows the tree hierarchy structure while creating actors. Therefore each actor will always contain a parent actor, which is a supervised actor. We will take supervise actor in a separate post and discuss.

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/akka-hierarchical-structure.jpg"><img src="/blog/akka-blog-series/akka-hierarchical-structure.jpg" alt="image"></a>
  <figcaption>Figure 1 - Akka Hierarchical Structure</figcaption>
</figure>

The main objective of this above tree hierarchy structure is to make small process components (micro level services). It has a big benefit of handling the failures in their parent level.  Therefore it will allow us to keep our application alive.

The top-level actors are lived within the **_Error Kernel layer_**. So until it reaches to the top-level actors the fully scaled application won’t shutdown. This pattern is extracted from **_Erlang Theories_**.

Through out our blog series we’ve seen several time and discussed about accessing the actors. Lets look in to deep on Actor selection and the path. 

> Actor System occupies a main role in Akka application. 

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/actor-system.jpg"><img src="/blog/akka-blog-series/actor-system.jpg" alt="image"></a>
  <figcaption>Figure 2 - Actor System features</figcaption>
</figure>

Everything is build up from ActorSystem. In **_Figure 2_** shows the thing that ActorSystem is focusing.

* **_Dead Letter Office :_** It's an another Actor that lives within ActorSystem. This actor is created by Akka. In case if actors find any communication problems (A actors is not exist or not running), the message will ends up with Dead Letter Office.

* **_System Guardian Actor :_** These actors are not created by us. It will be created by Akka internally to coordinate the whole system.

* **_User Guardian Actor :_** We are now concern about actors. They can’t independently stay in Akka application.  It will exist under a parent. Hence, User Guardian Actor is the parent of all Actors that we create from ActorSystem (using ActorSystem.actorOf() method)

* **_Event Stream :_** This components lives on ActorSystem and it’s mainly used to log the messages.  

* **_Scheduler :_** When ever we create a scheduler that will created on ActorSytem.

* **_Setting :_** All the setting and configuration for the System can be accessed using ActorSystem.

> All these guardian actors are living to build the **_resiliency_** in the system.

When we are creating the **_“family”_** ActorSystem the User Guardian Actor is created.

{% highlight scala %}
val system = ActorSystem("family")
{% endhighlight %}

So if we need to travel through the tree to access the Actor, the **_parent-child_** relationship should be placed in the **_path_**. 

`/user/{parent}/{child}`  

##Actor Paths

The URL pattern is standard through the Akka application. For an example we are creating **_“mother”_** Actor, so the expaned URL path will be,

`Akka://family/user/mother` 

If we are dealing with only single ActorSystem (lives on only in one machine), the location and port information won’t be useful. But when we are creating Clusters in Akka, machine information is essential.  To access a remote machine and remote Actors the URL needs to be included with **_HOST, PORT_**.

`Akka://family@{host}:{port}/user/mother` 

Now lets take the family members example again and expand it (**_Figure 3_**).  

<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/actor-family-members.jpg"><img src="/blog/akka-blog-series/actor-family-members.jpg" alt="image"></a>
  <figcaption>Figure 3 - Family Members</figcaption>
</figure>

To implement in much more nicely we will use **HOCON** (Human-Optimized Config Object Notation) configuration specification. So lets add our entire actor configuration in `src/main/resources.conf` file.

{% highlight apacheconf  %}
akka{
  apartment{
    securityGuardName = "Vikey"
    familyMembers{
      motherName = "Mary"
      fatherName = "John"
      sonsNames = ["Roy", "Petter"]
      daughtersNames = ["Sally", "Victoriya"]
    }
  }
}
{% endhighlight %}

It’s very challenging task to test the micro level services. But Akka provides us to log all the flow by adding the following configuration,

{% highlight apacheconf  %}
{
 loglevel = DEBUG
   actor {
     debug {
       lifecycle = on
     }
}
{% endhighlight %}

Therefore when we run it will log all the operations: 

{% highlight console  %}
[DEBUG] [08/23/2015 19:44:51.643] [family-akka.actor.default-dispatcher-4] [akka://family/system] now supervising Actor[akka://family/system/deadLetterListener#2131296836]
[DEBUG] [08/23/2015 19:44:51.645] [family-akka.actor.default-dispatcher-2] [akka://family/system/deadLetterListener] started (akka.event.DeadLetterListener@35cc941)
[DEBUG] [08/23/2015 19:44:51.658] [family-akka.actor.default-dispatcher-3] [akka://family/user] now supervising Actor[akka://family/user/familyMembers#-452406400]
[DEBUG] [08/23/2015 19:44:51.660] [family-akka.actor.default-dispatcher-4] [akka://family/user/familyMembers/Mary] started (com.tutorial.actorSystem.Mother@20318ba1)
...........
{% endhighlight %}


In this example **_familyMembers_** is a supervisor to all the child nodes/members. Since now actor configurations are provided in the conf file and to get the conf details the implementation will be like this:

{% highlight scala %}
motherName = Option(context.system.settings.config.getString(
      "akka.apartment.familyMembers.motherName"))
    context.actorOf(Props[Mother], motherName.get)
{% endhighlight %}

When comparing to the previous sample code the additional actors are the supervised actor and several child actors. 

In this example code I have used two ways to select the actors.

* context.actorSelection()
{% highlight scala %}
context.actorSelection(message) //FamilyMember.scala class line 62
{% endhighlight %}
* Storing the actorRef object 
{% highlight scala %}
fatherActor.get //FamilyMember.scala class line 63
{% endhighlight %}

I hope now you would have got a pretty good idea about the ActorSystem, actor hierarchy and the structure. In our next blog we will see how the fault tolerance is handled and implemented.  

To download the sample code : [**Download**](https://github.com/Renien/akka-tutorials){:target="_blank"}

###Blog Series
* [**Life with Akka.io**](/articles/life-with-akka/)
* [**Set Up Akka**](/blog/set-up-akka/)
* [**Akka Concurrency**](/blog/akka-concurrency/)
* [**Actor**](/blog/actor/)
* Actor System
