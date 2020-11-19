---
layout: post
title:  "Working with WSL on Windows 10"
excerpt: "Learn how to navigate WSL (Windows Subsystem for Linux) and make some tweaks"
tags: [WSL,Windows 10]
comments : true
date:   2020-02-11 20:39:39 -0600
categories: [WSL]
---

  WSL (Windows Subsystem for Linux), provides access to Linux from your Windows 10 system without having to run a virtual machine or dual boot. In a previous post I walked through [installing WSL](../2020-02/how-to-setup-wsl-on-windows-10). Now that we have WSL installed let's take a look at getting it setup and launching some Linux distros. 
<br/>
<br/>
<br/>
<h2><b>WSL Color settings</b></h2>  

The colors used for the WSL command prompt are hard to see and it's even worse if you launch WSL from Powershell.

![WSL Bash Color]({{site.baseurl}}/img/wsl/wsl-command-color.png "WSL Bash Color")  

To change the colors for the command prompt run wsl and edit the .bashrc file.  

``` nano ~/.bashrc ```  

Uncomment the following line:  

``` force_color_prompt=yes ```  

About fourteen lines below that change this line:  
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
<br/>

To this:  
<mark>
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;37m\]\u@\h\[\033[00m\]:\[\033[01;37m\]\w\[\033[00m\]\$ '
</mark>
<br/> 

After you save the file reload it so the changes take affect:  

``` . ~/.bashrc ```  

This changes the prompt color to white. ([list of color codes](https://misc.flogisoft.com/bash/tip_colors_and_formatting))

![WSL Bash New Color]({{site.baseurl}}/img/wsl/wsl-command-newcolor.png "WSL Bash New Color")  
<br/>
<br/>
<h2><b>WSL commands </b></h2>  

List Linux distros installed on WSL  
``` wslconfig /l ```   

![WSLconfig distro list]({{site.baseurl}}/img/wsl/wsl-command-distros.png "WSLconfig distro list")  
<br/>
Change default distro 
``` wslconfig /s SLES-15 ``` *(replace **SLES-15** with the distro you want to make default)*

![WSLconfig distro change]({{site.baseurl}}/img/wsl/wsl-command-change.png "WSLconfig distro change")  
<br/>
You can also unregister an installed distro *(This will destroy data associated with distro)*  

`` wslconfig /u SLES-15 `` 

![WSLconfig distro unregister]({{site.baseurl}}/img/wsl/wsl-command-unregister.png "WSLconfig distro unregister")  
<br/>
You can launch specific distro by name  

`` wsl -d SLES-15 `` **replace SLES-15 with distro you want to launch**  

![WSL distro launch]({{site.baseurl}}/img/wsl/wsl-command-launch.png "WSL distro launch")   

<br/>
<br/>
<h2><b>Update WSL Distro</b></h2>  

Before you start installing packages it's a good idea to update. (If you don't you might get this error message)<br/>
***E: Invalid operation update***   

Run the following commands to update (Ubuntu 18.04):  

``` sudo apt update ```  

``` sudo apt upgrade ```  
<br/>
<br/>
<h2><b> WSL and Bash </b></h2>  

Get a list of bash commands without having to go into your Linux distro

![WSL Bash help]({{site.baseurl}}/img/wsl/wsl-bash-list.png "WSL Bash Help")   


Run multiple screens within your WSL distro with tmux  
(checkout this great [tutorial for using tmux](http://bit.ly/2mnxAoJ))  

![WSL Bash tmux]({{site.baseurl}}/img/wsl/wsl-bash-tmux.png "WSL Bash tmux")  


Run Windows executable apps from bash prompt  

![WSL Bash Winapps]({{site.baseurl}}/img/wsl/wsl-bash-exe.png "WSL Bash Winapps")  
<br/>
<br/>
Hopefully these setup tips will help some folks get familiar with WSL.  
If you see anything in this post that's not correct or you have something I can add please let me know in the comments below.  



  
  
