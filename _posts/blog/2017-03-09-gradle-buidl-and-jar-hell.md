---
layout: post
title: "Gradle build and Jar Hell"
description: "One of the challenging task is to setup the ground level structure and build scripts focusing a large growing project."
category: blog
tags: [Gradle, Groovy, Hadoop, BigData]
image:
  feature: 
  credit:
  creditlink:
comments: true
share: true
---

# Overview

One of the challenging task is to setup the ground level structure for a project and build scripts focusing a large growing project. I was spending almost a week incrementally building the product features and updating the build scripts for a data science project.

To make sure all my dependencies are available for my Hadoop MapReduce jobs I’m creating FAT JAR. Due to multiple dependencies in the project and Hadoop cluster I faced a Jar Hell problem. JAR Hell is an endearing term referring to the problems that arise from the characteristics of Java’s class loading mechanism. Simply, it is a dependency version conflict issue. 

So I decided to move few libraries to use only at compilation time and during the Hadoop job execution it will get resolved from the HDP libraries. Since the provided scope was not supported in some Gradle version I implemented a workaround using the groovy script. 

Create your own configuration:

{% highlight gradle %}
configurations {
   providedCompile
}
{% endhighlight %}

and set it to be used with the compilation classpath:

{% highlight gradle %}
sourceSets {
    main {
        compileClasspath += configurations. providedCompile
    }
}
{% endhighlight %}

After 'providedCompile' task is added modified my build script to use few libs during only compilation. Eg:

{% highlight gradle %}
providedCompile([
        libs.pig
])
{% endhighlight %}

But unfortunately Gradle build failed for some reason with the following error message:

<span style="color:red">You can't change configuration 'providedCompile' because it is already resolved!</span>

The issue was in groovy : [Gradle Community Forums](https://discuss.gradle.org/t/custom-provided-configuration-not-working-with-gradle-2-0-rc2-in-multi-project-mode/2459){:target="_blank"}

Since I’m using Gradle 2 version I faced this issue. Because they have updated Gradle 2 with Groovy 2.3, which is no longer supported to add single element to a collection. Instead of adding a single element we need to add it as a collection passing the single element. 

{% highlight gradle %}
sourceSets {
    main {
        compileClasspath += [configurations. providedCompile]
    }
}
{% endhighlight %}

After fixing the issues in build script, I was able to build and execute the job successfully.
