---
layout: post
title:  "How to Quick Launch Windows 10 Development Environment"
excerpt: "This tutorial will walk you through getting Windows 10 setup with tools like Powershell 7, Windows Terminal, Visual Studio Code, Visual Studio 2019 and WSL2"
comments : true
date:   2020-11-09 09:39:39 -0600
categories: [WSL, Windows10]
---
 
__If you need to build a Windows 10 test environment with Powershell 7, Windows Terminal, WSL2, Visual Studio Code and Visual Studio 2019 then you're in the right place. In the steps below I will walk you through building a test environment on your existing PC/laptop using Hyper-V.__

<br>
#### Prerequisites ####

- **Windows 10 build 2004 or newer**
- **Hyper-V feature installed**

<br>
<br>
### Open Hyper-V and Create Windows 10 dev Virtual Machine ###


<br>
<br>
<center>Open Hyper-V and right mouse click your computer to choose Quick Create</center>
![Quick Create from Hyper-V Console](/img/quicklaunch/QuickCreateButton-50percent.png "Quick Create Button")

<br>
<br>
<center>Choose the Windows 10 dev environment and then hit Create Virtual Machine</center>
![Choose Windows 10 OS for dev environment](/img/quicklaunch/ChooseOS-50percent.png "Create Virtual Machine")

<br>
<br>
<center>Once you choose to create virtual machine the very large install image is downloaded (17+ Gb)<br>
<i>This will take a while. Good time for a break.</i></center>
![Download starts for Windows 10](/img/quicklaunch/Download-50percent.png "Downloading Windows 10 dev")

<br>
<br>
<center>After the image is downloaded it will extract automatically</center>
![Image is extracted](/img/quicklaunch/ExtractingImage-50percent.png "Extracting Image")

<br>
<br>
<center>Finally, my virtual machine is created. From here you can edit the settings or Connect. We're going to edit the settings first.</center>
![Virtual Machine Created](/img/quicklaunch/VMCreated-50percent.png "Virtual Machine has been created")

<br>
<br>
<center>Make your custom changes to the memory, CPU, etc. and save your settings.</center>
![Virtual Machine Settings](/img/quicklaunch/EditSettingsVM-50percent.png "Edit Settings for Virtual Machine")

<br>
<br>
<center>Ready to start Windows 10 dev Virtual Machine.</center>
![Virtual Machine Start](/img/quicklaunch/StartVM-50percent.png "Edit Settings for Virtual Machine")

<br>
<br>
<center>Your new Windows 10 environment. Now we can start to customize it.</center>
![Fresh install of Windows 10 dev environment](/img/quicklaunch/VMStarted-50percent.png "Fresh install of Windows 10 dev environment")

<br>
<br>
<center>You'll notice the dev environment is installed with Powershell 5.1 by default. If you want to install Powershell 7 you can download it from (https://docs.microsoft.com/en-us/powershell/scripting/install/migrating-from-windows-powershell-51-to-powershell-7?view=powershell-7)</center>
![Powershell 5 after install](/img/quicklaunch/Powershell6-50percent.png "Powershell 5 is installed by default")

<br>
<br>
<center>A useful tool that's included in this image is Windows Terminal. You can run scripts from Powershell, Command Prompt, WSL distros and Azure Cloud Shell.</center>
![Windows Terminal](/img/quicklaunch/WindowsTerminal-50percent.png "Windows Terminal") 

<br>
<br>
<center>Let's test out WSL. From the Start menu launch Ubuntu. Unfortunately, this does not work out of the box.</center>
![Launch Ubuntu WSL](/img/quicklaunch/LaunchUbuntu-50percent.png "Launch Ubuntu WSL")

<br>
<br>
<center>As you can see the subsystem for linux and virtualization are already enabled.</center>
![Subsystem and virtualization enabled](/img/quicklaunch/WSLEnabled-50percent.png "Subsystem and virtualization already enabled")

<br>
<br>
__You need to enable nested virtualization in order to launch Ubuntu. Shutdown the VM and run this powershell command from the physical Windows 10 device (*not from the VM*)__
```
Set-VMProcessor -VMName "Windows 10 dev environment" -ExposeVirtualizationExtensions $true
```
<br>
<br>
<center>Now you can power up the virtual machine and launch Ubuntu. You're all set!</center>
![Ubuntu now works](/img/quicklaunch/UbuntuWorks-50percent.png "Ubuntu now works")

<br>
<br>
You now have a Windows 10 dev environment with WSL2, Powershell 7, Windows Terminal, Visual Studio Code and Visual Studio 2019. I hope this article was helpful. If you see something that you would like to add please post your comments below.

<br>
<br>
>__References:__<br>
[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)<br>
[https://docs.microsoft.com/en-us/powershell/scripting/install/migrating-from-windows-powershell-51-to-powershell-7?view=powershell-7](https://docs.microsoft.com/en-us/powershell/scripting/install/migrating-from-windows-powershell-51-to-powershell-7?view=powershell-7)<br>
[https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/user-guide/nested-virtualization](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/user-guide/nested-virtualization)

