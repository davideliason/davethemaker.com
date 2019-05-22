---
title: AWS Identity/IAM
date: 2019-05-22 14:17:40
category: 
- AWS_Architecture
tags:
- AWS
- Identity
- IAM
---

I. Basics
II. S3 and Glacier Storage
III. EC2 & EBS
IV. VPC (network)
V. Elastic Load Balancing, CloudWatch, AutoScaling
VI. **AWS Identity/IAM**
VII. Database
VIII.SWS, SWF, SNS
IX. DNS, Route 53
X. ElastiCache
XI. Security
XII. Risk & Compliance
XIII. Architecture Best Practices

This post will cover briefly how AWS secures interactions with resources in your account. IAM gives you control as to how people and programs can interact with your AWS infrastructure, using users, groups, access control policies. 

## IAM ##
First of all, IAM is access to the infrastructcure, not the application itself. You should consider **Amazon Cognito** for a mobile app in terms of identity management.  Second, IAM you still need to make sure your OS is up to snuff with security. 

Next, IAM is accessed via CLI, AWS Management Console, or AWS SDKs. 
**3 kinds of Principals**
1. **Root User** don't use this on a daily basis. 
2. **IAM User** for people and applications
3. **Roles/Temporary Security Tokens** important for advanced IAM usage, it's a token that allows for within a certain period of time access to resources. They can allow access with EC2 application access, Cross-account access, federation (many organizations already have an identity repository outside of AWS and want to use that. Ex: Facebook, Google, etc)

There are **3 Ways to Auth a Principal**
1. User name/ password
2. Access key (access key ID + access secret key)
3. Access key / Session tokens (calls to AWS must include the two-part access key and the session token to authenticate)

**Policies**
A *policy* is a JSON doc that defines permission to access AWS resources. **Effect** (allow/deny), **Service** (which does permission affect?), **Resource** (the specific AWS infrastructure that the permission applies.), **action** (such as CRUD), **Condition** (any conditional values limiting permission).

**Associating Policies with Principal** 
With IAM user:
- **User Policy**. This is entered into the user interface on the IAM user page.
- ** Managed policy**. Created in the Policies tab on the IAM page, independent of any individual user. *Group policies*

**MFA** gives extra security, as do **rotating keys** 


