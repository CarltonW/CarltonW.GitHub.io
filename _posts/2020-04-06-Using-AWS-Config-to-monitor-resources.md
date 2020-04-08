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

AWS Config allows you to monitor changes to your AWS environment and record those changes to an S3 bucket. You can also use AWS Config for remediation when something is out of compliance. Have you ever enabled RDP or another service to allow temporary access and then forgot to remove the security rule? AWS Config is great at monitoring this type of activity. In this post I will walk you through creating a Config rule that monitors public access to RDP.

> ## Steps to get AWS Config working ##

<center>From the AWS console open Config under Management & Governance</center>
![AWS Console screen](/img/AWSConfig/aws-console-config.png)


<br>
<center>When you open Config for the first time you'll see this screen</center>
![AWS Config dashboard](/img/AWSConfig/aws-console-config-getstarted.png)


<br>
<center>The settings page opens when you setup your Config rule. You can change these settings or leave the defaults.</center>
![AWS Config settings](/img/AWSConfig/aws-console-config-settings.png)


<br>
<center>The next step is to pick one of the preconfigured rules or create your own</center>
![AWS Config settings](/img/AWSConfig/aws-console-config-rules.png)


<br>
<center>We'll go with one of the preconfigured rules. Search for restricted-common-ports</center>
![AWS Config settings](/img/AWSConfig/aws-console-config-searchcommonports.png)
