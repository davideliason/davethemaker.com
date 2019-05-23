---
title: 'AWS Architecture SQS, SWF, SNS'
date: 2019-05-23 10:58:04
category: 
- AWS_Architecture
tags:
- AWS
- SQS
- SWF
- SNS
---

I. Basics
II. S3 and Glacier Storage
III. EC2 & EBS
IV. VPC (network)
V. Elastic Load Balancing, CloudWatch, AutoScaling
VI. AWS Identity/IAM
VII. Database
VIII.**SQS, SWF, SNS**
IX. DNS, Route 53
X. ElastiCache
XI. Security
XII. Risk & Compliance
XIII. Architecture Best Practices

## SQS

Amazon SQS helps you decouple your infranstructure, you can store message as they travel between servers, allowing you to move data between distributed components of your application that perform different tasks without losing messages or requiring each component to always be availalbe.

A *visibility timeout* is a period of time during which Amazon SQS prevents other components from receiving and processing a message b/c another component is already processing it. By default 30secs.

*Amazon long polling* allows your SQS client to poll an SQS queue. If nothing is there, it will wait b/w 1-20 secs, but if something is there, the message is returned ASAP. 

## SWF
SWF allows you to make apps that coordinate work across distributed components. They are driven by *tasks*, which are logical units of work. You have to manage tasks, and that's wwhere *SWF* can help - gives you control of implementing tasks, coordinating them. 

A *workflow* is a collection of activities that carry out a specific goal. Each workflow runs in a AWS resource called a *domain* which controls the scope of the workflow. 

There are different *actors*, including *activity workers, workflow starters*, or *deciders.*

## SNS
SNS is a *push notification* service that allows you to send individual or multiple messages to large numbers of recipients. Consists of *publishers* and *subscribers*, communicated async.  Different protocols: HTTP, HTTPS, SMS, SQS, email, email-JSON, Lambda.