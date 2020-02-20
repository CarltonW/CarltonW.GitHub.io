---
layout: post
title:  "How to run CentOS 7 on WSL"
excerpt: "Find out how to get CentOS running on WSL"
comments : true
date:   2020-02-19 20:39:39 -0600
categories: [Linux, WSL]
---

Microsoft provides WSL as a way to bridge the gap between the Windows and Linux world. You can choose from several distros that are available in the Microsoft store, but one that's missing is CentOS. The tutorial below will walk you through installing CentOS on WSL using Docker containers.   


### Prerequisites:    

**Windows 10 Enterprise (build 1903 or newer)**  
**WSL feature installed ([tutorial](../how-to-setup-wsl-on-windows-10.markdown))**  
 **Docker setup for Windows and WSL ([tutorial](../Docker-on-WSL.markdown))**  
<br/>
>## Enter these commands to complete the CentOS install from WSL prompt:  

>```bash
>docker image pull centos
>docker create -i centos bash
>docker export <first few digits of image number> > centos.tar
>```  

>```powershell
powershell.exe
wsl --import CentOS-WSL .\CentOSStorage\ centos.tar
```  

>## Test new distro
```bash
wsl -d CentOS-WSL
cat /etc/centos-release
```

<br/>
**Here is a complete rundown on the commands:**  
![Docker commmands to install CentOS on WSL]({{site.baseurl}}/img/centos/centos-install.png "Docker commands to install CentOS on WSL")  
<br/>
<br/>


Thanks to [Craig Loewen](https://twitter.com/craigaloewen) for his help on this.












