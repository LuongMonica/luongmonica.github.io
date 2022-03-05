---
layout: post
title:  "Blog 4: Studying for AWS Certified Cloud Practitioner pt.5"
date:   2022-03-04 9:59:31 -0700
categories: jekyll update
published: false
---
![AWS Training and Certification](/assets/aws-training-and-certification.jpg)
# **Intro and Recap**
Hello again! This week we are continuing our discussion of the material that will most likely appear in the AWS Certified Cloud Pracitioner (CCP) Exam. Last time we went over a part of the fourth module, Cloud Security, and briefly discussed the Shared Responsibility Model, IAM, how to secure accounts and data, and how to ensure compliance. In this post, we'll start diving into the main service categories starting with Networking and Content Delivery. Let's get started!

# **Networking and Content Delivery** 
In this module, you learn about networking in the AWS Cloud. You go over networking basics to make sure you're up to speed, then dive into some of Amazon's networking services including VPC, Route 53, and CloudFront. I'm going to skip over the basics and focus on the services. 

## **Amazon VPC** 
What is a VPC? VPC stands for virtual private cloud; it's your own logically isolated section of the AWS cloud. While it has a somewhat branded name, it really is just a private, virtual network in the cloud. You control all the configuration and resources, including IP address ranges, subnets, and the configuration of route tables and network gateways. Security can be done in 2 different ways, security groups or network access control lists, to create multiple layers of security. A VPC belongs to a single region, while a subnet belongs to a single AZ. You can't change the IP address range of the VPC after creation so you have to really plan it out beforehand; leave enough room for future growth. The largest CIDR block that a VPC can be is /16 or 65536 (2^16) possible addresses. The smallest is /28 or 16 (2^4) possible addresses. While the max a subnet can have is 256 addresses, there are actually 5 reserved IPs so the real number is 251. Take a look at the table below for the reserved IPs and their purposes: 

| **IP Addresses for CIDR block 10.0.0.0/24** | **Reserved for**          |
| :------------------------------------------ | :------------------------ | 
| 10.0.0.0                                    | Network address           |
| 10.0.0.1                                    | Internal communication    |
| 10.0.0.2                                    | DNS resolution            |
| 10.0.0.3                                    | Future use                |
| 10.0.0.255                                  | Network broadcast address |

Within VPC, there are different types of networking solutions you can do to connect your VPC with other services or resources, including another VPC, your own on-prem data center, or an endpoint. To share your VPC with other AWS accounts in the same organization, use VPC Sharing. To connect VPCs, use VPC Peering. To connect your VPC to a remote network, use a VPN gateway and AWS Site-to-Site VPN Connection. To have a dedicated connection to a remote site, use AWS Direct Connect (DX). To connect your VPC to an AWS service endpoint (like S3 or DynamoDB) or an endpoint service powered by PrivateLink, use a VPC endpoint. And finally, if you want to connect your VPC to multiple other VPCs, remote sites, etc, use Transit Gateway to create and amange a single connection from the central gateway into each service/resource across your network. Take a look at the graphic below to see how you can simplify your network topology:

![Transit Gateway](/assets/aws-transit-gw.jpg)<br/><font size="2.75px"><em>Simplify your network topology to hub and spoke (aka star)</em></font>

Moving on to security within a VPC, you can secure your VPC using one or both of these firewall options: security groups (sg) or network access control lists (NACL). Look at the tables below for an example of how rules are defined for each:

![Security Group Rules](/assets/aws-sg.jpg)<br/><font size="2.75px"><em>Only Allow rules</em></font>

![Network ACL Rules](/assets/aws-nacl.jpg)<br/><font size="2.75px"><em>Rule # and Allow or Deny rules</em></font>

As you can see, there are some slight differences in the rules. Besides that, take a look at the table below for even more differences between the two:

| **Attribute**    | **Security Groups** | **Network ACLs**     |
| :--------------- | :------------------ | :------------------- |
| Scope:           | instance level      | subnet level         |
| Supported rules: | allow rules only    | allow and deny rules |
| State:           | stateful (return traffic is automatically allowed, regardless of rules) | stateless (return traffic must be explicitly allowed by rules) |
| Order of rules: | all rules are evaluated before decision to allow traffic | rules are evaluated in number order before decision to allow traffic |

## **Route 53**
Route 53 is AWS' Domain Name Service (DNS). It serves 3 main functions: registering domain names, routing internet traffic to your domain resources, and checking the health of your resources. Route 53 features traffic flow and has a visual editor to manage how your users are routed to your application's endpoints. This service has robust routing capabilities, giving you 7 different policies to choose from:

1. simple 
    - configure standard dns records
    - for use in a single server environment
2. weighted (round robin)
    - route traffic to multiple resources in proportions you specify
    - for use in A/B or blue/green deployments
3. latency based (lbr)
    - Route 53 will pick the route with the lowest latency for the user
4. geolocation
    - route traffic based on the location of your users
5. geoproximity
    - route traffic based on the location of your resources
6. failover (dns failover)
    - failover to a backup site if your primary becomes unreachable
7. multivalue answer
    - respond to dns queries up to 8 healthy reocrds selected at random
    - can combine any of the other routing policies into this one

## **CloudFront**
CloudFront is AWS' Content Delivery Network (CDN). A CDN is a globally distributed system of caching servers that delivers files, data, apps and APIs over the infrastructure with low latency and high transfer speeds. CloudFront uses the global network of edge locations and regional edge caches to deliver content to users faster. There are 4 main pricing points to this service: data transfer out, http(s) requests, invalidation requests, and, optionally, dedicated IP custom SSL certs. 

# **Next Time**
Hope you learned a lot today. We'll continue the AWS CCP discussion next week.

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

[AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/)

[Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)