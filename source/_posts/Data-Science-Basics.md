---
title: Data Science Basics
date: 2019-05-24 11:25:00
category:
- Data Science
tags:
- general concepts
---

One of the areas of teaching in the MSIS program will be that of data science, so in preparation for that content I'm reading through a book and wanted to put my notes here. Hopefully this will be of help to someone else, too, who is starting this journey towards understanding this field :)

## Data Science
*Data science* is the art of wrangling data (which is ever increasing from sensors and our phones and online interactions), to make all the data useful, to predict future behavior, uncover patterns for actionable behavior, and uncover meaning from this mass of data. It is *the practice of using a set of analytical techniques and methodologies to derive and communicate valuable and actionable insights from raw data, to be more precise* :)

Data science produces **data insights** - actionable, data-informed conclusions or predictions that you can use for business decisions. These insights are being increasingly demanded, from Uber passengers and pick-up times, to Amazon recommended (accurate) picks for shopping. 

**Data engineers** work to capture and collate large volumes of *big data* that doesn't fit conventional db systems due to size, or unstructured types of data, or because the input is so fast. **Data scientists** work to actually analyze that data for insights. The data scientist has to *query* data, most often using *SQL* to do so. You can use a variety of formats:
- *CSV files*
- *Python* or *R* programming scripts to analyze and visualize data
- *Application files* such as Excel
- *Web based* such as *D3.js* for data visualization (Javascript)

**Math skills** come in pretty handy for understanding the data, including *statitistic*. These are used to build decision models and make predictions

### Data Science Solution Alternatives
1. **Assemble in-house team**
As opposed to hiring *independent consultants* or deploying a ready-made cloud-based analytics solution
- Train existing employees
- Hire trained personnel
- Train exisiting and hire some experts.

Or, go ahead and ** **Outsource** and hire a *consultant* either for a wide-brush organizational approach, or specific tasks with an individual contractor.

2. ** Leverage cloud-based platform solutions**
- Helps provide info without scripting, but you still need professionals who can design, run, and interpret the results of the cloud produced work.

## Data Engineering Pipelines & Infrastructure

With **big data** we are talking *petabytes* and *terabytes.* Big in terms of *volume*, *velocity*, and *variety*.

1 Terabyte is the smallest with big data. Big data is *low-value* so you have to ingest a lot of it, quickly, to generate timely insights. **data velocity** is data volume / unit time. High throughput requirements are standard. **high variety** often refers to a variety of data formats. **Structured** data can be worked with RDBMS, while **unstructure data** doesn't fit that, examples are blog posts or emails.  A **data lake** is a flat container of unstructured data. 

*Big data* can come from IoT, social media, etc. **Data scientist** use data analysis for knowledge discovery such as helping business to work better. *Need math and statistics, computer programming, and domain-specific knowledge*.  **Machine learning** is the practice of applying algorithm to learn from, and make automated predictions about, data.

**Data engineering**, on the other hand, is more focused on the technical aspects of working with big data, such as reducing bottlenecks. They can build large-scale SaaS apps, build Hadoop apps, design relational dbs for big data. 

## Hadoop

Hadoop is the premier platform for large-scale data processing, storage, and management. Open source platform. A **hadoop cluster** can be comprised of thousands of nodes. 
Because big data doesn't fit with traditional RDBMS, they use Hadoop ecosystem which includes:
- **HDFS** for data storage, stands for Hadoop Distributed File System. Use *commodity servers* that run in paralled in clusters, also called *nodes.* Can now use SQL to query HDFS (like Hive and Spark SQL).
- **MapReduce** for bulk data processing
- **Spark** for real-time data processing (as opposed to MapReduce). You can now use Python to program Spark (PySpark)
- **Yarn** for resource management

**MapReduce** is a batch processor, an dcan't process real-time streaming data, but can process lots of data using *parallel distributed processing* framework (which means that tasks are processed in parallel fashion via clusters of servers). It transforms big data into smaller, more manageable data sized.

This is done by: 1. **mapping the data**, then 2. **reducing the data**.

## Alt to Hadoop
Massively Parallel Processing (MPP) is an altterntive, but run on costly custom hardware as opposed to MapReduce inexpensive commodity servers. So they are much more expensive, but are quicker and easier to use b/c they can be quieried with SQL while MapReduce (native) use Java (more complex). 

## NoSQL
RDBMS can't really handle big data, but NoSQL can b/c they are non-relational, distributed db systems that were designed for big data challenges. **MongoDB** is the most popular on the market.

Four categories: 
- graph db
- document db
- key-value stores
- column family stores


## How Data Science Can Apply To Business
- there are a variety of ways, such as decreasing financial risks by detecting fraud, for example. Data can be used to increase sales rates, and increase efficiency.

**Data analysis** can be *descriptive* ("What happened?"), *diagnostic* ("Why did this happen?"), *predictive*("What will happen?"), *prescriptive* (what you should do.)

**Data wrangling** is converting data into meaningful insights. For this you need to **extract data**, **prepare data**, **govern data** via data governance standards, and **data architecture** - you don't want data to be siloed.

After you get those insights, you have to take **decisive actions** based on those insights. 


