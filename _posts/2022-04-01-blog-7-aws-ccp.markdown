---
layout: post
title:  "Blog 7: Studying for AWS Certified Cloud Practitioner pt.8"
date:   2022-04-01 9:59:31 -0700
categories: jekyll update
published: false
---
![AWS Training and Certification](/assets/aws-training-and-certification.jpg)
# **Intro and Recap**
Hello again! This week we are continuing our discussion of the material that will most likely appear in the AWS Certified Cloud Pracitioner (CCP) Exam. Last time we went over a part of the seventh module, Storage, and briefly discussed the services of S3, EFS, and EBS.  In this post, we'll talk about the last main service category: Databases. Let's get started!

# **Databases** 
In this module, you learn about the last main service category we'll go over: Databases. This is the final pillar of the AWS portfolio, along with Compute and Storage. Databases are used to store data that will constantly be updated through CREATE, UPDATE, and DELETE operations. Data gets retrieved and manipulated by the corresponding users and applications that access it. This is how databases differ from regular storage options.

AWS offers a vast number of database services to fit the needs of any type of customer that wants to use them. Today I'll take about the 4 main ones that are more widely used than the other niche services. We'll talk about RDS, DynamoDB, Redshift, and Aurora.

## **RDS** 
RDS, or Relational Database Service, 

You should choose RDS when you have or require: complex transactions or queries, medium to high query or write rate with up to 30k iops (15k read + 15k write), and no more than a single worker node or shard. You shouldn't choose RDS when you have or require: massive read/write rates (150k write/sec), sharding due to high data size or throughput demands, simple GET or PUT requests and queries that a NoSQL database can handle, or RDBMS (Relational Database Management System) customization.


![EBS Volume Types](/assets/aws-ebs-volumes.jpg)<br/><font size="2.75px"><em>SSD vs HDD, the numbers</em></font>

## **DynamoDB**
DynamoDB is AWS' NoSQL, key-value database offering. First of all, what's NoSQL you might ask. NoSQL, or No Structured Query Language, means this database doesn't use that language to manipulate its data. Data is unstructured and comprised of key-value pairs, with fields not needing to be present in each data entry. This is opposed to rigidly structured data of rows and columns that must be of equal length. If you've heard of MongoDB, this is another example of a NoSQL database. For a visual example of data in NoSQL vs SQL databases, take a look at the graphic below:

![EBS Volume Types](/assets/aws-ebs-volumes.jpg)<br/><font size="2.75px"><em>SSD vs HDD, the numbers</em></font>

DynamoDB is highly performant.

## **Redshift**


## **Aurora**


# **Next Time**
Hope you learned a lot today. There's only 2 more modules left! Can you believe it? We're almost at the end! See you next week when we continue the AWS CCP discussion.

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

[AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/)

*Note: Assets in this post are from AWS Academy's Cloud Foundations course*