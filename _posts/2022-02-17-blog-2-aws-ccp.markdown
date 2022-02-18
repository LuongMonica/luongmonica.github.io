---
layout: post
title:  "Blog 2: Studying for AWS Certified Cloud Practitioner pt.2"
date:   2022-02-17 9:59:31 -0700
categories: jekyll update
published: false
---
![AWS Training and Certification](/assets/aws-training-and-certification.jpg)
# **Intro and Recap**
Hello again! This week we are continuing our discussion of the material that will most likely appear in the AWS Certified Cloud Pracitioner (CCP) Exam. Last time we went over a part of the second module, Cloud Economics and Billing, and briefly discussed 3 important things I learned: the fundamentals of pricing, AWS' pricing model, and the 5 different support models. In this post, we'll go over Global Infrastructure Overview. Let's get started!

# **Global Infrastructure Overview**
In this module, you learn about how AWS' global infrastructure is designed and a quick overview of some of the service categories and services that will be covered more fully in later modules. 

## **Global Infrastructure**
The AWS Cloud is comprised of different building blocks. At the top level is a region. A region is a geographical region of the world, such as Northern Virigina (us-east-1) or Ireland (eu-west-1). `us-east-1` is what is called a region code. These are used for a number of things like endpoints or when you programmatically interact with AWS. Each region has full redundancy and connectivity to the network; they communicate between each other using AWS' network infrastructure. If you want to replicate data across regions, you'll have to setup or configure that yourself. Each region usually has at least 2 or more Availability Zones, or AZs. That brings us to the next piece of the puzzle. An AZ is a fully isolated partition of the AWS infrastructure. They are designed for fault tolerance and are interconnected with other AZs by using high speed private networking. It's recommended to replicate data and resources across multiple AZs for resiliency. Each AZ typically has 3 or more data centers. Each data center is designed for security. Their locations are not disclosed and only access for a limited set of employees is allowed. They have redundant power, networking, and connectivity. This is to reduce outages and data loss due to natural disasters like fires, floods, earthquakes, tornadoes, etc. You can *not* choose a specific data center for your data, application, or resources to be placed. The highest level of granularity is an AZ.

![AWS Regions, AZs, and Datacenters](/assets/aws-region-az.jpg)

Currently, there are 26 regions, 84 AZs, 8 upcoming regions, and 300+ edge locations. You can go to [this page](https://aws.amazon.com/about-aws/global-infrastructure/#AWS_Global_Infrastructure_Map) for a constantly updated list of the statistics.

You should select a region by thinking about:
- any legal requirements or data goverance laws,
- proximity to customers (latency),
- services available within a region,
- and costs.

Take all these points in mind as you choose a region. You might prioritize something like latency over costs, depending on your needs and business requirements. Of course, if any legal requirements apply to you, you should abide by them else you might incur large penalty fees or lose customer satisfaction.

Besides regions, AZs, and data centers, there are also points of presence (POP). POP is used by services like CloudFront, AWS Shield, Web Application Firewall (WAF), and Route53 to deliver content to end-users with lower latency. They find the best possible way to route a request. POP are edge locations + regional edge caches. A regional edge cache is used to store content with infrequent access.

There are 3 benefits to the AWS infra: elasticity and scalability, fault tolerance, and high availability. Elasticity and scalability means being able to react to demand dynamically. Fault tolerance means being able to continue operations even with degraded services or failure. High availability means minimized downtime with no human interaction.

## **Services and Service Categories**
AWS is based on their foundational services of compute (EC2, ELB, EC2 Auto Scaling, etc), networking (VPC, etc), and storage (S3, EBS, S3 Glacier, etc). We can further divide the services into 26 service categories, which includes analytics, database, security, identity, and compliance, and networking and content delivery.

![AWS Service Categories](/assets/aws-service-categories.jpg)<br/><font size="2.75px"><em>Outdated picture. Currently 26 categories with the addition of Containers and Quantum Technologies. Some have also been renamed.</em></font>

# **Next Time**
Hope you learned a lot today. We'll continue the AWS CCP discussion next week.

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

[AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/)

[Global Infra Map](https://aws.amazon.com/about-aws/global-infrastructure/#AWS_Global_Infrastructure_Map)

[Global Infra Regions & AZs](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)