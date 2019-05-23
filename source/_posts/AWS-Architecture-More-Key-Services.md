---
title: AWS Architecture More Key Services
date: 2019-05-23 12:17:33
category: 
- AWS_Architecture
tags:
- AWS
- Storage
- Content Delivery
- Security
- Analytics
- DevOps
---

I. Basics
II. S3 and Glacier Storage
III. C2 & EBS
IV. VPC (network)
V. Elastic Load Balancing, CloudWatch, AutoScaling
VI. AWS Identity/IAM
VII. Database
VIII.SQS, SWF, SNS
IX. DNS, Route 53
X. ElastiCache
XI. Security
XII. Risk & Compliance
XIII. Architecture Best Practices
**Bonus material!**

## Storage & Content Delivery
*Amazon CloudFront* is a CDN  service, caches content on servers at edge locations, this decreases latency and increases user experience. It's usually a completely transparent experience, it simply is faster for the user. It supports all content that can be served over HTTP or HTTPS. 

You create a *distribution* which is identified by a DNS domain name. You use the distribution domain name in place of your websites's domain name, the rest of the file paths stay unchanged. you can use a user-friendly DNS name by creating a **CNAME** record in Route 53. 

When yuou create a distribution, you have to specific the DNS domain name of the orign, the S3 bucket or HTTP server, from where CloudFront will get the web files/objects. 

Once objects go into the cache, they remain there until they expire or get the  boot to make room for more frequently requested data.  Default is 24 hours, but you can control this. You can invoke the nuclear option and remove all objects from the cache using the *invalidation API*, which is for unusual circumstances. 

**But wait!**, CloudFront can do more than serve static files, it can also serve dynamic content and to use more than one origin server. You do this by using a feature called **cache behaviors**. 

**Use Cases**
- Serve static assets
- Serve whole webstie or web app
- serve content to users who are distributed geographically
- Distribute software or other large files
- Serve streaming media

## Amazon Kinesis
Platform for handling massive streaming data on AWS, makes it easy to load and analyze it, and also provide ability to build custom streaming data apps


## DevOps
Part of an agile methodology for more increased flexibility, blurring lines between traditional dev't and ops teams. 

**AWS OpsWorks** is a service that helps you configure and operate apps using **Chef**. Architectural-pattern neutral.  Supports Linux or Windows, including EC2 instances, so that a signle config mgmt service can deploy and operate apps across hybrid architectures.

Many solutions on AWS involve groups of resources, known as **stacks**. You typically need a way to distribute apps to all the servers, for example, or manage security, etc. AWS OpsWorks provides a "simple" and flexible way to create and manage stacks and applications. It allows you to manage the stack resources as a group, define some default config settings.  You can define **layers** of the stack, which serve a particular purpose, and customize and fine layered control.

**Chef receipes** handle tasks like installing packages on instances, deploying apps, and running scripts. 

**Use Cases**
- *Host multi-tier web application*. Use Chef to leverage 100s of community-built configs.
- *Support Continuous Integration*. Automate those bad boys!

## CloudFormation
Tool for creating an easy way to create and manage a collection of AWS resources, provisioning and updating them in an orderly and predictable fashio. You work with *template* and *stacks*. 

The *template* is used to define your AWS resources and their properties. It is a JSON text doc. The *stack* is the collection of resources, and these are updated, created, or deleted via the template. The stack is definted in the template. You can make customizations using *parameters*

**Use Cases**
- Quckly launch new test environments
- Replicate config between environments
- Launch apps in new AWS regions. 

## AWS Elastic Beanstalk
The fastest and simplest way to get an app up and running on AWS. Upload the code, and the service handles all the details such as provisioning, load balancing, auto scaling, and monitoring.