---
layout: post
title: How to setup Azure VPN
excerpt: "How to setup Azure VPN back to your on-premises environment"
modified: 2020-11-19
tags: [Howto,Azure,VPN,gateway]
comments: true
image:
feature: sample-image-2.jpg
categories: [Azure]
---

In this post I will walk through setting up an Azure VPN with an on-premises network. Before we get started there are some requirements for your on-premises environment.<br>

>#### Requirements: ####
>
>- **On-premises endpoint** 
>- **On-premises public IP**
>- **On-premises private subnet**
<br>
![Create Virtual Network Gateway in Azure](/img/azurevpn/1-CreateVirtualNetworkGateway.png "Azure Portal create Virtual Network Gateway")
<br>
![Virtual Network Gateway Settings in Azure](/img/azurevpn/2-VirtualNetworkGatewayPart1.png "Azure Portal Virtual Network Gateway settings")
<br>
![Create the Virtual Network in Azure](/img/azurevpn/3-CreateVirtualNetwork.png "Azure Portal create Virtual Network")





<br>
<br>
>__References:__<br>
[https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings)<br>
