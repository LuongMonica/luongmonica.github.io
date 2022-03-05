---
layout: post
title:  "Blog 3: Studying for AWS Certified Cloud Practitioner pt.4"
date:   2022-02-26 9:59:31 -0700
categories: jekyll update
---
![AWS Training and Certification](/assets/aws-training-and-certification.jpg)
# **Intro and Recap**
Hello again! This week we are continuing our discussion of the material that will most likely appear in the AWS Certified Cloud Pracitioner (CCP) Exam. Last time we went over a part of the third module, Global Infrastructure Overview, and briefly discussed the parts of what makes up the global AWS infrastructure and some services and service categories. In this post, we'll go over a very important topic: Cloud Security. Let's get started!

# **Cloud Security**
In this module, you learn about how highly valued security is in AWS. You learn about the Shared Responsibility Model, IAM, some ways you can secure your accounts and data, and how to ensure compliance in the cloud. 

## **Shared Responsibility Model**
While AWS is an amazing cloud platform that is seemingly magical, that doesn't mean it can do all the work for you in terms of security and compliance. On the contrary, security and compliance is a "shared responsibility" between AWS and the customer who uses it. The shared model that AWS has come up with outlines the parts that the customer and AWS is in charge of. AWS is responsible for the security "of" the cloud, while the customer is responsible for the security "in" the cloud. What this means is that AWS takes care of all the operational burdens by protecting the hardware and infrastructure that AWS runs on, as well as software including compute, database, and networking that they provide directly. Meanwhile, the customer has to take responsibility for the resources and other things that they place into the AWS Cloud. They have to handle the configuration of the OS, network, and firewall that they choose to use. They also have to handle their apps and the identity and access management of them. They have to protect their data, both at rest and in transit. Basically, anything that's owned by the customer is their security responsibility. Take a look at the graphic below for a summarized version of the model.

![AWS Shared Responsibility Model](/assets/aws-shared-responsibility-model.jpg)<br/><font size="2.75px"><em>AWS and the Customer: what security responsibilities each are responsible for</em></font>

## **IAM (Identity and Access Management)**
IAM is an integral part of AWS. It helps you manage access to your AWS resources by defining fine grained access rights that declare who can access, which resources and what can the user do with those resources, and how those resources can be accessed. When talking about IAM, it's necessary to first define a few key terms related to it. An IAM user is a person or app that can authenticate with an AWS account. An IAM policy is a (JSON) document that outlines the resources that can be accessed and to what extent. An IAM role is a temporary set of permissions for making AWS service requests. Think of a role like using 'sudo'. Now with IAM, they take after the Principle of Least Privilege, meaning all perms are denied by default. Denies will always take precedence over allows. Take a look at the picture before for the decision making flow.

![IAM Permissions Flow](/assets/aws-iam-perm-flow.jpg)<br/><font size="2.75px"><em>How IAM determines permissions</em></font>

## **Securing Accounts and Data**
We've talked about security on a high-level, but how do you actually secure your AWS accounts and data? What services can you use to help you achieve security?

The first thing to do when you create a new AWS account is to go through a checklist of security measures for the account:
1. Stop using root ASAP
    - It's not a good practice to use the root account for daily activities; it opens up a hole in your security posture. Instead you should create an admin account and do most of your operations with that account. There are only certain actions including changing AWS support plans, activating IAM access to the Billing and Cost Management Console, and restoring an IAM user's permissions, that you can only do with a root account. Otherwise, you could and should just use an account with the correct privileges. 
2. Enable MFA for everyone
    - Make it more difficult for hackers to get into your account by enabling MFA, either with virtual MFA-compliant apps, u2f security key devices, or hardware options like key fobs or display cards. 
3. Use CloudTrail
    - CloudTrail provides you with the event history of the past 90 days of account activity. Find out what users are doing and look out for any suspicious activity.
4. Enable Billing Reports like Cost and Usage Report
    - Take note of these reports to find out how much you're spending and on what. You might discover that there are charges that you don't recognize.

Now when thinking about how to protect data, you have to keep in mind that it's your responsibility to protect data at rest, like stored in an S3 bucket or an EBS volume, and in transit, like when it's moving across your network. You can protect your data by encrypting it with a secret key. AWS offers their KMS (Key Management Service) which encrypts and decrypts your data automatically without having to worry about making changes to your app to read data. S3, EBS, EFS, and RDS are just some services that are compatible with KMS. For protecting data in transit, you can use another service, AWS Certificate Manager (ACM) to manage, deploy, and renew TLS/SSL certs.

## **Working to Ensure Compliance**
AWS works with certifying bodies and independent auditors to ensure that their policies, controls, and processes are appropriately compliant. You can get access to documentation and other compliance related information through AWS Artifact. To help assess, audit, and evaluate the configuration of your resources to ensure compliance, use AWS Config. It continuously monitors your configs and compares them against the desired outcome, notifying you if the recorded config and desired one is not the same. AWS Config can also show you a record of all your config changes and history, making it easy to see changes for troubleshooting and analysis and even help prepare you with all the needed information for an upcoming audit. 

# **Next Time**
Hope you learned a lot today. We'll continue the AWS CCP discussion next week.

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

[AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/)

[AWS Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)
