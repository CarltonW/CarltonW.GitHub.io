---
layout: post
title:  "How to Quick Launch Windows 10 Development Environment"
excerpt: "This tutorial will walk you through getting Windows 10 setup with tools like Powershell 7, Visual Studio Code, Visual Studio 2019 and WSL2"
comments : true
date:   2020-11-09 09:39:39 -0600
categories: [WSL, Windows10]
---

### If you need to build a Windows 10 test environment with Powershell 7, Visual Studio Code and Visual Studio 2019 then you're in the right place. In the 
steps below I will walk you through building a test environment on your existing PC/laptop using Hyper-V. (Requires Windows 10 build 1909 or newer)

#### Prerequisites

- **Windows 10 build 1909 or newer**
- **Hyper-V feature installed**

## Open Hyper-V and Create Windows 10 dev Virtual Machine ##

<center>Open Hyper-V and right mouse click your computer to choose Quick Create</center>
![Quick Create from Hyper-V Console](/img/quicklaunch/QuickCreateButton.png "Quick Create Button")


<br>
<center>Choose the Windows 10 dev environment and then hit Create Virtual Machine</center>
![Choose Windows 10 OS for dev environment](/img/quicklaunch/ChooseOS.png "Create Virtual Machine")

<br>
<center>Once you choose to create virtual machine the very large install file is downloaded
*This is a very large image. Good time for a break.*</center>
![Download starts for Windows 10](/img/quicklaunch/Download.png "Downloading Windows 10 dev")

<br>
<center>After the image is downloaded it will extract automatically</center>
![Image is extracted](/img/quicklaunch/ExtractingImage.png "Extracting Image")

<br>
<center>Finally, after an hour my virtual machine is created. From here you can edit the settings or Connect. We're going to edit the settings first.</center>
![Virtual Machine Created](/img/quicklaunch/VMCreated.png "Virtual Machine has been created")

<br>
<center>Make your custom changes to the memory, CPU, etc. and save your settings.</center>
![Virtual Machine Settings](/img/quicklaunch/EditSettingsVM.png "Edit Settings for Virtual Machine")

<br>
<center>Ready to start Windows 10 dev Virtual Machine.</center>
![Virtual Machine Start](/img/quicklaunch/StartVM.png "Edit Settings for Virtual Machine")

<br>
<center>Your new Windows 10 environment. Now we can start to customize it.</center>
![Fresh install of Windows 10 dev environment](/img/quicklaunch/VMStarted.png "Fresh install of Windows 10 dev environment")

<br>
<center>
