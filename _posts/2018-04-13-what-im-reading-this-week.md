---
layout: post
title:  "What I'm Reading This Week - April 13, 2018"
date:   2018-04-13 2:00 PM
tags: [reading, big data, software engineering]
---
I spent a lot of time this week reading about how different engineering teams have scaled their Hadoop infrastructure. I also spent time looking at consistent hashing strategies, how GitHub manages DNS and routing, and how individual personalities affect team culture and performance. Read on for all the details.

[Transit and Peering: How your requests reach GitHub](http://awe.st/2gW1R86)

One of GitHub's infrastructure engineers talks about they use Geographic DNS routing and network [peering](https://en.wikipedia.org/wiki/Peering) to impact how their traffic is shaped. Through their efforts they were able to direct 60-70% of GitHub traffic through optimal routes.

[Great Teams Are About Personalities, Not Just Skills](https://awe.st/2v7BJ3P)

This article on the Harvard Business Review discusses how personalities affect team performance. Yes, the skill of each person is important, but other factors such as whether you are results-focused or relationship-focused matter too. The tl;dr is a mixture of various personality traits tends to yield greater team performance and interpersonal dynamics.

[Scaling Uber’s Hadoop Distributed File System for Growth](https://awe.st/2qtEUgO)

Uber's engineering team talks about how they've addressed critical bottlenecks in scaling their Hadoop/HDFS infrastructure. The post talks about splitting Hadoop/HDFS into multiple physical clusters using Namespaces and [ViewFs](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/ViewFs.html), deploying HDFS upgrades through better a deployment framework, and tuning NameNode garbage collection.

[Apache Hadoop - HDFS Federation](https://awe.st/2qtFzPk)

After reading how Uber addressed scalability challenges with ViewFs I wanted to better understand [HDFS Federation](https://awe.st/2qtFzPk). HDFS Federation addresses a limitation in prior Hadoop architectures where a single NameNode manages the Namespace. With federation you can support multiple NameNode/Namespaces which can bring better performance and process isolation, especially in a deployment with a lot of small files.

[All AWS Services are now GDPR Ready](https://awe.st/2HjyaKB)

This article on InfoQ provides some background on [General Data Protection Regulation (GDPR)](https://www.eugdpr.org/) and Amazon being GDPR ready for the legislation which goes into effect next month.

[Performance Evaluation of Hive-MR3 0.1 (Part I)](https://awe.st/2JFN4eJ)

This post discusses the results of testing Hive-MR3 and Hive-on-Tez using the [TPC-DS](http://www.tpc.org/tpcds/) benchmark on two different clusters. For this lab environment Hive-MR3 resulted in faster query execution times but it's not an easy comparison since Hive-MR3 shares the same runtime environment with Hive-on-Tez.

[Consistent Hashing: Algorithmic Tradeoffs](https://awe.st/2HxkCuW)

This article discusses various solutions to a common hashing problem. Given a key/value store, you want to distribute the keys evenly across all servers so you can easily find them again. But, you can't store a global directory/lookup to tell you where things are. Algorithms discussed include: Random Trees, Ketama (libketama), AWS Dynamo's k/v store, Jump Hash, Multi-probe Consistent Hashing and more.

[Give meaning to 100 billion analytics events a day](https://awe.st/2EGFf4A)

The Teads engineering team talks about their move from a [Lambda Architecture](http://lambda-architecture.net/) to a multi-cloud approach using AWS (Kafka) and Google Cloud Platform (BigQuery, DataFlow). Much of the article talks about their approach in scaling BigQuery through different ETL practices and data rollups.

[Engineering Data Analytics with Presto and Parquet at Uber](https://awe.st/2IPSAua)

The Uber engineering team discusses their Presto architecture and how they created an open source Parquet reader that uses memory and CPU more efficiently. Several of their Parquet reader performance and efficiency strategies are discussed include: skipping unnecessary data reads, reading columns vs rows, and lazy reads. If you use Presto - or Presto with Hadoop - it's worth checking this out.