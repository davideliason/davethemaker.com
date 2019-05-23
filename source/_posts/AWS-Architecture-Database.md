---
title: AWS Architecture Database
date: 2019-05-22 14:33:49
category: 
- AWS_Architecture
tags:
- AWS
- Database
---

I. Basics
II. S3 and Glacier Storage
III. EC2 & EBS
IV. VPC (network)
V. Elastic Load Balancing, CloudWatch, AutoScaling
VI. AWS Identity/IAM
VII. **Database**
VIII.SQS, SWF, SNS
IX. DNS, Route 53
X. ElastiCache
XI. Security
XII. Risk & Compliance
XIII. Architecture Best Practices

There  is Relational Database Service (RDS), DynamoDB ( a NoSQL db), and Redshift (data warehouse). You can build an app that integrates RDBMS (Relational Database Management Systems) + NoSQL database.

**Relational DB**
This is the most common type, incl. MySQL, PostgreSQL, Microsoft SQL Server, and Oracle. Read/write using Structured Query Language (SQL). A relational db consists of one or more tables, and a table consists of columns, rows, with the column containing attributes like a person's name. Each attribute is assigned a data type like text, number. One record in a table can relate to another table's record by means of *primary keys (foregin key)*. 

Either Online Transaction Process (OLTP) [ transaction-oriented, freq writing and changing data, ex e-commerce] or Online Analystical Processing (OLAP)[ data warehouses, large data sets], depending on how tables are organized and how app uses it. 

*Amazon RDS* simplifies setup and maintenance of OLTP and OLAP dbs. Support for MySQL, Oracle, PostgreSQL, Microsoft SQL server, MariaDB, and Amazon Aurora. Or, you can spin up an EC2 instance and install, maintain yourself a different db engine. Rigid schema. Simplifies setup and maintenance.  Exposes a db endpoint to which client software can connect and execute SQL. No shell access

An API allows you to create and manage one or more *DB Instances.*, which is an isolated db env deployed in your VPC. 

**Data Warehouses**
Central repository for data, ususally used by orgs for highly complex queries. Typically updated on a batch schedule multiple times a day or hour. Often, orgs split RD into one for OLTP transactions and one for data warehouse vis-a-vis OLAP (less frequent but more complex). **Amazon Redshift** is high-performance data warehouse for OLAP use cases. Can combine Amazon RDS + Amazon Redshift.

**NoSQL**
Simpler, more flexible, great performance. Horizonatal scalability. Non-relational.  Are key/value stores or document stores with flexible schemas. Many app teams use Hbase, MongoDB, Cassandra, CouchDB, Riak, and Amazon DynamoDB to store large volumes with high transaction reates. Often support clusetering and scale horizonatally.  Common use is managing user session state, user profiles, shopping cart data, or time-series data. 

**DB Engines**
- *MySQL* is one of the most popular open source db in the world. Wide range of apps are powered with it. Amazon RDS MySQL allows you to connect using standard MySQL tools such as MySQL Workbench or SQL Workbench/J.

- *PostgreSQL* is widely used
- *MariaDB* was built by creators of MySQL with enhanced enterprise tools and functionality. Added features to enhance performance, availability, and scalability of MySQL.
- *Oracle* is one of most populare relational db used by enterprise, supported by Amazon rDS. 
- *Microsoft SQL Server* is very popular in enterprise. 
- *Amazon Aurora* is enterprise-grade commercia db tech, cost effectively, simply. Fully managed service. MySQL-compatbile out of the box. 
- *Amazon Redshift* is petabyte scale data warehouse, relational db, designed for OLAP scenarios, lowered cost, makes it easy to analyze large amounts of data.  Use of *cluster* which is made of a leader node and one or more compute nodes. The client app interacts directly with only leader node. Different node types each with different mix of CPU, memory, storage. 
= *Amazon DynamoDB* is fully managed NoSQL db service that provides fast, low-latency performance. Simplifies hardware provisioning, setup, config, replication, pathech. Can create tables that scale to an unlimited number of items and configure very high levels of provisioned read and write capacity.