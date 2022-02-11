---
layout: post
title:  "Blog 1: Studying for AWS Certified Cloud Practitioner pt.2"
date:   2022-02-11 9:59:31 -0700
categories: jekyll update
published: false
---
![AWS Training and Certification](/assets/aws-training-and-certification.png)
# **Intro and Recap**
Welcome back to my blog! This week we are continuing our discussion of the material that will most likely appear in the AWS Certified Cloud Pracitioner (CCP) Exam. Last time we went over a part of the first module, Cloud Concepts Overview, and briefly discussed 2 important things I learned: the 6 advantages of cloud computing and the AWS Cloud Adoption Framework (CAF). In this post, we'll go over Cloud Economics and Billing. Let's get started!

# **Cloud Economics and Billing**
In this module, you learn about how pricing and billing works in the AWS cloud, ways to save money, technical support models, and a little bit about the service, AWS Organizations. Today, I'll only be discussing the essentials of pricing in AWS and the support models they offer. Although pricing is probably the furthest thing someone technical like a full-stack developer or even a DevOps Engineer cares to know about, it's important to know because nobody has an unlimited budget to work with. We have to work within our pre-defined budgetary constraints. Understanding how pricing works is part of the job. With that out of the way, let's dive in.

## **Fundamentals of Pricing**

![AWS 3 Pricing Fundamentals](/assets/aws-pricing-fundamentals.jpg)

As the picture above shows, there are 3 fundamental drivers of cost with AWS. For the compute category of services, instances are charged by the hour, or second for Linux instances. Pricing is dependent on the instance type. For example, a t2.micro (fit for general purposes) costs less than 
a C4.large (compute optimized). Secondly, storage in services like S3 (Simple Storage Service), EBS (Elastic Block Storage), or EFS (Elastic File System) is typically charged per GB (per month). Lastly, data transfer is a big part of pricing. Remember that *outbound* data transfer is aggregated and charged. Note however, outbound within the same region actually has no charge. Inbound, for the most part, has no charge. Data transfer charges appear on the montly statement as 'data transfer out' and is typically charged by the GB.

## **Pricing Model**
AWS' pricing model consists of 4 main concepts: 
1. pay for what you use
2. pay less when you reserve
3. pay less when you use more
4. pay less as AWS grows

The first discusses how you don't have to pay for any large upfront expenses to start to use AWS services. The second talks about reserving instances (in EC2 and RDS) to save up to 75%. There are 3 options if you want to go this route: all upfront reserved instance (AURI), partial upfront reserved instance (PURI), and no upfront reserved instance (NURI). You save more if you pay for it all upfront. Take a look at the image below.

![AWS Pay Less When You Reserve](/assets/aws-pay-less-reserve.jpg)<br/><font size="2.75px"><em>For EC2 instances, you save money when you reserve and save even more when you pay more in upfront costs</em></font>

The third part of the pricing model talks about taking advantage of discounts when you use more of AWS' services. This is just like when people go to Costco to save money by buying things in bulk. AWS has volume based discounts and tiered pricing available. Finally, you pay less as AWS grows. If you look at the pricing history of various services, you'll see that they've lowered prices many times since launch. In short, remember use, reserve, use more, and AWS grows.

## **Support Models**
AWS currently offers 5 support plans - Basic, Developer, Business, Enterprise On-Ramp, and Enterprise - to choose from, based on your different needs. As a side-note, I'll mention that Enterprise On-Ramp is a fairly new addition having been released for general availability in late November 2021. Since the Cloud Foundations AWS Academy was created in mid/late 2019, you need to be on the lookout for differences from the teaching material. Starting off with the Basic plan, this plan is available from the get-go for free to all AWS customers. You get access to FAQs, forums, basic health checks, the personal health dashboard, and some core Trusted Advisor checks. Basic, since it's free, offers no case support. The Developer plan is geared to, you guessed it, developers using the AWS platform. Besides everything from the Basic plan, they get guidance and technical support. The Business plan is for customers that run a business and use AWS for their production workloads. Enterprise On-Ramp is an in-between, offering more than Business but less than Enterprise. Finally, Enterprise is for customers that run business and mission-critical workloads. They get access to a dedicated technical account manager (TAM) who will help them architect and deploy their infrastructure on AWS. An important thing to look at when comparing the different plans is the response times to varying levels of incident severity. Look at the table below. Note that Enterprise On-Ramp has the same response times as Enterprise except for critical which is 30 minutes or less, as opposed to 15.

![AWS Support Plans Response Times Comparison](/assets/aws-support-response-time-table.jpg)<br/><font size="2.75px"><em>Response Times for the Different Support Plans</em></font>

For more detailed information on the differences between the support plans that AWS offers, check their [website](https://aws.amazon.com/premiumsupport/plans/).

# **Next Time**
Hope you learned a lot today. We'll continue the AWS CCP discussion next week.

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

[AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/)