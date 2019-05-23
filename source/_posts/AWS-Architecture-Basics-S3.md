---
title: 'AWS Architecture: Basics & S3'
date: 2019-05-22 07:38:21
category: 
- AWS_Architecture
tags:
- AWS
- S3
---

It's been a few months since I took (and passed) the AWS Certified Solutions Architect, so to dust off any cobwebs i'm reviewing the offical study guide for that exam and I'm going to jot down my notes here. That'll serve as a convenenient reminder for me, and hopefully a helpful resource for anyone else undertakin a similar effort. Here we go!

I. **Basics**
II. **S3 and Glacier Storage**
III. EC2 & EBS
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

## I. Basics

Cloud computing offered by AWS back in 2006, now all over the world, it's on-demand computing resources so you don't have to buy, setup, maintain all that stuff yourself. Advantages include economies of scale, more agility, don't have to guess capacity, speed for global access, leverage economies of scale. You can go all-in or hybrid using local resources.

AWS has *regions* which is a geographical area, and within each region are *availability zones* which are isolated areas (so in case of a natural disaster for example, you have redundancy), but are connected with links. So, by putting your resources in different AZs, you can protect your data. 

Security is a big deal, the client needs to step up too. I learned from experience the hard way of that! (long story). 

To access AWS Platform, you can use CLI, SDK software kit, or online management console.

**EC2** is a virtual computer, configurable in terms of OS, memory, storage, CPU, etc. *Lambda* is part of the serverless approach for backend devs wherein AWS EC2 instances will run your back-end code. *Auto scaling* lets EC2 instance capacity be scaled up and down automatically based on config. *ELB*  automatically distributes data across EC2 instances allowing better fault tolerance. *AWS Elastic Beanstalk* makes it really easy to deploy a web app on AWS. *Amazon VPC*  is private cloud virtual network including IP address range, subnets, route tables, network gateways, and such. *AWS Direct Connect* is a dedicated data connection from local org to AWS. *AWS Route 53* is a DNS web service.

**Storage**: *S3* is the backbone where object storage is unlimited, used for backup, storage, etc, cheap, durable. *Glacier* is archival S3 storage. *EBS* is block-level storage for use with EC2 instances. *AWS Storage Gateway* connects on-site storage with cloud-storage. *AWS CloudFront* is a content delivery service, caches data locally around the world at edge locations. 

**Database**: *RDS* is relational database service that takes up heavy lifting. *DynamoDB* is NoSQL db. *Redshift* petabyte-scale warehouse service, with SQL interface. *ElastiCache* in-memory cache in the cloud. 

**Management Tools**: *CloudWatch* monitoring service of apps and resources running on AWS. *AWS CloudFormation*  effective way to create and manage a collection of related AWS resources, using JSON templating language. *CloudTrail* is a logging service for data. *AWS Config* resource inventory.

**Security & Identity**: *IAM* creates users and groups for permissions for access. *KMS* control encryption services. *AWS Certificate Manager* manage and deploy SSL/TLS certifcates. *WAF* a firewall to protect web apps against common attacks. 

**Application Services**: *API Gateway* devs can create, publish, maintain and secure APIS at any scale, it accepts all the tasks involved in accepting API calls and processing requests. *Elastic Transcoder*is media transcoding in the cloud, such as photo size. *SNS* sending messages to recipients. *SES* simple email service sending emails and receiving them can deliver to S3 bucket or push SNS etc. *SWF* scale background jobs which have parallel steps. *SQS* decouple components in an app.

## S3 and Glacier Storage
**S3** are secure, durable, highly-scalable, *object storage* with simple web interface good for backup, media and software storage and distribution, big data analytics, cloud-native mobile and web app hosting, websites.  Different storage classes. Rich set of permission, acccess controls, and encryption options. It is *object storage* which differs from block storage and file storage, both of which are accessed using protocols specific, closely associated with server and OS. *S3* is diffent, it is independent of server and is accessed via the web using API and HTTP verbs. S3 use *buckets*, and its simplicity has benefits such as its being unlimited in data, plus objects are automatically replicated in multiple facilities within a region (robust!), also very scalable. The bucket is created in a specific region but namespace is global so must be unique. Every object has a *key* which is unique, and has an *object URL* which makes it web accessible. CRUD and list. REST interface (CRUD). Very durable and available. *Eventually consistent data*, because of replication it might take some time to read after an update. 

S3 is integrated with many other AWS cloud services: IAM, KMS, EC2, EBS, EMR, Database, SQS, Lambda, Cloudfront.

*Access control* : S3 is secure and locked-down by default. You can control access via Access Control List (ACL), bucket policies, IAM policies, and query-string authentication. *bucket policies* are recommended because they provide much finer-grained control.

*Static website hosting* is very common, you can't have server-side processing but they can be dynamic using client-side scripts such as JS. 

*Different Storage Classes* : Standard, Standard-IA infrequent access, Reduced Redundancy Storage (RRS), Glacier for long-term archival.

*Object Lifecycle Management* where you shift to different storage classes.

*Encryption* : server-side (AWS-Managed, AWS KMS Keys, Customer-Provided Keys), client-side.

*Versioning* if you want it, but steps up storage costs.

*MFA Delete* requires additional authentication before big action

*Pre-Signed URLs* means the owner can share object with others via time-limited permission.

*Multipart Upload* for uploading or copying large objects.

*Cross-Region Replication* async replication from one region to target bucket in another region.

*Logging* to track request, gives all sorts of info

*Event notifications* can be sent in response to objects uiploaded or stored in S3 --> run workflows, send alerts, perform other actions.