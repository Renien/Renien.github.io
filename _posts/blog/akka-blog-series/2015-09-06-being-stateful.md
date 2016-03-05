---
layout: post
title: "Being Stateful"
description: "In this post lets explore another Actor features that provide us to be a stateful actor."
category: blog
tags: [Akka.io, scala, Stateful, Behaviours]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

So far we have discussed about actors and actor supervision that leads us to keep the system alive.  In this post lets explore another Actor feature that provide us to be a stateful actor. It basically let us to change an Actor’s running behavioural state while message is processed. So we can change the way it reacts to future messages in any way we want. Hence, this will help us to change the behaviour of our actors based on its internal state.

Now lets take our Family ActorSystem example and try to understand. Son (Roy) is addicted to junk food. When Mother (Mary) realize that her son ate junk food she always goes crazy and shouts at him. So we can see Mother’s behaviour is changing according to her son’s state (**_Figure 1_**).


<figure style="text-align: center;">
  <a href="/blog/akka-blog-series/mother-son-emotion-state.jpg"><img src="/blog/akka-blog-series/mother-son-emotion-state.jpg" alt="image"></a>
  <figcaption>Figure 1 - Mother & Son Actor Communication</figcaption>
</figure>

Like in **_Figure 1_** we will come across so many situation in our application domain. Therefore, to handle these situation the primary way that Akka let us to modify the actor behaviour is by simply using the ActorContext’s **_become()_** and **_unbecome()_** methods.

To handle the two behaviours in Mother Actor the two following **_Receive_** methods are implemented.

{% highlight scala %}
override def receive: Receive = {
    case Conversation(message) => {
      message match
      {
        case Son1 => {
          println(s"${sender().path.name} : " + message)
          sender() ! Conversation(FamilyMemberMessage.message("Mom1"))
        }
        case Son2 => {
          println(s"${sender().path.name} : " + message)
          context.become(angryConversation)
          sender() ! Conversation(FamilyMemberMessage.message("Mom2")) }
      }

    }
  }

  def angryConversation: Receive = {
    case Conversation(message) => {
      message match
      {
        case Son3 => {
          println(s"${sender().path.name} : " + message)
          sender() ! Conversation(FamilyMemberMessage.message("Mom3"))
        }
        case Son4 => {
          println(s"${sender().path.name} : " + message)
          sender() ! Conversation(FamilyMemberMessage.message("Mom4"))
        }
      }

    }
  }
{% endhighlight %}

And also the Son Actor’s **_Receive_** methods will be as follow,

{% highlight scala %}
override def receive: Receive = {
    case Conversation(message) => {
      message match {
        case Son1 => {
          context.parent ! Conversation(message)
        }
        case Mom1 => {
          println(s"${sender().path.name} : " + message)
          sender() ! Conversation(FamilyMemberMessage.message("Son2"))
        }
        case Mom2 => {
          println(s"${sender().path.name} : " + message)
          context.become(sadConversation)
          sender() ! Conversation(FamilyMemberMessage.message("Son3"))
        }
      }
    }
  }

  def sadConversation: Receive = {
    case Conversation(message) => {
      message match
      {
        case Mom3 => {
          println(s"${sender().path.name} : " + message)
          sender() ! Conversation(FamilyMemberMessage.message("Son4"))
        }
        case Mom4 => {
          println(s"${sender().path.name} : " + message)
          println("Conversation Ends")
        }
      }

    }
  }
{% endhighlight %}

By executing the sample application, we can see how the behaviours are changed in the Actor model.

{% highlight console  %}
...........
[DEBUG] [09/06/2015 14:10:52.348] [family-akka.actor.default-dispatcher-7] [akka://family/user/familyMembers/Mary/Petter] started (com.tutorial.stateful.Son@4525a40d)
Roy : Mom, I just now came home
Mary : Roy come lets have our dinner
Roy : I'm full, I had my dinner
Mary : What did you eat ?
Roy : Sorry mom, I had junk food :(
Mary : What's wrong with you! :@ How many times I have told you not to eat junk food
Roy : I'm very sorry I won't eat again
Mary : I have told yo so many times. Now you're groudned for two weeks (EVIL SMILE)
Conversation Ends
[DEBUG] [09/06/2015 14:10:52.978] [family-akka.actor.default-dispatcher-8] [akka://family/user] stopping
[DEBUG] [09/06/2015 14:10:52.978] [family-akka.actor.default-dispatcher-7] [akka://family/user/familyMembers] stopping
[DEBUG] [09/06/2015 14:10:52.978] [family-akka.actor.default-dispatcher-5] [akka://family/user/familyMembers/John] stopping
...........
{% endhighlight %}

### Conclusion

We can see **_become()_** and **_unbecome()_** methods come very handy. By default receive method is used to handle all incoming messages. However at any time if we need to change the behaviour we can use the **_become()_** method, which accepts as arguments with a return type of **_receive_** signature. Once we change the receive method all the messages that are sent to the Actor model will be handled by the new method. **_unbecome()_** method is contrast to the **_become()_** method. By executing the unbecome method we will be able to restore to the original receive method. 

To download the sample code : [**Download**](https://github.com/Renien/akka-tutorials){:target="_blank"}

### Blog Series
* [**Life with Akka.io**](/articles/life-with-akka/)
* [**Set Up Akka**](/blog/set-up-akka/)
* [**Akka Concurrency**](/blog/akka-concurrency/)
* [**Actor**](/blog/actor/)
* [**Actor System**](/blog/actor-system/)
* [**Supervision / Supervisor**](/blog/supervisor/)
* Being Stateful