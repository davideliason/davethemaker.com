---
title: AWS Architecture Security
date: 2019-05-23 12:45:12
category: 
- AWS_Architecture
tags:
- AWS
- Security
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
XI. **Security**
XII. Risk & Compliance
XIII. Architecture Best Practices

## Security

I can speak from experince as my account was hacked and I got hit with some charges how important it is to take this seriously! AWS uses the *Shrared Responsibility Model*, which basically says that AWS takes certain steps, but the user has to take steps too for security. For example, AWS network provides a good deal of protection against some traditional attacks, such as DDoS attacks, Main in the Middle attacks, IP spoofing, Port scanning attacks, Packet sniffing by other tenants. 

AWS uses *credentials* to ensure only authorized users gain access. Passwords, MFA, access  keys, key pairs, and certificates are all approaches.