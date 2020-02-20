---
layout: post
title:  "How to Setup Docker on WSL"
excerpt: "This tutorial will show you how to get Docker up and running on Windows 10 WSL"
comments : true
date:   2019-10-01 20:39:39 -0600
categories: [WSL, Docker]
---

 Containers can provide a quick way to spin up an app without having to worry about the backend OS. With Docker on WSL you can easily test multiple containers. Docker provides some great documentation, but it's a little confusing to get it working with WSL. 
<br/>
<br/>
> ## Get Docker for Windows ##  

Let's head over to the Docker website to download the community edition for our Windows 10 machine. If you search "Docker CE for Windows" you should find the download link for this page [Docker for Windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)  

![Install Docker on Windows 10]({{site.baseurl}}/assets/img/docker/docker-install-windows.png "Install Docker on Windows")  
*(You'll need to create a Docker hub account to download)*  


Install with the defaults (including the option to run Linux container.) Launch docker from the icon on your desktop. You'll be prompted about installing Hyper-V. Hit okay to allow it to install. That will add the Hyper-V feature and reboot your system.  

![Prompt to enable Hyper-V]({{site.baseurl}}/assets/img/docker/docker-install-hyperv.png "Allow Hyper-V feature to install")  

After you've installed Docker and enabled Hyper-V you need to set a feature in Docker to work with WSL. Find the Docker icon on the bottom right corner and right mouse-clike and choose Settings. Check the box next to "Expose Daemon" 

![Enable port on Docker app]({{site.baseurl}}/assets/img/docker/docker-install-switch.png "Enable ports on Docker app")  

We now have Docker running on our Windows 10 machine.    

>## Prepare Ubuntu for Docker setup ##  

We have Docker running on Windows so let's get into WSL/Bash prompt to get it working on the Linux side.  

__Update apt package index:__  
``` sudo apt-get udpate ```  

__Install packages for docker:__ *(copy and paste entire section)*    
```bash
sudo apt-get install apt-transport-https \  
ca-certificates \ 
curl \ 
gnupg-agent \ 
software-properties-common 
```  
<br/>

__Install Docker GPG key:__  
``` bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```  

__Verify key from previous step:__  
``` sudo apt-key fingerprint 0EBFCD88 ```  
<br/>
__Setup the repository:__ *(copy and paste entire section)*   
```bash
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```  

__Run Update Again:__  
``` sudo apt-get update ```  
<br/>


>## Install Docker CE ##    

``` sudo apt-get install docker-ce ```  

>## Install Docker Compose ##    

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
__Set Permissions for binaries:__    

``` sudo chmod +x /usr/local/bin/docker-compose ```  
<br/>


>## Allow Docker to speak to host ##  

We need to edit .bashrc  
``` nano ~/.bashrc ```  

Add the following line to the bottom of the file and save it   
``` export DOCKER_HOST=tcp://localhost:2375 ```  

![Add export to bashrc]({{site.baseurl}}/assets/img/docker/docker-install-bashrc.png "Add export to bashrc")  

__Reload .bashrc:__  
``` source ~/.bashrc ```  

__Allow Docker CLI access without root access__  
``` sudo usermod -aG docker $USER ```  

__Now, restart WSL and test your docker setup from WSL:__  
``` docker run hello-world ```  

<br/>
<br/>


>__References:__  
[https://docs.docker.com/install/linux/docker-ce/ubuntu/](https://docs.docker.com/install/linux/docker-ce/ubuntu/)  
[https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)  














 




























