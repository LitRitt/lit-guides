---
layout: post
title:  "Creating a macOS VM on Windows with VirtualBox"
date:   2022-12-26 17:30:00 -0500
category: guide
---

### [Install VirtualBox](https://www.virtualbox.org/wiki/Downloads)

### [Install VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads)

### [Download the macOS Monterey ISO](https://www.mediafire.com/file/4fcx0aeoehmbnmp/macOS+Monterey+by+Techrechard.com.iso/file)

### Create Virtual Machine

#### General

- Basic/Name: macOS Monterey

#### System

- Motherboard/Base Memory: Any to spare
- Motherboard/Boot Order: Disable Floppy Disk
- Motherboard/Chipset: ICH9
- Processor/Processors: Any to spare

#### Display

- Screen/Video Memory: 128+ MB
- Screen/Extended Features: Enable 3D Acceleration

#### Storage

- SATA Port 0: Create a Virtual Hard Drive (50-100 GB)
- SATA Port 1: Select iso file downloaded above

#### Network

- Adapter 1: Bridged Adapter

#### USB

- USB Controller: USB 3.0

Save but **do not** start the VM yet

### Patches and Config

Run the following commands from an elevated command prompt to finish setting up the VM

{% highlight sh%}
cd C:\Program Files\Oracle\VirtualBox\
VBoxManage.exe modifyvm "macOS Monterey" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata "macOS Monterey" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac19,3"
VBoxManage setextradata "macOS Monterey" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata "macOS Monterey" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Mac-AA95B1DDAB278B95"
VBoxManage setextradata "macOS Monterey" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata "macOS Monterey" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
VBoxManage setextradata "macOS Monterey" "VBoxInternal/TM/TSCMode" "RealTSCOffset"
VBoxManage setextradata "macOS Monterey" VBoxInternal2/EfiGraphicsResolution 1920x1080
bcdedit /set hypervisorlaunchtype off
{% endhighlight %}

### Done

Start the VM and enjoy