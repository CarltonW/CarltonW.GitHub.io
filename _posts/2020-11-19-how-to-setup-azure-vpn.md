---
layout: post
title: How to setup Azure VPN
excerpt: "How to setup Azure VPN back to your on-premises environment"
modified: 2020-11-19
tags: [Howto,Azure,VPN,gateway]
pinned: true
comments: true
categories: [Azure]
---

If you're just getting started using Azure one of the first things you might be asked to do is create a site-to-site vpn connection between your on-premises network and Azure. In this post I will walk through setting up an Azure VPN with an on-premises network. Before we get started there are some requirements for your on-premises environment.

>### On-Premises Requirements:

- **On-premises endpoint**  
- **On-premises public IP**  
- **On-premises private subnet**  
<br/>

>### Resources required in Azure to setup a Site-to-Site VPN:

- **Virtual Network Gateway**  
- **Virtual Network**  
- **Local Network Gateway**  
- **Public IP address**  
- **Connection**  
<br/>
<br/>

<center>The Virtual Network Gateway is the resource that ties all of other components together when setting up your VPN. Let's get started creating that resource. From the portal choose <b>Create a Resource</b> and search for "Virtual Network Gateway".</center> 
![Find Virtual Network Gateway in Azure](/img/azurevpn/001-CreateVirtualNetworkGateway.png "Azure Portal find Virtual Network Gateway")
<br>
<br>
<center>Hit <b>create</b> to get the Virtual Network Gateway settings page.</center>
![Create Virtual Network Gateway in Azure](/img/azurevpn/1-CreateVirtualNetworkGateway.png "Azure Portal create Virtual Network Gateway")
<br>
<br>
<center>Here is the settings page for the Virtual Network Gateway. All of the settings with a red asterisk are required. We will create a Virtual Network and Public IP from this settings page. Please make note that even though I changed the SKU to <b>Basic</b> it reverted back to the default of <b>VpnGw1</b>. After you've made all changes to the settings make sure you set the SKU type back to Basic (or whatever SKU you decide on), before proceeding. You can go with the defaults I have below or change them to something else. Go ahead and choose <b>Create virtual network</b></center>
![Virtual Network Gateway Settings in Azure](/img/azurevpn/2-VirtualNetworkGatewayPart1.png "Azure Portal Virtual Network Gateway settings")
<br>
<br>
<center>After you've set the required fields choose to Create a Virtual Network. Give it a name and enter a network and subnet or you can go with the defaults and hit <b>Ok</b>.</center>
![Create the Virtual Network in Azure](/img/azurevpn/3-CreateVirtualNetwork.png "Azure Portal create Virtual Network")
<br>
<br>
<center>Choose to create a new Public IP address and give it a name unless you already have one setup. Again, make sure your SKU has not changed and then hit <b>Review + Create</b>.</center>
![Create the Virtual Network Gateway check SKU in Azure](/img/azurevpn/4-CreateVnetGateway2.png "Azure Portal create Virtual Network Gateway check SKU")
<br>
<br>
<center>Confirm the settings and then hit <b>Create</b></center>
![Confirm Virtual Network Gateway settings in Azure](/img/azurevpn/5-VNetGatewayConfirm.png "Azure Portal Confirm Virtual Network Gateway settings")
<br>
<br>
<center>We now have three of the five components necessary to setup the VPN.</center>
![Virtual Network Created in Azure](/img/azurevpn/6-VnetCreated.png "Azure Portal Virtual Network Created")
<br>
<br>
<center>We can now add the local network gateway. Hit <b>+Add</b></center>
![Add local network gateway in Azure](/img/azurevpn/9-AddLocalNetworkGateway.png "Azure Portal add local network gateway")
<br>
<br>
<center>Type in <b>Local Network Gateway</b> in the search to find the resource.</center>
![Choose local Network gateway in Azure](/img/azurevpn/10-ChooseLocalNetworkGateway.png "Azure Portal choose local network gateway")
<br>
<br>
<center>Create the Local Network Gateway resource</center>
![Create local network gateway in Azure](/img/azurevpn/11-CreateLocalNetworkGateway.png "Azure Portal create local network gateway")
<br>
<br>
<center>Enter the subnet for your on-prem network and the public IP for your on-prem device</center>
![Enter subnet for Local network in Azure](/img/azurevpn/12-LocalNetworkGateway.png "Azure Portal setup local subnet for on-prem network")
<br>
<br>
<center>We need to add a Connection resource to connect our VPN. Choose <b>+Add</b> again.</center>
![Add Connection in Azure](/img/azurevpn/13-AddConnection.png "Azure Portal add Connection")
<br>
<br>
<center>Search <b>Connection</b> to find the resource.</center>
![Create connection between on-prem and Azure](/img/azurevpn/14-CreateConnection.png "Azure Portal create connection between on-prem and vnet")
<br>
<br>
<center>Choose <b>Site-to-Site</b> as the connection type.</center>
![Settings for Connection in Azure](/img/azurevpn/15-ConnectionSave.png "Azure Portal settings for Connection before saving")
<br>
<br>
<center>Verify the Connection settings and hit <b>Ok</b></center>
![Verify connection settings in Azure](/img/azurevpn/16-VerifyConnectionSettings.png "Azure Portal verify connection settings")
<br>
<br>
<center>Now all of our VPN resources are created</center>
![VPN resources are now created in Azure](/img/azurevpn/17-ConnectionCreatedAllResources.png "Azure Portal all resources required for VPN")
<br>
<br>
<center>Open the Connection resource and download the configuration. This will give us the needed information for our on-prem device.</center>
![Download configuration for local router setup in Azure](/img/azurevpn/18-DownloadConfig.png "Azure Portal download config file for local network")
<br>
<br>
<center>Change the device type to the one you have on-prem. If it's not listed choose Generic and then hit the <b>Download Configuration</b> button.</center>
![Verify device type before download in Azure](/img/azurevpn/19-ChooseRouterType.png "Azure Portal verify device type before download")
<br>
<br>
<center>Open the configuration file and make the necessary changes to your on-prem device to create the VPN connection.</center>
![Complete settings for on-prem network device in notepad](/img/azurevpn/20-ConfigSettings.png "settings necessary for on-prem network device setup")
<br>
<br>
<center>After you've created the VPN settings on your on-prem device go back to the Connection in the Azure portal and refresh the page. You should now have 
a connection between your on-prem and Azure.</center>
![VPN is now connected to Virtual Network Created in Azure](/img/azurevpn/21-VPNConnected.png "Azure Portal Virtual Network Created")

<br>
<br>
>__References:__<br>
[https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings)<br>
