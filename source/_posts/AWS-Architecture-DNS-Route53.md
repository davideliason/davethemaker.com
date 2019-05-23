---
title: AWS Architecture DNS & Route53
date: 2019-05-23 11:17:40
category: 
- AWS_Architecture
tags:
- AWS
- DNS
- Route53
---

I. Basics
II. S3 and Glacier Storage
III. EC2 & EBS
IV. VPC (network)
V. Elastic Load Balancing, CloudWatch, AutoScaling
VI. AWS Identity/IAM
VII. Database
VIII.QS, SWF, SNS
IX. **DNS, Route 53**
X. ElastiCache
XI. Security
XII. Risk & Compliance
XIII. Architecture Best Practices

## DNS

DNS is the way that people-friendly domain names are converted to IP addresses.  DNS starts with *TLDs*, which is **.com, .edu** , etc. The IANA controls all the TLDs in a db.

DNS names are registered with a *domain registrar*, who can assign domain names under a TLD. These domains are registered with InterNIC, a subsidiary of ICANN. Each domain name is registered in a central db called WhoIS db. 

DNS consists of different record types, including: *A, AAAA, CNAME, MX,* and a few others. **Amazon Route 53** is a DNS service that connects user requsets to infrastructure running on AWS (like your EC2 instance), and can route users to infrastructure outside of AWS too.  Your DNS records are organized into hosted zones that you configure with API. A **hosted zone** simply stores records for your domain, including A, CNAME, MX, and other types. 

These records types, a little more detail:
**A** is an address record.
**AAAA** IPv6 address record
**CNAME** canonical name record or alias
**MX** mail exchange record
**NS** name server record
**PTR** pointer record
**SOA** start of authority record
**SPF** sender policy framework
**SRV** service locator
**TXT** text record 

There are different **routing policies**, including *simple* [ most common when you have a single resource that performs a given function for your domain], *weighted* [ when you want to route a certain % to a particular resource], *Latency-based* [ routed based on lowest latency time], *failover* [ route traffic from primary to standby location], *geolocation* [route your traffice based on end user's location].

Use ELB load balancers across AZ's with connection draining enabled, use health checks so that only EC2 healthy ones are used, use a latency-based routing policy with ELB health checks for lowest latency. User CloudFront edge locations for low latency. Deploy the app in multiple AWS regions for increased protection.

*DNS registration* each domain is registered in central DB called WhoIS db. 