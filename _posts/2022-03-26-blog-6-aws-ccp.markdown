---
layout: post
title:  "Blog 6: Studying for AWS Certified Cloud Practitioner pt.7"
date:   2022-03-25 9:59:31 -0700
categories: jekyll update
published: false
---
![AWS Training and Certification](/assets/aws-training-and-certification.jpg)
# **Intro and Recap**
Hello again! I've enjoyed my short spring break but now it's time to get back to work! This week we are continuing our discussion of the material that will most likely appear in the AWS Certified Cloud Pracitioner (CCP) Exam. Last time we went over a part of the sixth module, Compute, and briefly discussed the services of EC2 and Lambda. We also talked about how to optimize costs for EC2 through different payment models. In this post, we'll talk about another main service category: Storage. Let's get started!

# **Storage** 
In this module, you learn about the next pillar in AWS' main service categories: Storage. Where and how do you keep your data, whether it be for an EC2 instance, your application, or another purpose? Well with AWS, they provide a few different storage solutions to meet each of your needs. The main services, and the ones we'll talk about today, are EBS, EFS, and S3. 

Before we dive into each service, let's first talk about the different types of storage available: block and object storage. EBS is *block* storage while S3 is *object* storage. So, you might ask, what's the difference? Let's say you wanted to make a change to one character in a file. With block storage, you would simply replace the block that the character is stored in. With object storage however, you would have to replace the entire file. 

## **EBS** 
Starting off with EBS, or Elastic Block Storage, this is a service that you are already familiar with if you've used EC2. An EBS volume is the persistent, or non-volatile, block storage that is used to hold the OS and filesystem of your EC2 instance. EBS volumes are replicated across AZs and have 5 9s of availability. EBS volumes are divided into 2 types: SSD (solid state drive) and HDD (hard disk drive). Furthermore, each type of volume is split into 2 more types, based on the purpose you want to use them for. In general, SSDs are faster but more costly. If you have a focus on the most amount of storage at the lowest cost, go with HDDs, especially the cold version. Also, be aware that only SSDs can be used as a boot volume. Take a look at the table below for number comparisons:

![EBS Volume Types](/assets/aws-ebs-volumes.jpg)<br/><font size="2.75px"><em>SSD vs HDD, the numbers</em></font>

## **EFS**
Elastic File System is your shared file storage in the cloud. EFS uses NFS (network file system) to allow EC2 instances in the same region to access a shared file system. So, login to one EC2, create some files, then login to another EC2 and see those files there as well. 

To setup an EFS, follow these steps:
1. Create your EC2 instances
2. Create your EFS
3. Create mount targets in the appropriate subnets
4. Connect the EC2 instances to the mount targets
5. Test and verify

These are the basic steps but you'll also have to do a few more steps to get everything up and running, including: making sure the security group for your mount point and instances allow traffic from port 2049 (NFS), installing 'nfs-client' on your instances, making a directory for your mount, and mounting EFS to that directory you created. 

![EFS Diagram](/assets/aws-efs.jpg)<br/><font size="2.75px"><em>Example of EFS in a VPC</em></font>

## **S3**
Simple Storage Service, better known as S3, is the quintessential storage solution for AWS. Use it to store just about anything from Terraform state files to your website's HTML pages and images. Storage is virtually unlimited (a single object is limited to 5TB), so go wild (while keeping costs in mind). S3 is replicated and stored across at least 3 AZs and boasts 11 9s of durability so you're almost guaranteed to never lose your data. S3 uses special terminology that you should know. Data is stored as objects and the containers that hold objects are called buckets. With S3, there are 6 different storage classes you can choose from to meet your needs: 
1. standard
2. intelligent tiering
3. standard infrequent access (standard-ia)
4. one zone-ia
5. glacier
6. glacier deep archive

Intelligent tiering optimizes your cost by automatically moving your data to different storage classes. The infrequent access classes are cheaper and for data that you don't touch often. When you do need to access the data, it's still pretty quick. One Zone-IA is used when you don't need your data to be as highly available as Standard. Instead of replicating across at least 3 AZs, your data is only in 1 AZ. The glacier tiers are for cold storage or archival purposes. It's meant for data that you have to keep, but will almost never need to access. Accessing data in glacier classes is not real-time and can take anywhere from 1 minute to 12 hours. Glacier Deep Archive is the cheapest option because of its long retrieval times (within 12 hours). Take a look at the graphics below to compare the different storage classes and see the difference between S3 and S3 Glacier. 

![S3 Storage Classes](/assets/aws-s3-comparison.jpg)<br/><font size="2.75px"><em>Comparison of features for each S3 storage class</em></font>

![S3 vs S3 Glacier](/assets/aws-s3-vs-s3-glacier.jpg)<br/><font size="2.75px"><em>S3 vs S3 Galcier</em></font>

As your data ages, you'll find that you won't have to access it as much as you used to. To save on costs while still complying with any data regulations, you can setup a lifecycle policy. This enables you to automatically delete or move data based on age. Policies can be created per object or per bucket. Take a look at the graphic below for a great example of a full lifecycle policy:

![S3 Lifecycle Policy](/assets/aws-s3-lifecycle-policy.jpg)<br/><font size="2.75px"><em>Example lifecycle policy for S3: After 30 days, object is moved to Standard-IA. After 60 days, object is moved to Glacier. After 365 days, the object is deleted. </em></font>

# **Next Time**
Hope you learned a lot today. We'll continue the AWS CCP discussion next week.

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

[AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/)

*Note: Assets in this post are from AWS Academy's Cloud Foundations course*