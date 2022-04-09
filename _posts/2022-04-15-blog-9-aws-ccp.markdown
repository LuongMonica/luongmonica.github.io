---
layout: post
title:  "Blog 9: Studying for AWS Certified Cloud Practitioner pt.10"
date:   2022-04-15 9:59:31 -0700
categories: jekyll update
published: false
---
![AWS Training and Certification](/assets/aws-training-and-certification.jpg)
# **Intro and Recap**
Hello! This is the final week of our discussion of the material that will most likely appear in the AWS Certified Cloud Pracitioner (CCP) Exam. Last time we went over a part of the ninth module, Cloud Architecture, and briefly discussed the Well-Architected Framework, Reliability and High Availablity, and AWS Trusted Advisor.  In this post, we'll talk about the last module: Auto Scaling and Monitoring. Let's get started!

# **Auto Scaling and Monitoring** 
Demand for your application constantly fluctuates, whether it be because it's shopping season, it's the weekend, it's at night, your new marketing campaign has been really successful, a competitor is stealing away users, or you're even getting DDOS-ed, capacity needs dynamically change all the time. To correctly meet demand without under or over-provisioning, you have to constantly monitor your resources and scale automatically. Today we'll talk about 3 services that will help you do just that: ELB, CloudWatch, and EC2 AutoScaling. 

## **ELB** 
ELB, or Elastic Load Balancing, is the way you can juggle the demand to your different resources. An ELB distributes incoming app or network traffic across multiple targets, whether it be in a single or multiple AZs. It offers health checks, security, and monitoring to your targets. Targets can be IP addresses, EC2 instances, containers, Lambda functions, or even another load balancer. There are currently 4 different ELBs: application, network, gateway, and classic. As the names suggest, ALBs are for routing traffic to your applications, NLBs are for handling routing based on IP data, and GLBs are to be used as a gateway for 3rd-party virtual appliances like NGFWs, IDPS, etc. At this point, it's not recommended to use the Classic LB anymore; it only exists for compatability and legacy reasons. The other lbs perform better. For some handy comparisons, take a look at the charts below.

![Load Balancer Comparison Chart](/assets/aws-lb-chart.jpg)<br/><font size="2.75px"><em>Side-by-side comparison of 3 load balancers</em></font>

![Load Balancer Comparison Chart](/assets/aws-lb-comparison.jpg)<br/><font size="2.75px"><em>Most important distinctions between the 4 load balancers</em></font>

If you want more information on the differences between the 4 different types of load balancers, I encourage you to visit the [products comparison page](https://aws.amazon.com/elasticloadbalancing/features/).

For a load balancer to work, it uses listeners to check for connection requests to the targets/target groups. Health checks are used to monitor the health of registered targets. The load balancer will only route traffic to healthy targets. 

![Load Balancer Listener](/assets/aws-lb-listener.jpg)<br/><font size="2.75px"><em>How Elastic Load Balancing works</em></font>

## **CloudWatch**
CloudWatch is an essential service to use in AWS for monitoring. It looks at your AWS resources and applications in your AWS environment. By collecting and tracking standard or custom metrics, it can trigger alarms to send notifications or even take actions on events. For example, you can create a custom metric to track the CPU utilization of a business critical EC2 instance. If it goes over a certain threshold, say 80% for 5 minutes, it'll send a notification to an Amazon SNS topic and start spinning up another EC2 instance. This is an example of a static threshold. You can also create alarms based on anomaly detection and a metric math expression. For static threshold, there's actually a number of things you have to specify. First is the namespace, or where the metric is from. In my example it would be aws/ec2. Next, define the metric. Next, specify the statistic, or how you want to calculate. This could be average, sum, min, max, sample count, or percentile. Next is the time period you want to watch for. After that is the condition, or greater than, less than, etc. Then you can make any additional configurations, like what to do if there's missing data or the number of times the threshold has to be breached before triggering the alarm. Finally, specify the action that you want to take.

## **EC2 Auto Scaling**
EC2 Auto Scaling is all about maintaining app availability by detecting impaired applications or unhealthy instances and replacing them automatically. There's a few things you need in order to make this all work. First is the Auto Scaling group (asg). It's the collection of instances that are logically grouped together to be easily managed. Next you have to define the launch configuration or template. It defines what you're scaling and its associated properties and resources. Launch configurations are not recommended to use anymore and aren't updated with new EC2 features, instead use launch templates. Templates have more features like versioning and the ability to be used for other services besides EC2 Auto Scaling. In a launch configuration/template you have to define the scaling option, or how you will scale your resources. There are 5 scaling options: manual, maintain current instance level at all times, scheduled, dynamic/on-demand, and predictive. With manual you only have to declare the minimum, maximum, and desired capactiy for your asg. Scheduled is best used when you have consistent, predictable traffic patterns that can be scheduled around, like weekends and after work hours. Dynamic scaling lets you monitor different parameters to adjust your scaling. This is done with CloudWatch alarms and ELB. Predictive is a pretty advanced scaling option. It uses AWS Auto Scaling and learns your actual EC2 usage. By using ML models, it can predict when and how to scale your resources. Take a look at the graphic below to see what goes into EC2 Auto Scaling. 

![How EC2 AutoScaling Works](/assets/aws-ec2-autoscaling.jpg)<br/><font size="2.75px"><em>The What, Where, and When of how EC2 AutoScaling works</em></font>

# **Next Time**
That's it! We covered all 10 modules in the AWS Academy Cloud Foundations course. While I didn't have all the time to cover each detail I wanted to in all the topics, I think I did a pretty good overview. Now it's up to you to learn the rest! 

The next blog post is the final one! See you then!

# **More Info**
[AWS Certification](https://aws.amazon.com/certification/)

[AWS CCP Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

[AWS Academy Cloud Foundations course](https://aws.amazon.com/training/awsacademy/)

[Load Balancer Types](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/load-balancer-types.html)

*Note: Assets in this post are from AWS Academy's Cloud Foundations course*