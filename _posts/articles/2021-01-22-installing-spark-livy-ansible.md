---
layout: post
title: "Installing Spark & Livy with Ansible"
description: "Installing Spark & Livy with Ansible"
modified:
categories: articles
excerpt:
tags: [Data Science,Big Data, Spark, Livy, Automate, Machine Learning]
image:
  feature:
date: 2021-01-22T15:39:55-04:00
comments: true
share: true
---


<div class="github-fork-ribbon" style="position: fixed;padding: 2px 0;background-color: #000;background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.15));-webkit-box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);-moz-box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.5);z-index: 9999;pointer-events: auto;top: 42px;right: -43px;-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);-ms-transform: rotate(45deg);-o-transform: rotate(45deg);transform: rotate(45deg);"><a href="https://github.com/Renien/docker-spark-livy" style="font: 700 13px &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif;color: #fff;text-decoration: none;text-shadow: 0 -1px rgba(0, 0, 0, 0.5);text-align: center;width: 200px;line-height: 20px;display: inline-block;padding: 2px 0;border-width: 1px 0;border-style: dotted;border-color: rgba(255, 255, 255, 0.7);">Fork me on GitHub</a></div>

Deploying your own Spark Standalone cluster with Livy is a time consuming task due to the complexity of the deployments. Even for the guys who want to play around with spark and livy in their local machine or even in virtual machines this project will be useful.

In my recent project we are building a **SAAS platform** where we need to deploy dev and stage environments in different cloud providers. Therefore, I used docker and ansible for deployments. Spark can be run on top of the Hadoop ecosystem and as stand alone mode. Therefore, I created the **latest version (2.4.7) of Spark Standalone docker image and the latest version of Livy (0.7.0 Incubating) image**.

1. [Spark Standalone Docker Image](https://hub.docker.com/repository/docker/renien/spark-stand-alone){:target="_blank"}
2. [Spark with Livy Docker Image](https://hub.docker.com/r/renien/spark-stand-alone-livy){:target="_blank"}

The following [**starter kit**](https://github.com/Renien/ansible-spark-livy){:target="_blank"} repository contains a simple ansible playbook to install a Spark Standalone cluster and Livy in docker. Current playbook contains only local ip to install docker and deploy spark cluster and livy. Based on your needs you will be able add more environments and automate your big data dev, stage and prod environments.

The repository [README file](https://github.com/Renien/ansible-spark-livy/blob/master/README.md){:target="_blank"} contains more details about setting up the environments.



> Thanks to Ansible we can scale the platform with one button click.

<figure style="text-align: center;">
	<a href="/articles/ansible.jpeg"><img src="/articles/ansible.jpeg" alt="image" ></a>
</figure>

Starter Kit: [**Ansible Spark Livy**](https://github.com/Renien/ansible-spark-livy){:target="_blank"}
