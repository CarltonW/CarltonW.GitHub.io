---
layout: post
title: Using AWS Config to monitor open RDP port
excerpt: "How to use AWS Config to monitor your resources"
modified: 2020-04-06
tags: [Howto]
comments: true
pinned: true
image:
feature: sample-image-2.jpg
categories: [AWS]
---

AWS Config allows you to monitor changes to your AWS environment and record those changes to an S3 bucket. You can also use AWS Config for remediation when something is out of compliance. Have you ever enabled RDP or another service to allow temporary access and then forgot to remove the security rule? AWS Config is a great tool for monitoring this type of activity. In this post I will walk you through creating a Config rule that monitors public access to RDP.

> ## AWS Config setup ##

<center>Choose your region then open Config under Management & Governance</center>
![AWS Console screen](/img/AWSConfig/aws-console-config.png "AWS Console screen")


<br>
<center>When you open Config for the first time you'll see this screen</center>
![AWS Config dashboard](/img/AWSConfig/aws-console-config-getstarted.png "AWS Config dashboard")


<br>
<center>The settings page opens when you setup your Config rule. You can change these settings or leave the defaults.</center>
[ ![AWS Config settings](/img/AWSConfig/aws-console-config-settings-small.png "AWS Config settings") ](/img/AWSConfig/aws-console-config-settings.png "AWS Config settings")<center><i>Click on image to see larger version</i></center>


<br>
<center>The next step is to pick one of the preconfigured rules or create your own</center>
![AWS Config rules](/img/AWSConfig/aws-console-config-rules.png "AWS Config rules")


<br>
<center>We'll go with one of the preconfigured rules. Search for <i>restricted-common-ports</i></center>
![AWS Config rules](/img/AWSConfig/aws-console-config-searchcommonports.png "AWS Config rules")


<br>
<center>Once you choose the <i>restricted-common-ports</i> rule you'll be giving the option to change settings within that rule as listed below. In this demo I'm only changing a few fields.<br> I also removed some of the other ports that are monitored by default.</center>
[ ![AWS Config rule setup](/img/AWSConfig/aws-console-config-rulesetup1-small.png "AWS Config rule setup") ](/img/AWSConfig/aws-console-config-rulesetup1.png "AWS Config rule setup")<center><i>Click on image to see larger version</i></center>


<br>
<center>Here is the bottom half of the screen. Remediation has a dropdown which allows for many tasks. </center>
[ ![AWS Config rule setup](/img/AWSConfig/aws-console-config-modifyrule2-small.png "AWS Config rule setup") ](/img/AWSConfig/aws-console-config-modifyrule2.png "AWS Config rule setup")<center><i>Click on image to see larger version</i></center>


<br>
<center>After you save the rule you can wait for it to evaluate or manually force it by hitting the re-evaluate button.</center>
[ ![AWS Config rule re-evaluate](/img/AWSConfig/aws-console-config-rules-reevaluate-small.png "AWS Config rule re-evaluate") ](/img/AWSConfig/aws-console-config-rules-reevaluate.png "AWS Config rule re-evaluate")<center><i>Click on image to see larger version</i></center>


<br>
<center>Once your rule is evaluated you can go back to the Config Dashboard and see the status and open the resource from here to make necessary changes to get back into compliance.</center>
[ ![AWS Config Dashboard view of rule status](/img/AWSConfig/aws-console-config-dashboardfinished-small.png "AWS Config Dashboard view of rule status") ](/img/AWSConfig/aws-console-config-dashboardfinished.png "AWS Config Dashboard view of rule status")<center><i>Click on image to see larger version</i></center>

<br>
That's it. You just created an AWS Config rule that will evaluate whether RDP has been opened on any security group in that region. To enable this rule in other regions you'll have to follow the same steps for each region.