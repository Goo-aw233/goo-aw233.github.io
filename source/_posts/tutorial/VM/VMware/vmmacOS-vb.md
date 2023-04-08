---
title: VirtualBox 安装 macOS
date: 2022-02-28 23:10:11
categories: 
	- [虚拟机,VirtualBox]
	- [教程,macOS]
tags:
	- VirtualBox
	- macOS
description: 利用 CDR,ISO 或 DMG 文件在 VirtualBox 中安装 Mac OS (X)/macOS
top_img: https://www.apple.com.cn/v/mac/home/bk/images/overview/monterey/tile_monterey__bm1x7sttegty_large.jpg
cover: https://www.apple.com.cn/v/mac/home/bk/images/overview/monterey/tile_monterey__bm1x7sttegty_large.jpg
---

## 用前说明
因为是虚拟机且没有显卡，所以版本越高，卡顿便越明显
<font size=3 color=yellow>AMD CPU 并不确保 100% 可以使用</font> 

### 实验环境（其他版本 VirtualBox 没试过）
VirtualBox 6.1
CDR/ISO/DMG（你也可以在其他地方下载）
<font size=1><del>DMG 镜像需要{% post_link tutorial/VM/VMware/vmdmg 特殊手段 %}安装</del></font> 暂时还没找到合适的方法给 VirtualBox 安装
[OneDrive 站点](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/EpoxWXc-tPpFnoAJTb4hoxYB0UWLRWMPHEwt5Tp-ZMZBvA)
[阿里云盘站点](https://www.aliyundrive.com/s/W4PHQ9gyLWi)

## 创建虚拟机

------

如果你需要用 DMG 镜像安装系统请看下面的文章
{% post_link tutorial/VM/VMware/vmdmg 使用 DMG 引导虚拟机 macOS %}

------

创建好一个虚拟机，配置像我这样就好了
（硬盘大小自由选择，建议≥50GiB
![](https://s2.loli.net/2022/08/15/VfX8C7U5aORdlD1.png)

## 修改机型
关闭 VirtualBox，然后<code>以管理员身份运行 Windows 终端或 PowerShell</code>
然后输入以下代码
````SHELL
cd <VirtualBox 的安装根目录>
.\VBoxManage.exe modifyvm <虚拟机名称> --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
.\VBoxManage setextradata <虚拟机名称> "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac19,1"
.\VBoxManage setextradata <虚拟机名称> "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
.\VBoxManage setextradata <虚拟机名称> "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Mac-AA95B1DDAB278B95"
.\VBoxManage setextradata <虚拟机名称> "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
.\VBoxManage setextradata <虚拟机名称> "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 0
.\VBoxManage setextradata <虚拟机名称> "VBoxInternal2/EfiGraphicsResolution" "1440x900"

如果你是 AMD CPU 可以尝试再加这个
.\VBoxManage modifyvm <虚拟机名称> --cpu-profile "Intel Xeon X5482 3.20GHz"
````
（如果命令有问题的话就请尝试把开头的<code> .\ </code>给去掉后重试）

其中<code>VirtualBox 的安装根目录</code>和<code>虚拟机名称</code>是根据自己需要来更改
![](https://s2.loli.net/2022/08/15/8NLBfTbH2WVOIKc.png)

------

<font size=4>如果你不知道 VirtualBox 的安装根目录</font>
在桌面上右键 VirtualBox 快捷方式，然后选择属性
（以 VMware Workstation 为例）
![](https://s2.loli.net/2022/07/31/1SEVKo8YjUnNMwg.png)
起始位置就是安装根目录了（不包括引号）
![](https://s2.loli.net/2022/07/31/ynSuFXxrRfmaBG5.png)

------

## 启动虚拟机
完成后关闭命令窗口，打开 VirtualBox
并启动虚拟机，然后你就会卡在这很久很久
![](https://s2.loli.net/2022/08/15/8NLBfTbH2WVOIKc.png)
<font size=2>*取自 [forums.virtualbox.org 原话](https://forums.virtualbox.org/viewtopic.php?f=22&t=85631 "It may seem that the installation stalls but don't shut the VM, be patient. Specifically, right before you switch to the graphics with the Apple logo and the progress bar, you'll get stuck at the point where the OSX ≥ 10.12.4 gets stuck:
IOConsoleUsers: gIOScreenLockState 3, hs 0, bs 0, now 0, sm 0x0")</font>
安装似乎会停止，但不要关闭 VM，请耐心等待。具体来说，在切换到带有 Apple 徽标和进度条的图形之前，您将卡在 OSX ≥10.12.4 卡住的位置：
IOConsoleUsers: gIOScreenLockState 3, hs 0, bs 0, now 0, sm 0x0
