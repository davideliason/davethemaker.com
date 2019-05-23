---
title: AWS Architeccture ElastiCache
date: 2019-05-23 11:48:23
category: 
- AWS_Architecture
tags:
- AWS
- ElastiCache
---

I. Basics
II. S3 and Glacier Storage
III. EC2 & EBS
IV. VPC (network)
V. Elastic Load Balancing, CloudWatch, AutoScaling
VI. AWS Identity/IAM
VII. Database
VIII.QS, SWF, SNS
IX. DNS, Route 53
X. **ElastiCache**
XI. Security
XII. Risk & Compliance
XIII. Architecture Best Practices

## ElastiCache

Caching helps to improve performance of apps, and this Amazon service takes the deployment and ops burdens from your shoulders. **In-memory cachine** makes User experience fast and responsive. R/t trips to db and storage really increases lag time and user frustration. 

 *Caching frequently-used data is one of the most important performance optimizations that you can make in your app*.

 *Memcached* or *Redis* are cache engines that allow you to store data in-memory for fast performance. *Memcached* is one of the most popular, while *redis* can be used as a cache, database, or even message broker. *ElastiCache* lets you use either one, your choice. *Redis* supports the ability to persist the in-memory data onto disk, so you can create a snapshot as backup. Can sort and rank data. 

 The most common cachine patterm is the cache-aside pattern - if the data is not in the cache, the db is queried and the data is populated in the cache for the next user. 

 Eache cache *cluster* contains one or more *nodes*. You can select *node type* to get the right mix of compute and memory resources you need. You can expand the cluster type for your needs.  You can exapnd horizontally too using *replication group*.  *Redis* allows for *snapshots* of data, which can be recovered in case of failure. 
 
 You can **secure** your cache environmenst at network levels with security groups and NACLs, and infrastructure level using IAM policies.