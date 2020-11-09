---
layout: post
title:  "How to Quick Launch Windows 10 Development Environment"
excerpt: "This tutorial will walk you through getting Windows 10 setup with tools like Powershell 7, Visual Studio Code, Visual Studio 2019 and WSL2"
comments : true
date:   2020-11-09 09:39:39 -0600
categories: [WSL, Windows10]
---
 
#### If you need to build a Windows 10 test environment with Powershell 7, Visual Studio Code and Visual Studio 2019 then you're in the right place. In the steps below I will walk you through building a test environment on your existing PC/laptop using Hyper-V. ####

<br>
#### Prerequisites ####

- **Windows 10 build 1909 or newer**
- **Hyper-V feature installed**

<br>
<br>
## Open Hyper-V and Create Windows 10 dev Virtual Machine ##


<br>
<br>
<center>Open Hyper-V and right mouse click your computer to choose Quick Create</center>
![Quick Create from Hyper-V Console](/img/quicklaunch/QuickCreateButton.png "Quick Create Button")

<br>
<br>
<center>Choose the Windows 10 dev environment and then hit Create Virtual Machine</center>
![Choose Windows 10 OS for dev environment](/img/quicklaunch/ChooseOS.png "Create Virtual Machine")

<br>
<br>
<center>Once you choose to create virtual machine the very large install image is downloaded (17+ Gb)<br>
<i>This will take a while. Good time for a break.</i></center>
![Download starts for Windows 10](/img/quicklaunch/Download.png "Downloading Windows 10 dev")

<br>
<br>
<center>After the image is downloaded it will extract automatically</center>
![Image is extracted](/img/quicklaunch/ExtractingImage.png "Extracting Image")

<br>
<br>
<center>Finally, my virtual machine is created. From here you can edit the settings or Connect. We're going to edit the settings first.</center>
![Virtual Machine Created](/img/quicklaunch/VMCreated.png "Virtual Machine has been created")

<br>
<br>
<center>Make your custom changes to the memory, CPU, etc. and save your settings.</center>
![Virtual Machine Settings](/img/quicklaunch/EditSettingsVM.png "Edit Settings for Virtual Machine")

<br>
<br>
<center>Ready to start Windows 10 dev Virtual Machine.</center>
![Virtual Machine Start](/img/quicklaunch/StartVM.png "Edit Settings for Virtual Machine")

<br>
<br>
<center>Your new Windows 10 environment. Now we can start to customize it.</center>
![Fresh install of Windows 10 dev environment](/img/quicklaunch/VMStarted.png "Fresh install of Windows 10 dev environment")

<br>
<br>
<center>You'll notice the dev environment is installed with Powershell 5.1 by default. If you want to install Powershell 7 you can<br>
<a href "https://docs.microsoft.com/en-us/powershell/scripting/install/migrating-from-windows-powershell-51-to-powershell-7?view=powershell-7">download it from here</a></center>
![Powershell 5 after install](/img/quicklaunch/Powershell6.png "Powershell 5 is installed by default")

<br>
<br>
<center>Another useful tool I like is Windows Terminal. You can you run scripts from Powershell, Command Prompt, WSL distros and Azure Cloud Shell.</center>
![Windows Terminal](/img/quicklaunch/WindowsTerminal.png "Windows Terminal") 

