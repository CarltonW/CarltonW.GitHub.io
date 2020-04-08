---
layout: post
title: Using AWS Config to monitor resources
excerpt: "How to use AWS Config to monitor your resources"
modified: 2020-04-06
tags: [Howto]
comments: true
pinned: true
image:
feature: sample-image-2.jpg
---

AWS Config allows you to monitor changes to your AWS environment and record those changes to an S3 bucket. You can also use AWS Config for remediation when something is out of compliance. Have you ever enabled RDP or another service to allow temporary access and then forgot to remove the security rule? AWS Config is great at monitoring this type of activity.

In this post I will walk you through creating a Config rule that monitors public access to RDP. 

<left>From the AWS console open Config under Management & Governance
![AWS Console screen](/img/AWSConfig/aws-console-config.png)</left>


<left>When you open Config for the first time you'll see this screen.</left>
![AWS Config dashboard](/img/AWSConfig/aws-console-config-getstarted.png)



