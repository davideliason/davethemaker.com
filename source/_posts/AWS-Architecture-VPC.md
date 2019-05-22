---
title: AWS Architecture VPC
date: 2019-05-22 09:42:45
category: 
- AWS_Architecture
tags:
- AWS
- VPC
---

I. Basics
II. S3 and Glacier Storage
III. EC2 & EBS
IV. **VPC** (network)
V. Elastic Load Balancing, CloudWatch, AutoScaling
VI. AWS Identity/IAM
VII. Database
VIII.SWS, SWF, SNS
IX. DNS, Route 53
X. ElastiCache
XI. Security
XII. Risk & Compliance
XIII. Architecture Best Practices

Okay, now we dive into VPC which is where we can configure a private network for our instances, storage services, and such. This section blew my brain when I first started watching ACloudGuru videos, because it can get awfully complex pretty fast, but it's pretty interesting too.

**What** VPC is the networking layer for EC2, so imagine that you are physically creating a network at home with those big blue CAT-5 cables plugged into your computer/server, into the router, into the printer or whatever else have you. You're doing the same thing just up in the cloud, you just have to make diagrams and imagine what you're connecting and building. But, in essence, you're going to build a network where you connect, say, an EC2 instance with an internet-facing server, perhaps a database, and whatever other resources you want. Since this is the cloud, you need to configure the virtual space where this all will run.

You create the IPv4 address range (CIDR block) ex: 10.0.0.0/16. That's for your network. Then you can create subnets placed in different AZ, and add a route table.

**A VPC consists of**: subnets, route tables, security groups, Network access control lists (NACL), with **options** of *Internet Gateways* (IGW), *EIP* address or elastic IP address, *elastic network interface (ENI)*, endpoints, peering, *NAT* instances and gateways, *virtual private gateway(VPG)*
A **subnet** is part of the IP address range where you can launch an EC2 instance, RDS, and other resources. Subnets reside within one AZ and can't span zones. You can have multiple subnets in one AZ thought. Subnets can be public, private, or VPN-only. 
A **route table** contains rules that are applied to the subnet re: where traffic is directed. A route table's routes are what permit an EC2 instances within different subnets to communicate with each other. Here, you can also specific which subnets are public and private. 
An **internet gateway** allows communication with VPC and the web.
An **elastic IP address(EIP)** is an IP address that is "yours". It is a static, public IP address in the pool that you can allocate to your account and also release.  Allows you to maintain a set of IP addresses that remain fixed even though the underlying infrastructure might change over time.
An **endpoint** allows you to create a private connection b/w VPC and another service without having to brave the troubled waters of the internet.
**Peering** is a networking connection between two VPCs so they can communicate.
A **security group** is a virtual firewall that controls in/outbound traffic to AWS resources and EC2 instance.
**Network Access Control Lists(ACLs)** is another security layer acting as stateless firewall on *subnet level*.
**NAT Instance/Gateway** allow an instance in a private subnet within the VPC to communicate with the internet, but only for initiating outbound traffic. So it would prevent receiving any inbound traffic initiated by someone on the Internet. The gateway is rec'd over instance b/c easier, better availability, higher bandwidth.

The *difference between security group and NACL* is that **security group** is at the instance level, you can have multiple instances in mulitple subnets that are memebers of the same security groups.  They are stateful (return traffic is auto allowed). A **NACL** is on a subnet level, stateless - you have to allow both in/outbound traffic.



See here for an example of a VPC being set up and used:
{% post_link AWS-EC2-Instance-Using-ELB-and-Simple-Route %}
