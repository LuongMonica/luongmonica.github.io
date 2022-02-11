---
layout: post
title:  "Blog 0: Studying for AWS Certified Cloud Practitioner pt.1"
date:   2022-01-29 9:59:31 -0700
categories: jekyll update
---
![AWS Training and Certification](/assets/aws-training-and-certification.png)
# **Intro**
Amazon Web Services (AWS) is the leading platform for cloud computing services. It dominates the world of cloud providers, having a fair margin over its other competitors, Azure and Google Cloud Platform (GCP). Getting an AWS certification helps you stand out from the crowd, allowing you to validate your knowledge and expertise on AWS and, in general, cloud computing. I have decided to go after the foundational certification of Cloud Practitioner (CCP) and I plan to take the exam fairly soon! In my blogs on AWS CCP, I'll talk about some of the important topics I've learned while studying for the exam, including cloud concepts, security and compliance, some different service categories, and billing and pricing. Let's get started!

# **Cloud Concepts Overview**
This is the first module in the [AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/) I took. In this module, you basically learn about what the cloud is, why you'd use it, an overview of what AWS provides, and how to migrate to the cloud. I'll talk about the 2 topics I didn't exactly know about before. 

## **Advantages of Cloud Computing**
AWS lists 6 advantages of cloud computing: 
1. trade Capex (capital expense) for variable expense
2. economies of scale
3. stop guessing capacity
4. increase speed and agility
5. stop spending money on running and maintaining datacenters
6. go global in minutes

The first one talks about using cloud computing because of its pricing models. Instead of spending money on acquiring, upgrading, and maintaining physical resources regardless of whether you use them to their full potential, you should use the cloud to pay only for what you consume. The second one is talking about the enconomic principle "economies of scale". AWS has an extremely large customer base. They are able to pass on the savings they make to its customers because of the aggregate usage among them. Third, you don't have to predict the capacity you should provision. Cloud resources are flexible, elastic, and dynamically scalable. The fourth talks about the speed and agility that instances and other resources can be spun up (in a matter of minutes or even seconds!) The fifth argues that you should leave the running and maintaining of datacenters to AWS and instead redirect costs to better uses like customer satisfaction and product development. And lastly, AWS has datacenters all over the world. You can easily deploy globally in a matter of minutes. 

The mnemonic I came up for this was: Cappy Enables Capacity Speed Maintenance Globally. Mnemonics work best when they're personal and odd/funny. Anything that will help you remember a list of stuff. 

## **AWS Cloud Adoption Framework**
The AWS Cloud Adoption Framework (CAF) is a set of guidance and best practices to help organizations build an approach to cloud computing across the org and throughout the IT lifecycle to accelerate successful cloud adoption. It's divided into 6 areas of focus, or "perspectives", which each have a set of responsibilities, or "capabilities". 

![AWS CAF](/assets/aws-caf.jpg)<br/><font size="2.75px"><em>Cloud Adoption Framework Perspectives</em></font>

The 6 perspectives are Business, People, Governance, Platform, Security, and Operations. The first (or left) 3 have a focus on business capabilities while the last (or right) 3 have a focus on technical capabilities. So for example, the Platform perspective consists of people like cloud architects and IT managers. Their job is to make sure they understand the cloud platform that they are migrating to and the services that they provide. They must be able to describe their target architecture in detail and can use the CAF for principles and patterns of developing solutions in the cloud. My mnemonic is Big Pink Gorilla Powerfully Slams Octopus. It's weird, I know.

# **Next Time**
Hope you learned a lot today. We'll continue the AWS CCP discussion next week.

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)