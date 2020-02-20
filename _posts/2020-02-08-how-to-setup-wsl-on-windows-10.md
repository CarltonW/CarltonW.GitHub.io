---
layout: post
title: "How to setup WSL on Windows 10"
excerpt: "This guide will walk you through setting up Windows Subsystem for Linux."
comments : true
date: 2019-09-08 19:32:20 +0300
categories: [WSL]
---

WSL or (Windows Subsystem for Linux), allows for various distros to run inside of Windows 10. In the past you had to spin up a virtual machine on HyperV to get Linux working from your Windows 10 box. WSL offers access to the bash command line without having to build a Linux distro from scratch.  

You'll find WSL offered as a feature addon in Windows 10. In order to get WSL up and running you first need to add the feature by going to **Control Panel** and opening **Windows Features**. Scroll down until you see **Windows Subsystem for Linux** and check the box. Hit **OK** to exit the feature options. _(Restart is required)_

![Add WSL Feature from Features Add/Remove]({{site.baseurl}}/assets/img/wsl/wsl-setup-featuresadd.png)

You also have the option to enable WSL with Powershell:  
```Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux```  
<br/><br/>

## Get a Distro
Now that you have WSL installed (I hope you rebooted after enabling feature), you need to install a Linux distro. You can choose your favorite distro at the Microsoft Store.  Search for "Linux" in store app.

![Linux Distros from Microsoft Store]({{site.baseurl}}/assets/img/wsl/wsl-setup-distros.png)  
<br/>
It's as easy as selecting the one you want and hitting the **Get** button.  
![Hit Get to install the Ubuntu distrobution from Microsoft Store]({{site.baseurl}}/assets/img/wsl/wsl-setup-ubuntu1804.png)  
<br/>
Hit the launch button to get the distro started.  
![Launch Ubuntu distro]({{site.baseurl}}/assets/img/wsl/wsl-setup-launch.png)  
<br/>
The distro will take some time to get setup.  
![Installing distro]({{site.baseurl}}/assets/img/wsl/wsl-setup-start.png)  
<br/>
After the initial setup you'll be prompted for a login name and password (don't forget your password)  
![Installing distro]({{site.baseurl}}/assets/img/wsl/wsl-setup-newuser.png)  
<br/>
There you go. You now have Ubuntu 18.04 running on Windows 10!  
![Installing distro]({{site.baseurl}}/assets/img/wsl/wsl-setup-bash.png)  
<br/>
### When you want to access your distro you have many options: ###  
1. Launch Ubuntu (distro you installed) from Start Menu
2. From command prompt Windows button + R then type "bash"
3. From Powershell prompt type "bash"
4. From Powershell or CMD prompt type name of distro "ubuntu1804"

That's all there is to getting WSL running in Windows 10. If you see any typos or anything that's not correct please let me know in the comments below.  
Thanks!


