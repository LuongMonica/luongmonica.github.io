---
layout: post
title:  "Blog 7: Studying for AWS Certified Cloud Practitioner pt.8"
date:   2022-04-01 9:59:31 -0700
categories: jekyll update
---
![AWS Training and Certification](/assets/aws-training-and-certification.jpg)
# **Intro and Recap**
Hello again! This week we are continuing our discussion of the material that will most likely appear in the AWS Certified Cloud Pracitioner (CCP) Exam. Last time we went over a part of the seventh module, Storage, and briefly discussed the services of S3, EFS, and EBS.  In this post, we'll talk about the last main service category: Databases. Let's get started!

# **Databases** 
In this module, you learn about the last main service category we'll go over: Databases. This is the final pillar of the AWS portfolio, along with Compute and Storage. Databases are used to store data that will constantly be updated through CREATE, UPDATE, and DELETE operations. Data gets retrieved and manipulated by the corresponding users and applications that access it. This is how databases differ from regular storage options.

AWS offers a vast number of database services to fit the needs of any type of customer that wants to use them. Today I'll take about the 4 main ones that are more widely used than the other niche services. We'll talk about RDS, DynamoDB, Redshift, and Aurora.

## **RDS** 
RDS, or Relational Database Service, is a fully managed relational database service that takes care of the hassle of administrative tasks like backups and upgrades so you can focus on your data and optimizing it for your application. RDS offers 6 database engines: MySQL, Aurora, Microsoft SQL Server, PostgreSQL, MariaDB, and Oracle. With RDS, you can easily setup advanced database availability procedures like multi-AZ deployments or read replicas. In a multi-AZ deployment, you have synchronous replication of your database instance. Read replicas, which are only available for MySQL, Aurora, PostgreSQL, and MariaDB, offer asynchronous replication. This replica is read-only and can be used for your application when it only needs to do read queries. This can help promote greater efficiency in your database usage. Take a look at the graphics below for a visual of these 2 techniques.

![RDS Multi-AZ Deployment](/assets/aws-rds-multi-az.jpg)<br/><font size="2.75px"><em>Multi-AZ deployment made possible by synchronous replication to the standby RDS instance in the other AZ</em></font>

![RDS Read Replica](/assets/aws-rds-read-replica.jpg)<br/><font size="2.75px"><em>The master RDS instance offloads read queries to the read replica instance. If needed, the replica can be manually promoted to master. The read replica can also be created in a different region </em></font>

You should choose RDS when you have or require: complex transactions or queries, medium to high query or write rate with up to 30k iops (15k read + 15k write), and no more than a single worker node or shard. You shouldn't choose RDS when you have or require: massive read/write rates (150k write/sec), sharding due to high data size or throughput demands, simple GET or PUT requests and queries that a NoSQL database can handle, or RDBMS (Relational Database Management System) customization.

## **DynamoDB**
DynamoDB is AWS' NoSQL, key-value database offering. First of all, what's NoSQL you might ask. NoSQL, or No Structured Query Language, means this database doesn't use that language to manipulate its data. Data is unstructured or semi-structured and comprised of key-value pairs, with fields not needing to be present in each data entry. This is opposed to rigidly structured data of rows and columns that must be of equal length. NoSQL is becoming more popular because it solves some big challenges that face relational databases. It is able to make sense of semi or non structured data and is better for massive data sets because it can scale horizontally instead of vertically. If you've heard of MongoDB, this is another example of a NoSQL database. For a visual example of data in NoSQL vs SQL databases, take a look at the graphic below:

![Relational vs Non-Relational](/assets/aws-relational-vs-non-relational.jpg)<br/><font size="2.75px"><em>Side-by-side comparison of relational vs non-relational</em></font>

DynamoDB is highly performant. A few key points that make DynamoDB a great choice are its virtually unlimited storage, consistent, low latency queries (single digit milliseconds), scalable read/write throughput, and the fact that it runs exclusively on SSDs. 

When learning about DynamoDB, it's important to know some key terminologies. A table is a collection of data. Tables consists of items, which are groups of attributes that are uniquely identifiable. Finally, an attribute is the most fundamental data element; you can't drill down any further than it. DynamoDB also supports 2 types of primary keys (PKs): partition key and partition and sort key. A primary key is used to uniquely identify an item. A partition key is a single attribute whereas a partition and sort key are 2 attributes that combine to form a composite key.

Another important thing to know is how you retrieve data in DynamoDB. In a SQL database you would use a query like `SELECT * FROM Users WHERE pk="blah"`. In DynamoDB, you can use either a query or scan operation. A query uses only the PK to find an item. Meanwhile, a scan locates items by matching conditions on non-key attributes. A scan is less efficient because it'll look through all the items to find a match.

## **Redshift**
Redshift is a fully managed data warehouse service. This means that it's used for much larger data sets than a regular database. In fact, data warehouses typically serve petabytes of data! This service is used to analyze data using SQL queries and BI (business intelligence) tools. To be able to run such complex, analytic queries against large amounts of data, Redshift uses query optimization, columnar storage, and massively parallel data processing. It automatically and continuously monitors clusters, adding more nodes and redistributing the data for maximum performance. 

## **Aurora**
Aurora is a MySQL and PostgreSQL-compatible relational database service. Like RDS, you can automate time consuming, administrative tasks like provisioning, patching, and backups. Aurora takes it a step further by offering even more in terms of failure detection, repair (self healing), and high availability. Aurora boasts a resilient design that reduces restart time after a database crash to less than 60 seconds. It also moves the buffer cache out of the database process to reduce the need of throttling access to the database. For a more thorough comparison of RDS and Aurora, read this [AWS Blog Post](https://aws.amazon.com/blogs/database/is-amazon-rds-for-postgresql-or-amazon-aurora-postgresql-a-better-choice-for-me/).

# **Next Time**
Hope you learned a lot today. There's only 2 more modules left! Can you believe it? We're almost at the end! See you next week when we continue the AWS CCP discussion.

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

[AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/)

*Note: Assets in this post are from AWS Academy's Cloud Foundations course*