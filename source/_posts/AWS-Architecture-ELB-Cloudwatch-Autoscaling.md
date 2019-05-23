---
title: 'AWS Architecture ELB, Cloudwatch, Autoscaling'
date: 2019-05-22 14:01:08
category: 
- AWS_Architecture
tags:
- AWS
- ELB
- Elastic Load Balancing
- CloudWatch
- AutoScaling
---

I. Basics
II. S3 and Glacier Storage
III. EC2 & EBS
IV. VPC (network)
V. **Elastic Load Balancing, CloudWatch, AutoScaling**
VI. AWS Identity/IAM
VII. Database
VIII.SQS, SWF, SNS
IX. DNS, Route 53
X. ElastiCache
XI. Security
XII. Risk & Compliance
XIII. Architecture Best Practices

ELB in action:
{% post_link AWS-EC2-Instance-Using-ELB-and-Simple-Route %}

## Elastic Load Balancing (ELB) ##
This is a service that distributes traffic across EC2 instances with options that give flexibility and control of incoming requests to those instances. Because AWS cloud allows convenience of spinning up a good deal of servers, the ELB helps with consistency; the data is distributed equally. There is a managed service that is available, automatically scaling and integrates with Auto Scaling. 

**Internet-facing Load Balancer**: takes requests from the Internet --> EC2 instances.
**Internal Load Balancers** balance the load within internal EC2 instances within subnets
**HTTPS Load Balancers** for encrypted SSL/TLS protocol. 

Every load balancer must have **listeners** configured, that checks for connection requests, okay with HTTP, HTTPS, TCP, SSL.

You can configure ELB with *idle connection timeout*, *cross-zone load balancing* so that AZ crossover is allowed, *connection draining* in terms of instances that fail health checks, *proxy protocol* which adds human-readable header to request header, *stick sessions* which binds a user session to a specific instance so that all requests are send to the same instance, *health checks* to test EC2 instances.

## CloudWatch ##
Used to monitor AWS resources and applications in real time. You can select metrics, alarms, basic or detailed, customizable. 

## Auto Scaling ##
A big advantage of deploying to the cloud is ability to launch and release servers in response to variable workloads.  This service lets you scale EC2 capacity vis-a-vis criteria you give. There are different plans. 