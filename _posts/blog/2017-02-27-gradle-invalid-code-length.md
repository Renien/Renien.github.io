---
layout: post
title: "Gradle: Invalid method Code length 66047 in class file jobs_51dck7bh02aiqhihu32e2hl475"
description: "JVM has a limit on method size in bites"
category: blog
tags: [Gradle, Groovy, Java]
image:
  feature: 
  credit:
  creditlink:
comments: true
share: true
---

# Overview

Recently, I came across the following issue (_Figure 1_) in my build script when I started to add more custom tasks into my build script. The current project code base is huge and lot of custom build process needs to be implemented to automate the project build. 

<figure style="text-align: center;">
  <a href="/blog/gradle-error-invalid-method-code-length.jpg"><img src="/blog/gradle-error-invalid-method-code-length.jpg" alt="image"></a>
  <figcaption>Figure 1 - Invalid Method Length</figcaption>
</figure>

After reading so many articles got to know that these issues can happen due to the method length in our java code. Basically, JVM has a limit on method size in bites, but during byte code transformation which is required to make possible mocking static, final size of the method could exceed this limit. But even though when I shorten my groovy custom tasks it was throwing the same error. 

I don’t know for some reason, I thought to modularize the build script and import the different sub.gradle files to the main gradle file so that number of lines of code will be reduced. At last I was able to build successfully.

Basically, while transforming the code to Java byte code due to the big lengthy build script it exceeded the JVM method size limit.
